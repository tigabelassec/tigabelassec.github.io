---
title: Stored XSS | Stealing Cookie Admin
author: mrhidden
date: '2019-07-04T10:25:00.000-07:00'
categories: [Blogging, Tutorial]
tags: [xss]
---

![](https://1.bp.blogspot.com/-5bvTWOJBYGM/XR4acMIa5BI/AAAAAAAAAkc/ZW5Jax0vHDgcToIYKyxhKnEmoNj9IYTpwCLcBGAs/s400/cross-site-scripting-xss.jpg)

  
Kali ini saya mau bahas tentang _Cross Site Scripting_ ( **XSS** ).  
Kerena kemarin saya mendapatkan sebuah bug XSS yang Ber-tipe Stored XSS pada salah satu situs E-Commerce indonesia dan Alhamdulillah mendapakan reward karena berhasil masuk ke Admin Panel.  
Tapi sayang nya saya tidak mendapatkan izin untuk Write-Up disini jadi saya bakal coba jelaskan dengan DVWA aja  
Ok sebelumnya saya akan menjelaskan sedikit apa _Cross Site Scripting_ ( **XSS** )  
  
**XSS** merupakan kependekan yang digunakan untuk istilah _cross site scripting_. XSS merupakan salah satu jenis serangan injeksi code _(code injection attack)_. XSS dilakukan oleh penyerang dengan cara memasukkan kode [HTML](https://id.wikipedia.org/wiki/HTML "HTML") atau _client script code_ lainnya ke suatu situs. Serangan ini akan seolah-olah datang dari situs tersebut. Akibat serangan ini antara lain penyerang dapat mem-_bypass_ keamanan di sisi klien, mendapatkan informasi sensitif, atau menyimpan aplikasi berbahaya.  
Alasan kependekan yang digunakan XSS bukan [CSS](https://id.wikipedia.org/wiki/CSS "CSS") karena CSS sudah digunakan untuk _cascade style sheet._  
  
Sumber : [Wikipedia](https://id.wikipedia.org/wiki/XSS)   
  
Sebelum lanjut membaca mohon baca dulu [DISCLAIMER](/disclaimer), jika sudah baca berarti anda setuju dengan apa yang saya tulis.  
  
Untuk kalian yang ingin mempelajari tentang bug-bug saya rasa DVWA cukup membantu untuk latihan  
  
Kalo mau lebih mudah bisa pake fitur yang ada di [XSS Hunter](http://xsshunter.com/)  
  
Bahan :  

1.  XAMPP kalian bisa download pada situs resminya atau klik [disini](https://www.apachefriends.org/index.html)
2.  DVWA kalian bisa download pada situs resminya atau klik [disini](https://github.com/ethicalhack3r/DVWA)

  
Langsung liat video aja ya biar lebih enak  

<center>
  <iframe src="https://www.blogger.com/video.g?token=AD6v5dw1kgPlSTTfIDv1uebT7V_P_R-aV4V-Aar-6OktnJK9bm024XJAXh9dlknx0MgU4EUoaZvEeVGguD4jPcQo5nIRQP7eYJQIxvYTw7ot4mxxqLgyde5O2dLfI9pTswT72_N2ed7d" width="350" height="250" mozallowfullscreen="mozallowfullscreen"></iframe>
  </center>

Ok sekian dulu. Terima kasih  
CMIIW