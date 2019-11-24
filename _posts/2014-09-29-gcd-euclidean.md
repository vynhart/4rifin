---
layout: post
title:  "Greatest Common Divisor (GCD) dan Algoritma Euclidean"
date:   2014-09-29 19:19:00 +0700
categories: math
permalink: greatest-common-divisor-gcd-dan-algoritma-euclidean/
layout: post
---

*Greatest Common Divisor (GCD)* atau yang disebut sebagai Faktor Persekutuan Terbesar dalam bahasa indonesia merupakan sebuah bilangan bulat x paling besar yang dapat membagi habis dua buah bilangan bulat `a` dan `b`.

Misalkan `a = 12` dan `b = 8`. kita dapati bahwa bilangan-bilangan yang habis membagi kedua bilangan tersebut adalah sbb:

`12` habis dibagi oleh : `1, 2, 3, 4, 6, 12.`
`8` habis dibagi oleh : `1, 2, 4, 8.`

Dari kedua deret bilangan yang kita dapati diatas, kita dapat melihat bahwa bilangan yang terdapat pada kedua baris yaitu : `1, 2, dan 4`. yang artinya `1, 2, dan 4` dapat membagi habis `a = (12)` dan `b = (8)`. Maka GCD dari 12 dan 8, ditulis:

`gcd(12, 8)` adalah *4*.

Dalam dunia komputer, untuk memecahkan sebuah persoalan, dibutuhkan algoritma. Disini saya akan membahas sedikit tentang algoritma pencarian GCD dari dua buah bilangan a dan b dengan algoritma Euclidean.

## Algoritma Euclidean

Jika sebuah bilangan a dibagi dengan bilangan b dan hasil baginya tidak habis, maka kita bisa mendapatkan sebuah bilangan sisa yang kita sebut sebagai *remainder*.

Misalkan jika `a = 13` dan `b = 4`.

`13 / 4` akan menghasilkan `3` dengan sisa bagi `1`.

`13 = (4 * 3) + 1`

angka *3* pada persamaan diatas disebut *quotient*.  
sedangkan angka *1* disebut *remainder*.

Algoritma Euclidean dalam mencari GCD dari dua buah bilangan memanfaatkan persamaan diatas dengan mengambil *remainder* sebagai bagian penting dalam mencari GCD. perhatikan algoritma Euclidean berikut:

> Jika a dan b adalah bilangan bulat dengan a >= b, algoritma dibawah akan menemukan gcd (a,b) dengan langkah yang pasti selesai (terminated).

> (1) ro = a dan r 1 = b
> (2) i = 1
> (3) Bagilah ri-1 dengan ri untuk mendapat quotient dan remainder. r1+1 = remainder.
> (4) Jika ri+1 = 0, maka gcd(1,b) = ri dan algoritma selesai.
> (5) jika ri+1 tidak 0, atur nilai i = i + 1, lalu kembali ke langkah 3.

### Contoh

gcd(2024, 748):

```
2048 = 748 * 2 + 528
748 = 528 * 1 + 220
528 = 220 * 2 + 88
220 = 88 * 2 + 44
88 = 44 * 2 + 0
```

Maka *gcd(2024, 748) = 44*

Thats it! Not a rocket science right? ;)