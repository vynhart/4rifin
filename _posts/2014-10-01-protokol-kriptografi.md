---
layout: post
title:  "Cryptographic Protocols (Protokol Kriptografi)"
date:   2015-08-18 19:19:00 +0700
categories: kriptografi
permalink: cryptographic-protocols-protokol-kriptografi/
---

Sebuah protokol, dalam kehidupan manusia diartikan sebagai serangkaian etika yang telah disusun sedemikian rupa, seperti perilaku yang dapat dimengerti ketika makan malam formal.

Dalam kriptografi, sebuah protokol kriptografi adalah sebuah algoritma yang melibatkan dua atau lebih entiti (pihak yang terlibat dalam pertukaran informasi), menggunakan kriptografi (penyandian pesan), dan dirancang/ disusun untuk mencapai sebuah tujuan keamanan. Tujuan tersebut akan melibatkan otentikasi, privasi, dan kerahasiaan.

## Mengapa protokol diperlukan?

Salah satu alasan yang paling penting mengapa kita harus menggunakan protokol kriptografi adalah agar kita dapat memeriksa entiti yang mencoba untuk menipu kita, sehingga memberikan kita metode untuk membuat protokol untuk menggagalkan percobaan tersebut. kita perlu melakukan ini karena protokol komputer tidak “face-to-face” sehingga sulit memastikan keberadaan masing-masing personal.

Agar protokol dapat berjalan dengan semestinya, ktia mengasumsikan bahwa semua entity / pihak di dalam protokol mengetahui langkah-langkah penting dalam protokol. Setiap entity yang terlibat juga harus berada pada persetujuan untuk mengikuti setiap langkah dan menyelesaikan protocol sampai selesai.

Ada tiga jenis protokol kriptografi. Untuk menjelaskan protokol yang pertama, kita akan berkenalan dengan sebuah karakter entity di dalamnya : Trent, perantara yang dipercayai.

### Arbitrated protocols (Protokol dengan perantara)

Jenis protokol ini dibangun di atas sebuah trent yang dipercayai untuk tidak memberikan perlakuan khusus kepada Andi, Bob, atau siapapun. Trent tidak memiliki kesetiaan terhadap entity manapun yang terlibat di dalam protokol dan tidak memiliki alasan apapun untuk menyelesaikan protokol (Anggaplah trent sebagai pengacara yang tidak punya kepentingan selain membantu klien). Sehingga, karakteristik dari protocol jenis ini adalah semua entity dapat menerima, tidak hanya apa yang dilakukan benar, namun juga seluruh protokol harus diselesaikan dengan benar. Contoh dari protokol ini adalah:

Protokol berikut biasanya digunakan untuk mengidentifikasi pemilik. Alice (yang memiliki PIN atau password S) dari sebuah kartu kredit, ID card atau akun komputer. Protokol ini melakukannya dengan mengizinkan Alice meyakinkan seorang penjual, Bob tentang S (passwordnya benar) tanpa perlu memperlihatkan satu bit karakter pun dari S. Hal ini pertama diperkenalkan oleh Fiat dan Shamir pada 1987 sebagai otentikasi dan digital signature, dan dimodifikasi pada sebagai identification protocol.
