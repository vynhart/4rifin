---
layout: post
title:  "Public Key Cryptography (Kriptografi Kunci Public)"
date:   2014-10-04 19:19:00 +0700
categories: kriptografi
permalink: public-key-cryptography-kriptografi-kunci-public/
---

![XML Logo](/images/xml-logo.png)

Public Key Cryptography atau uga disebut Assymetric cryptography. adalah sebuah jenis algoritma kriptografi dengan dua kunci yaitu kunci private (yang dirahasiakan) dan kunci publik (yang didistribusikan kepada siapapun yang membutuhkan). Public Key akan digunakan untuk mengenkripsi pesan, dan private key akan digunakan untuk mendekripsi pesan. Istilah Assymetric diambil dari berbedanya kunci untuk mengenkripsi dan mendekripsikan pesan, berbeda dengan kriptografi simetris yang menggunakan kunci yang sama untuk mengenkripsi dan mendekripsi pesan.

Kriptografi kunci publik diciptakan dari permasalahan sulitnya / berbahayanya distribusi kunci yang ada pada jenis kriptografi simetris. Pada kriptografi kunci publik, pemilik kunci private tidak perlu khawatir kunci publik yang digunakan untuk mengenkripsi pesan diketahui oleh siapapun, karena pesan yang telah dienkripsi, tidak akan bisa didekripsi jika tidak menggunakan kunci private yang hanya dimiliki si pembuat kunci. Asumsi pada kriptografi ini adalah kunci private tidak akan bisa (secara komputasi tidak mungkin) ditemukan berdasarkan kunci publik yang didistribusikan sehingga keamanan pesan yang dikirim terjamin sekalipun dalam pengiriman pesan ada man in the middle selama kunci private tidak diketahui oleh orang lain.

## Cara kerja kriptografi kunci publik

Berikut adalah gambaran bagaimana kriptografi kunci publik bekerja:

![Public Key Cryptography](/images/public-key-cryptography.png)

Tahap pertama, seperti pada gambar diatas, Alice akan membuat kunci public dan kunci private. Lalu Alice akan memberikan kunci public pada siapapun yang memerlukan untuk mengenkripsi pesan dan ditujukan kepada Alice.

Tahap kedua, Bob telah menerima kunci public yang dikirimkan oleh Alice (dimana siapapun boleh menerimanya), lalu Bob mengenkripsi pesan dengan kunci public tersebut lalu mengirimkannya pada Alice. Pesan yang telah dienkripsi tidak perlu dikhawatirkan untuk ketahuan / bocor kepada pihak lain karena tidak ada satupun pihak yang akan mampu memecahkan pesan yang telah dienkripsi tanpa kunci private yang hanya dimiliki oleh Alice.

Alice menerima pesan yang telah dienkripsi (disebut ciphertext) yang dikirimkan Bob, lalu mendekripsi pesan tersebut ke plaintext awal.
