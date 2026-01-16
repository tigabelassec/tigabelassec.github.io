---
title: Konfigurasi Genymotion dan Burp Suite SSL Certificate
author: mrhidden
date: "2021-12-28T09:31:00.006-08:00"
image: /assets/img/posts/2021/genymotion-burp/header.png
description: Panduan konfigurasi Genymotion dengan Burp Suite untuk intercept traffic HTTPS, mencakup setup proxy, instalasi CA certificate, dan kebutuhan testing aplikasi Android.
categories: [Blogging, Tutorial]
tags: [Android Emulator]
---

Sebelum kita melakukan konfigurasi saya anggap teman-teman sudah menginstall Genymotion maupun Burp Suite.  
Oke kita bahas satu-satu apa itu Genymotion dan apa itu Burp Suite?

**Genymotion**

Genymotion adalah emulator android yang menyertakan serangkaian sensor dan fitur lengkap untuk berinteraksi dengan Android virtual.  
Dengan Genymotion teman-teman dapat menguji aplikasi Android di perangkat virtual untuk tujuan pengembangan, pengujian dan demontrasi.  
Genymotion ini juga tersedia untuk beberapa operasi sistem seperti Windows, MacOS, dan Linux. Bagi teman-teman yang belum menginstall teman-teman dapat mendownloadnya di official website Genymotion.  
Berikut tautan untuk mendownload `https://www.genymotion.com/download/`, pastikan teman-teman download sesuai dengan operasi sistem yang teman-teman gunakan.

![Genymotion step 1](/assets/img/posts/2021/genymotion-burp/genymotion-1.png)

Tampilan setelah selesai installasi dan login

Setelah selesai melakukan installasi teman-teman dapat memilih device apa yang ingin teman-teman gunakan, disini saya menggunakan xiaomi redmi note 7 dengan versi android 9.0 dan menggunakan processor 2 core dan ram 2gb serta menggukan mode jaringan NAT by default.  
Teman-teman bisa kustomisasi sendiri dengan spek pc teman-teman sendiri.

![Genymotion step 2](/assets/img/posts/2021/genymotion-burp/genymotion-2.png)

Pemilihan perangkat

Jika sudah tunggu beberapa saat untuk melakukan peng-installan android, setelah itu teman-teman sudah dapat menggunakannya dengan menekan titik tiga disebalah kanan dan pilih start.  
Sampai disini selesai sudah untuk melakukan installasi Genymotion dan android virtual nya, sekarang kita lanjut membahas Burp Suite.

**Burp Suite**

Burp Suite adalah suatu tools yang banyak digunakan untuk melakukan penetration testing pada website maupun mobile apps. tools ini digunakan untuk mencegat (intercept) data yang dikirim (request) atau diterima (response) oleh aplikasi atau browser dari server melalui jalur proxy yang sudah disetting pada browser maupun android dan ios.  
Burp Suite ini dapat digunakan di berbagai sistem operasi seperti Windows, MacOS, dan Linux. Teman-teman dapat mendownload ini melalui official website nya, berikut tautan untuk download `https://portswigger.net/burp/releases`.

Disini saya anggap teman-teman sudah mendownload maupun install pada perangkat yang teman-teman gunakan.  
Selanjutnya kita akan melakukan konfigurasi agar bisa berinteraksi antara Genymotion dengan Burp Suite.

Pada tampilan Burp Suite silahkan pilih tab **proxy** kemudian pilih **options** pada pilihan **proxy listeners** klik tombol **add** kemudian pilih **specific address** dan pilih **IP address** teman-teman, untuk teman-teman yang tidak tau berapa **IP address** yang teman-teman gunakan, teman-teman dapat membuka terminal bagi yang menggunakan linux ketik **ifconfig** dan untuk pengguna windows teman-teman dapat menggunakan command prompt (cmd) kemudian ketik **ipconfig**. Jika sudah masukan **port 8080** kemudian klik **ok** pada Burp Suite.

![Burpsuite step 1](/assets/img/posts/2021/genymotion-burp/burp-1.png)

Mengatur proxy

Setelah itu lakukan export CA certificate dengan format **.der**

![Burpsuite step 2](/assets/img/posts/2021/genymotion-burp/burp-2.png)

Export Certificate

Jika sudah sekarang kita bisa menggunakan tools **openssl** untuk mengubah file **.der** menjadi .**pem** kemudian di ubah lagi menjadi `<hash>.0`

Pada terminal ketikkan perintah:

```shell
openssl x509 -inform DER -in namafile.der -out namafile.pem
```

Setelah memasukkan perintah di atas kalian akan mendapatkan 2 file certificate dengan format **.der** dan **.pem** kemudian ketikkan lagi perintah:

```shell
openssl x509 -inform PEM -subject_hash_old -in namafile.pem | head -1
```

Setelah mengetikkan perintah diatas teman-teman akan mendapatkan kode hash, setelah mendapatkan kode hash teman-teman salin kode tersebut kemudian lakukan rename file dengan perintah:

```shell
mv namafile.pem <hash>.0
```

![shell step 1](/assets/img/posts/2021/genymotion-burp/shell-1.png)

Jika sudah sekarang kita akan menyalin file hash tersebut ke `/system` sistem android. Saya anggap teman-teman sudah menginstall **adb**.

Pada terminal ketikkan perintah:

```shell
adb remount
```

Kemudian kita akan menyalin file certificate ke `/sdcard/` dengan perintah:

```shell
adb push <hash>.0 /sdcard/
```

![shell step 2](/assets/img/posts/2021/genymotion-burp/shell-2.png)

Jika sudah kita akan masuk ke shell dengan perintah:

```shell
adb shell
```

Jika sudah di dalam shell kemudian kita akan memindahkan file hash di `/sdcard/` ke sistem dengan perintah:

```shell
mv /sdcard/<hash>.0 /system/etc/security/cacerts/
```

Kemudian ubah permission-nya menjadi **644** dengan perintah:

```shell
chmod 644 /system/etc/security/cacerts/<hash>.0
```

Setelah itu lakukan reboot

```shell
reboot
```

![shell step 3](/assets/img/posts/2021/genymotion-burp/shell-3.png)

Jika perangkat sudah hidup kembali silahkan pastikan bahwa certificate sudah ada dengan cara, pergi ke **pengaturan -> security & location -> encrtyption & credentials -> trusted credentials** kemudian cari certificate dengan nama **PortSwigger**.

![config step 1](/assets/img/posts/2021/genymotion-burp/config-1.png)

Jika sudah sekarang kita melakukan konfigurasi pada jaringan di emulator dengan cara pergi ke **pengaturan -> network & internet -> wifi -> pilih gambar gear -> pilih gambar pensil -> klik advanced options ->** pada bagian **proxy** pilih **manual ->** isi **hostname** dan **port** sama dengan settingan pada Burp Suite tadi kemudian **save**.

![config step 2](/assets/img/posts/2021/genymotion-burp/config-2.png)

Sekarang kita coba apakah berjalan dengan baik, buka browser pada virtual android kemudan ketikan `google.com` setelah itu cek apakah ada request yang masuk pada Burp Suite, jika ada maka kalian berhasil melakukan konfigurasi.

![config step 2](/assets/img/posts/2021/genymotion-burp/config-2.png)

Sekian dulu dari saya, jika ada yang salah dalam penyampaian atau kurang dimengerti silahkan untuk menghubungi saya melalui email [contact@tigabelassec.my.id](mailto:contact@tigabelassec.my.id).
