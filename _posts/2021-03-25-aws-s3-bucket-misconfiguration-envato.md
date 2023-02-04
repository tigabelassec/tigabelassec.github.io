---
title: AWS S3 Bucket Misconfiguration | Envato
author: mrhidden
date: '2021-03-25T21:52:00.000-07:00'
categories: [Blogging, Writeup]
tags: [writeup, aws]
---

![](https://1.bp.blogspot.com/-Dd69u3H5DN4/YEkbRlqlYYI/AAAAAAAAA6U/apM6av0fcToC-QrOFpjw48U0j2g28OvyACPcBGAYYCw/s2703/Envato.png)

  

Gak usah lama - lama lagi, jadi langsung saja

Semua berawal karena saya sedikit frustasi dikarenakan beberapa laporan saya di h1 dan bugcrowd dinyatakan duplikat 😥

Kemudian saya baca - baca write up orang lain sekalian cari - cari referensi dan menambah wawasan, sampai akhirnya saya menemukan write up milik bang [teguh](https://teguh.co/ssrf-vulnerability-dan-aws-s3-bucket-misconfiguration-di-placeit-envato/) atas temuannya di Envato, sampai akhirnya saya coba hunting di envato.

Alat tempur yang saya gunakan : 

*   [https://github.com/aboul3la/Sublist3r](https://github.com/aboul3la/Sublist3r)

*   [https://github.com/sa7mon/S3Scanner](https://github.com/sa7mon/S3Scanner)

*   [https://github.com/aws/aws-cli](https://github.com/aws/aws-cli)

Pertama kumpulin dulu semua domain yang in scope, kalian bisa cek disini  
[https://webuild.envato.com/helpful-hacker/](https://webuild.envato.com/helpful-hacker/) 

Setelah semua domain terkumpul, kemudian saya mengumpulkan subdomain nya juga menggunakan **Sublist3r**.
\
Kemudian saya coba scan menggunakan **S3Scanner** untuk mencari S3 Bucket yang terbuka, saya menemukan ada 4 subdomain milik Envato yang ACL nya tidak terkonfigurasi dengan baik, salah satunya **webuild.envato.com.s3.amazonaws.com**.

Jika **aws-cli** sudah terinstall dan sudah di konfigurasi kita bisa mencoba untuk melakukan pengecekan terhadap target kita dengan perintah
```shell
aws s3 ls s3://webuild.envato.com
```
![](https://1.bp.blogspot.com/-bJ3CFC8VlZk/YF1g0Du_f0I/AAAAAAAAA7g/mmwj2nQFBQoR3tZxZ7wApaUpJe_aVLgYgCLcBGAsYHQ/s836/EnvatoList.png)

  
Setelah menemukan celah tersebut saya kemudian mereport kepada security team nya dan saya mendapatkan respon yang baik

![](https://1.bp.blogspot.com/-ECgP-M9R1ew/YF1jQtXurAI/AAAAAAAAA7o/I0In8vT1IQQvn58-RcNNJZB78LCGcrc0gCLcBGAsYHQ/s964/Respon.png)

 

**Timeline**  

Feb 22, 2021 - Celah dilaporkan  
March 1, 2021 - Tim menyatakan bahwa bug valid  
March 1, 2021 - Bug Fixed

> Envato tidak akan memberikan _reward_ dalam bentuk apapun ke orang-orang yang melaporkan bug ke aset milik mereka. Nantinya jika laporan kamu dinyatakan valid, mereka akan mencamtumkan nama kamu di HOF (_Hall of Fame_).
{: .prompt-info }

Sekian dulu dari saya,  
Semoga bermanfaat.