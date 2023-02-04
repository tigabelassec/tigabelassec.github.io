---
title: Laravel Framework PHPUnit Remote Code Execution
author: ilham
date: 2019-06-30T09:13:00.003-07:00'
categories: [Blogging, Exploit]
tags: [exploit]
---

![](https://1.bp.blogspot.com/-_ff5oeppegQ/XRj5B8F4VpI/AAAAAAAAAhY/2vus48KyaFc8RvTEVOKcQhnZ_FLIaZeegCLcBGAs/s400/Screenshot_45.png)

  

  
  
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

<center>
  <iframe src="https://www.blogger.com/video.g?token=AD6v5dwUqxGW9DmS3qvOBw_206EC6XOLmTYdq_1ogZ-P8UoKBtcQJ-zu-POHafQN7JDUP5dCDAy7IMk9UEmjB_O5fnAikXhNRMIMklC27m5kmVVAUinxkKLjs8yFDqUuUGf8vIgvuMw" width="350" height="250" mozallowfullscreen="mozallowfullscreen"></iframe>
  </center>

Sekian dulu ya.  
CMIIW