---
title: Konfigurasi Genymotion dan Burp Suite SSL Certificate
author: mrhidden
date: '2021-12-28T09:31:00.006-08:00'
categories: [Blogging, Tutorial]
tags: [Android Emulator]
---

![](https://blogger.googleusercontent.com/img/a/AVvXsEhwpI8nqivv8YhdeJu61U73Xv8njr9MBeLO-uEkM-qGx5n5468Ub9KaBMQakoBsZhknqgjOwUDH-EW5KX5iiACDqx5773x4_1ZpNkw1FYByPajQ_5f7iy4dcIrK7HBZeWZI5PxBZnzHD7wGTAUnZWruFPhKYdAz4ext4j3m637vy3tsM_Zj0Uu942L5Ng=s1365)

  

Sebelum kita melakukan konfigurasi saya anggap teman-teman sudah menginstall Genymotion maupun Burp Suite.  
Oke kita bahas satu-satu apa itu Genymotion dan apa itu Burp Suite?

**Genymotion**

Genymotion adalah emulator android yang menyertakan serangkaian sensor dan fitur lengkap untuk berinteraksi dengan Android virtual.  
Dengan Genymotion teman-teman dapat menguji aplikasi Android di perangkat virtual untuk tujuan pengembangan, pengujian dan demontrasi.  
Genymotion ini juga tersedia untuk beberapa operasi sistem seperti Windows, MacOS, dan Linux. Bagi teman-teman yang belum menginstall teman-teman dapat mendownloadnya di official website Genymotion.  
Berikut tautan untuk mendownload `https://www.genymotion.com/download/`, pastikan teman-teman download sesuai dengan operasi sistem yang teman-teman gunakan.

![](https://blogger.googleusercontent.com/img/a/AVvXsEgwppE-HEz7kJZLDTvgZOwkAQJa7wYIYUxF1fzKqC-XGxpQ11ewDjHfddDo3-cL_rNY4Q7yce0A0Rcv62dKEeMVlNFMqXPFxmc7wtBvhKNNSGqiD6lVcay64UKiM9I-HwO-g9nFk6qW-M3Ri5X0SuqUV8yBrUNk8C1VuLd6jMhO6H5PXFXLpw6r2kwg8A=s1362)

Tampilan setelah selesai installasi dan login

  
Setelah selesai melakukan installasi teman-teman dapat memilih device apa yang ingin teman-teman gunakan, disini saya menggunakan xiaomi redmi note 7 dengan versi android 9.0 dan menggunakan processor 2 core dan ram 2gb serta menggukan mode jaringan NAT by default.  
Teman-teman bisa kustomisasi sendiri dengan spek pc teman-teman sendiri.

![](https://blogger.googleusercontent.com/img/a/AVvXsEh00HaUF72SsWWXE2G1stm-2qlif8edNg7n07N23GC-dJ2ouT6ZcEcTqIO1edGsxyL4ROfuLZWgxmN-9nACSmXpZLxKMjwAV5KEe6I0VXxG3QGil_keKjoaU4QfC5c7VYju_ai4FKQZAI_YNaQz5jJperkh74oNv9WH9ZaT-tnysybwDHQvq4XNUOm2OQ=s1363)

Pemilihan perangkat

  
Jika sudah tunggu beberapa saat untuk melakukan peng-installan android, setelah itu teman-teman sudah dapat menggunakannya dengan menekan titik tiga disebalah kanan dan pilih start.  
Sampai disini selesai sudah untuk melakukan installasi Genymotion dan android virtual nya, sekarang kita lanjut membahas Burp Suite.

**Burp Suite**

Burp Suite adalah suatu tools yang banyak digunakan untuk melakukan penetration testing pada website maupun mobile apps. tools ini digunakan untuk mencegat (intercept) data yang dikirim (request) atau diterima (response) oleh aplikasi atau browser dari server melalui jalur proxy yang sudah disetting pada browser maupun android dan ios.  
Burp Suite ini dapat digunakan di berbagai sistem operasi seperti Windows, MacOS, dan Linux. Teman-teman dapat mendownload ini melalui official website nya, berikut tautan untuk download `https://portswigger.net/burp/releases`.

Disini saya anggap teman-teman sudah mendownload maupun install pada perangkat yang teman-teman gunakan.  
Selanjutnya kita akan melakukan konfigurasi agar bisa berinteraksi antara Genymotion dengan Burp Suite.

Pada tampilan Burp Suite silahkan pilih tab **proxy** kemudian pilih **options** pada pilihan **proxy listeners** klik tombol **add** kemudian pilih **specific address** dan pilih **IP address** teman-teman, untuk teman-teman yang tidak tau berapa **IP address** yang teman-teman gunakan, teman-teman dapat membuka terminal bagi yang menggunakan linux ketik **ifconfig** dan untuk pengguna windows teman-teman dapat menggunakan command prompt (cmd) kemudian ketik **ipconfig**. Jika sudah masukan  **port 8080** kemudian klik **ok** pada Burp Suite.

![](https://blogger.googleusercontent.com/img/a/AVvXsEiHZKRP-yS7dAjkxdYgORQUkOLdYgp4FpXKJidBmOMxzXZNMM06lMPzM4WQPRSOPL2L-1CL-iuFsz3nqEqsuAhsZ5Qy-568lXX_tN_MRk_xMqWPlIr8GOoMULp932EDnJuuqIfzBS1zWVFrwMT6FfiCJvsE_EaRzmCmr-wioyP-1-ClEwVpvDjo_NnmZA=s1365)

Mengatur proxy

  

Setelah itu lakukan export CA certificate dengan format **.der** 

![](https://blogger.googleusercontent.com/img/a/AVvXsEhbg-SwFwsgjFbFRO_BFBJHiHgBNGz3IyotSjTiuoykR-j4idTW3rS9XEBkk5uQ6o4vwaINHTxxV1JMQcneHGaB8aeqUpURUocyklR7LplIbdlu9iimsBVZGwEpBqWUrtB-gLC_HoEV6FSJOQ-jsZWkwjqldGeDVDYoqi3MTcCcr1Qenl8GA3NoSsskVw=s1365)

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
![](https://blogger.googleusercontent.com/img/a/AVvXsEig6XPK3G2TYBuE6hKTmbhfV_7BVDJ1rLlLtZnwoj1cXcowXUTPUlU9vmurrw_J5iLO-oIzHKlro1NRjga5ZVUEeMmV2v0vbKWF2oYPnUr7qaq7vVkDP7pPi8VhRh4EcKAt7aifqlpGeFcaAD4eybqbUnEHhlefk6JlQTC28UuUJBghOntb7H7gSWDTQg=s1103)

  
Jika sudah sekarang kita akan menyalin file hash tersebut ke `/system` sistem android. Saya anggap teman-teman sudah menginstall **adb**.

  

Pada terminal ketikkan perintah:
```shell
adb remount
```
Kemudian kita akan menyalin file certificate ke `/sdcard/` dengan perintah:
```shell
adb push <hash>.0 /sdcard/
```
![](https://blogger.googleusercontent.com/img/a/AVvXsEgKMZlsS2x4MkxWXurBKfpTIC5nav19Y5Y5NAKof0rogK0XsCehsmbMxWEwDbAFjIaB6ZGEZ7-hiAUkN4sP9jprWF_F1JnlvvXeC22bsDeV4kxRfAbLsAeenNHEgGlQpXQ6y-IDPts9bFyc3WFYPKppp993W8yWW7npOkSjlQjnJlJJr6PEuiLxA11ftA=s1086)

  

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
![](https://blogger.googleusercontent.com/img/a/AVvXsEiWivIm4zyFNebsUAnM9LI2XulGjp9AF0d3bg1lcWQ9GwRRTsT_CWDpQ1cWWVffxRcW1uHEjFIG9x9nl8U4i5kTxpzlISo7Rl6T_WyhDCCWChEjUjSHtKW4DjY-Exz2CC-T1SDD8Ln5-IxpBuoSU6eQ4UZ4pq1Cq7t0SrXBEspHdxYlvH3AgBObCULh7Q=s1104)

  

Jika perangkat sudah hidup kembali silahkan pastikan bahwa certificate sudah ada dengan cara, pergi ke **pengaturan -> security & location -> encrtyption & credentials -> trusted credentials** kemudian cari certificate dengan nama **PortSwigger**.

  

![](https://blogger.googleusercontent.com/img/a/AVvXsEgEuCdXCLz_bGhEJSwvmHPFMwJXXKT8gyQ3mAJAQT1XWlnM1lv-0UY54LMlPpZ6wrUr_82_zZqhzoZYsrtBLqpwPOfVM9T3jkSPqON7tK7igf64BB6XBxmsig2g_qYegQTmhPqfkyVjQcHl3ub0DcHiQ_xUx4tX3-7cT6fINoPFURnc4yS_LIrfxjPSyA=s733)

  

Jika sudah sekarang kita melakukan konfigurasi pada jaringan di emulator dengan cara pergi ke **pengaturan -> network & internet -> wifi -> pilih gambar gear -> pilih gambar pensil -> klik advanced options ->** pada bagian **proxy** pilih **manual ->** isi **hostname** dan **port** sama dengan settingan pada Burp Suite tadi kemudian **save**.

  

![](https://blogger.googleusercontent.com/img/a/AVvXsEhxXamSrL5GUzwdRMJZUNR9mVxc2UgR1F1twA8_XKSe3NdZJ1SGG72KbnpNsKcjLHh-mnrVrrkM3SPdH6SpGll6pM3kBHJdBqaiKWz-O67sSXuxSJTzOK7Jn-CItnqMriB3gf5SmdcDQweXvAJImo0wszPQgaSj0e3uSTYufNOdGFxHvCHakycXflUHDA=s727)

  

Sekarang kita coba apakah berjalan dengan baik, buka browser pada virtual android kemudan ketikan `google.com` setelah itu cek apakah ada request yang masuk pada Burp Suite, jika ada maka kalian berhasil melakukan konfigurasi.

  

![](https://blogger.googleusercontent.com/img/a/AVvXsEg-rvl5i5Z_4CDsJ7f71Wik_wN_Y66CcoTYD3t1JFsVIJkZMgJtHG206xDbzmqqpguh3vV6cbULnaZ8JPPIaRhbVB1hupZzi2S1fhzor9D6XT7g7bmlSTcPQ3oax-RSyH7IZ2c_VIugPmD-05sDk_ymoSfqwPGLlXPkYNrAGqeNtZPDFeIbOqs9wc02Ug=s1365)

  

Sekian dulu dari saya, jika ada yang salah dalam penyampaian atau kurang dimengerti silahkan untuk menghubungi saya melalui email [contact@tigabelassec.my.id](mailto:contact@tigabelassec.my.id).