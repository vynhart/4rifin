---
layout: post
title:  "Cara memindahkan database sqlite ke Mysql"
date:   2016-05-29 19:19:00 +0700
categories: database
permalink: cara-memindahkan-database-sqlite-ke-mysql/
---

Bagi anda yang sudah membuat aplikasi dengan menggunakan database sqlite dan pada suatu waktu menemukan bahwa Sqlite tidak lagi cocok untuk digunakan diaplikasi anda, lalu anda memutuskan untuk berpindah ke Mysql, semoga tulisan ini dapat membantu anda.

Dalam kasus saya, Sqlite sulit untuk menghandle multiple thread sehingga saya memutuskan untuk migrasi ke mysql. Saat melakukan migrasi, saya kesulitan mendapatkan cara untuk memindahkan data yang sudah terlanjur banyak di database sqlite ke database Mysql. Saya mencoba untuk melakukan dump sqlite, dan mengimport nya ke Mysql, ternyata tidak bisa. Ada cukup banyak syntax query berbeda yang digunakan sqlite dibandingkan Mysql.

Setelah cukup lama berselancar, saya menemukan sebuah solusi yang membuat saya berkata “Hore”. Ini dia:

*Export database SQlite anda ke CSV, kemudian import CSV tersebut ke MySQL.*

Sederhana kan? Caranya? Silahkan googling sendiri :p

Baiklah baiklah, caranya macam-macam, jika anda menggunakan database client seperti PhpMyAdmin dll-nya, prosesnya akan lebih mudah, tapi jika anda menggunakan command line seperti migrasi database di server dimana anda akses menggunakan ssh, begini caranya:

1. Export dari sqlite ke csv:
    ```
   ./bin/sqlite3 ./sys/xserve_sqlite.db <<!
   .headers on
   .mode csv
   .output out.csv
   select * from eS1100_sensor_results;
   !
    ```
2.  Import file CSV tersebut ke MySQL menggunakan mysqlimport
    ```
    mysqlimport --ignore-lines=1 \
    --fields-terminated-by=, \
    --verbose --local -u [user] \
    -p [database] \
    /path/to/mycsv.csv
    ```
