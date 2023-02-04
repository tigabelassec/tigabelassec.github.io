---
title: Rubber Ducky - 4 Digit PIN Brute Force
author: mrhidden
date: '2021-09-29T09:59:00.004-07:00'
categories: [Blogging, Digispark]
tags: [Digispark]
pin: true
---

![](https://1.bp.blogspot.com/-EVpuHde-BP8/YVSWzREMtuI/AAAAAAAABAM/uBtJYTOXb4oQvSK1K4JDs5cYelh-_FasgCLcBGAsYHQ/s600/Digispark-Attiny85.jpg)

Karena sekarang saya udah gak nganggur lagi jadi jarang kali nulis di blog, giliran nulis malah ngebait ✌️

Sekarang saya mau sharing tentang brute force pin android tapi bukan dengan USB Rubber Ducky, ya dikarenakan harganya lumayan mahal $49.99, jadii saya pake board pengganti yaitu digispark attiny85 selain harganya yang murah juga mudah untuk didapatkan.

Sedikit penjelasan tentang digispark attiny85:

Digispark adalah papan pengembangan mikrokontroler berbasis Attiny85 yang mirip dengan lini Arduino, hanya saja lebih murah, lebih kecil, dan sedikit kurang bertenaga. Dengan sejumlah besar pelindung untuk memperluas fungsionalitasnya dan kemampuan untuk menggunakan Arduino IDE yang sudah dikenal, Digispark adalah cara yang bagus untuk terjun ke elektronik, atau sempurna untuk saat Arduino terlalu besar atau terlalu banyak.

Berikut adalah spesifikasi:

    Support for the Arduino IDE 1.0+ (OSX/Win/Linux)
    Power via USB or External Source - 5v or 7-35v (12v or less recommended, automatic selection
    On-board 500ma 5V Regulator
    Built-in USB
    6 I/O Pins (2 are used for USB only if your program actively communicates over USB, otherwise you can use all 6 even if you are programming via USB)
    8k Flash Memory (about 6k after bootloader)
    I2C and SPI (vis USI)
    PWM on 3 pins (more possible with Software PWM)
    ADC on 4 pins
    Power LED and Test/Status LED

Sekarang kita masuk ke inti dari pembahasan kali ini, awalnya saya tidak tertarik dengan hal seperti ini tapi di karenakan teman saya menanyakan soal ini jadi saya coba cari-cari referensi tentang digispark dan bagaimana board seperti ini dengan ukuran yang mungil bisa bekerja sebagai pengganti keyboard.

Setelah saya baca-baca mengenai digispark attiny85 akhirnya saya coba beli board tersebut, dan saya coba pelajari gimana nge-deploy board tersebut agar bisa berfungsi sebagaimana mestinya, ternyata board ini di program dengan Arduino IDE menggunakan bahasa C++.

Akhirnya saya menemukan referensi tentang brute force pin android di forum Digistump, kemudian saya coba pelajari dan saya mencoba membuat dengan code saya sendiri.

Disini saya tidak meberikan tutorial bagaimana cara install maupun konfigurasi Arduino IDE, kalian bisa searching aja sendiri udah banyak yang buat tutorial gimana cara konfigurasinya, saya juga tidak membagikan source code saya, kalian bisa pelajari sendiri.

Berikut video singkat brute force pin :

 

  

  

**Referensi:**

[https://digistump.com/board/index.php?topic=858.0](https://digistump.com/board/index.php?topic=858.0)

[https://github.com/urbanadventurer/Android-PIN-Bruteforce](https://github.com/urbanadventurer/Android-PIN-Bruteforce)