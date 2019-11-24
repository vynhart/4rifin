---
layout: post
title:  "Jenis-jenis Database yang harus kamu ketahui"
date:   2015-12-31 19:19:00 +0700
categories: database
permalink: jenis-jenis-database-yang-harus-kamu-ketahui/
---

Bagi kamu yang masih baru dalam dunia software development maupun programming, jika mendengar kata ‘database’ mungkin yang ada di pikiran kamu adalah ‘MySQL’ ataupun ‘Microsoft Access’, beberapa yang lain juga akan teringat ‘PostgreSQL’ walaupun hanya sekedar ‘pernah dengar’, setidaknya itulah yang saya alami dulu, hehehe.

Ternyata database itu ada banyak jenisnya, tidak hanya RDBMS seperti yang mungkin selama ini kamu ketahui. Masing-masing jenis database itu memiliki tujuan penggunaannya sendiri-sendiri. Artikel ini akan membahas tiga jenis database yang paling banyak digunakan. Ke depannya akan ditambah lagi. So, Stay tuned.

## Relational Database

Relational database adalah sistem penyimpanan data dalam bentuk tabel-tabel yang saling berhubungan. Setiap tabel memiliki field-nya masing masing, di antara field tersebut biasanya terdapat satu field ID yang akan menjadi pembeda setiap baris (disebut juga dengan record) di dalam tabel. ID inilah yang nantinya akan menjadi penghubung tabel satu dengan tabel yang lain.

![Relational Database](/images/relational-database.png)

## Key Value Database

Jenis database yang satu ini berbeda dengan RDBMS yang selama ini sudah familiar di antara kita. Tujuan penggunaannya juga berbeda. Seperti namanya, key-value database adalah database yang menyimpan key-value. Itu saja? ya. sama seperti Hash dalam bahasa pemrograman dimana ada ‘key’, dan setiap ‘key’ tersebut memiliki ‘value’.

![Relational Database](/images/key-value-database.png)

Diantara yang paling populer adalah Memcache dan Redis (Redis Saat ini telah menggeser posisi Memcache menjadi key-value database paling populer dan banyak digunakan), database dengan tipe seperti ini biasanya akan disimpan di memory dan tidak langsung di write ke database. Tujuannya adalah untuk penyimpanan ‘sementara’ -meski tidak selalu seperti itu, Redis menyimpan datanya tidak hanya di memory tapi juga di dalam storage-. Pada web server yang diakses jutaan pengguna tiap harinya, mekanisme seperti ini sangat dibutuhkan. Bayangkan jika setiap kali user mengakses halaman profilenya, maka semua data harus di retrieve dari storage, ini tentunya tidak efisien, data yang telah di retrieve dari storage biasanya akan disimpan di dalam Key-value database yang ada di memory untuk dipergunakan dalam jangka waktu tertentu.

## Document-based Database

Sama seperti RDBMS, Document-based database bertujuan untuk menyimpan data yang banyak dan besar, namun implementasinya berbeda. Jika RDBMS memiliki ‘Relational’ yang menjadi fondasi utama hubungan antar table, Document-based database tidak memiliki ‘Relasi’ antar tabel. Setiap relasi akan secara langsung dituliskan di dalam record, why? Seperti yang pernah saya baca, mereka mengatakan ‘Storage is cheap, but processing is expensive’. Perbedaan utama lain antara RDBMS dengan Document-base ialah, document base database tidak memiliki Struktur tabel yang harus diikuti dengan ketat, artinya, setiap record bisa saja memiliki struktur field yang berbeda, tipe data yang berbeda, dan segala-galanya berbeda, cool huh?

![Document Based Database](/images/document-base-database.png)

Lalu menjadi pertanyaan, mengapa masih ada RDBMS jika sudah ada Document-based? Secara performa, pada data-data yang besar dimana ada puluhan juta record misalnya, misalkan untuk pencarian record tertentu, RDBMS (terutama versi enterprise seperti Oracle, dll) masih lebih cepat jika dibandingkan Document-based. Namun untuk data-data dinamis yang fieldnya tidak tetap dan akan berubah seiring waktu, Document-based menjadi solusi yang tepat.

# And Others

Masih ada jenis database yang lain yaitu: Graph database, Search Engines, Object Oriented database, Time-series Database, Multi value database, Native XML Database, Content stores, Wide Column stores, Event stores, Navigational Database, RDF Stores, tapi karena saya lapar jadi saya cukupkan segini dulu untuk pengantarnya hehe, silahkan untuk menjelajah web lebih lanjut. Mbah Google know many about everything, trust me, hehehe.

Semoga bermanfaat. :)
