---
title: Laravel Framework PHPUnit Remote Code Execution
author: mrhidden
date: "2019-06-30T09:13:00.003-07:00"
image: /assets/img/posts/2019/phpunit/header.png
description: Kerentanan PHPUnit pada framework Laravel yang dapat dimanfaatkan untuk Remote Code Execution akibat konfigurasi dan exposure endpoint yang tidak aman.
categories: [Blogging, Exploit]
tags: [exploit]
---

Laravel Framework PHPUnit Remote Code Execution, dimana bug ini kembali rame di bahas di forum - forum. Celah ini sebenarnya terletak pada vendor third party yakni PHPUnit, bukan dari Laravelnya

Sebelum lanjut membaca mohon baca dulu [DISCLAIMER](/disclaimer), jika sudah baca berarti anda setuju dengan apa yang saya tulis.

**Dork:** `inurl:/vendor/phpunit/`
\
Point Vuln nya itu terletak di **eval-stdin.php**
\
Full Path Exploit: `http://target.com**/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php`

Disini saya mengirim datanya menggunakan Burp Suite.
\
Selain itu juga kalian bisa menggunakan lain nya untuk melakukan Remote Code Execution nya
\
pake yang menurut kalian enak aja

Langsung liat video nya aja biar lebih mudah dipahami.

<figure>
  <iframe
    src="https://www.blogger.com/video.g?token=AD6v5dwUqxGW9DmS3qvOBw_206EC6XOLmTYdq_1ogZ-P8UoKBtcQJ-zu-POHafQN7JDUP5dCDAy7IMk9UEmjB_O5fnAikXhNRMIMklC27m5kmVVAUinxkKLjs8yFDqUuUGf8vIgvuMw"
    width="100%"
    height="420"
    loading="lazy"
    allowfullscreen>
  </iframe>
</figure>

Sekian dulu ya.  
CMIIW
