---
title: Reflected XSS on File Upload - *.mail.ru
author: mrhidden
date: '2020-01-18T21:47:00.000-08:00'
categories: [Blogging, Writeup]
tags: [xss, writeup]
---

![](https://1.bp.blogspot.com/-usTIL0X-IFM/Xgh6MCr1S0I/AAAAAAAAAt8/Bao2P1HIIBA3IGMupGn3dvk2oDRkuPItQCLcBGAsYHQ/s1600/help.mail.ru.png)

  
Sudah lama gak nulis di blog ini, nah kali ini saya share bagaimana saya menemukan bug Reflected XSS di subdomain nya mail.ru  
  
Pertama saya lihat banyak sekali yang menemukan bug di mail.ru pada platform HackerOne, nah dari sini saya mulai tertarik dan saya mulai cari bug di mail.ru  
  
Setelah beberapa menit saya hunting bug di mail.ru sampai akhirnya saya menemukan adanya bug Reflected XSS pada file upload  
  
Saya coba memasukkan payload xss pada form-form yang ada ternyata tidak ada efek apapun yang terjadi, kemudian saya coba capture semua request dengan burpsuite dan saya coba menggunakan trik **MIME Type Sniffing** dengan tujuan untuk mengubah **Content-Type** dari **image/jpg** menjadi **text/html** dan tetap tidak terjadi apapun  
  

![](https://media.giphy.com/media/DfSXiR60W9MVq/giphy.gif)

  
Kemudian saya coba lagi, tapi kali ini saya mengubah nama filenya dengan payload xss seperti ni `1<ScRiPt>alert(document.domain)</ScRiPt>` dan BOOMMMM!!!! xss triggerd  
  

  
**Timeline**  
  
Dec 28, 2019 - Celah dilaporkan.  
Dec 28, 2019 - Tim mengatakan bahwa sudah dilaporkan oleh peneliti lain (Duplicate)  
Jan 19, 2020 - Bug Fixed