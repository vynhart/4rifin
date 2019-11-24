---
layout: post
title:  "Solusi CodeIgniter tidak dapat upload filetype pdf. Error: The filetype you are attempting to upload is not allowed"
date:   2015-09-06 19:19:00 +0700
categories: web-development
permalink: solusi-codeigniter-tidak-dapat-upload-filetype-pdf-error-the-filetype-you-are-attempting-to-upload-is-not-allowed/
---

Setelah menelusuri web untuk mencari solusi atas permasalahan diatas, berikut saya simpulkan solusinya.

## Penyebab

1. Error tersebut terjadi karena PHP mengenal ekstensi file dengan type nya masing, masing. Tipe file inilah yang menjadi pedoman bagi CodeIgniter dalam menentukan file apa saja yang boleh diupload ke server. Contohnya, untuk file jpg, PHP menerjemahkannya sebagai tipe: image/jpeg. Ekstensi dari masing-masing jenis file ini disimpan di dalam file application/config/mimes.php untuk dijadikan sebagai rujukan file apa saja yang diijinkan untuk diupload ke server.
2. Terjadi perbedaan penafsiran mengenai file pdf antara PHP dengan CodeIgniter, sehingga file yang dikenali PHP terhadap PDF berbeda dengan jenis file yang tersimpan di dalam CodeIgniter

## Solusi

Pada baris controller dimana anda melakukan proses upload file, anda akan menampilkan error jika file tidak berhasil diupload, yaitu pada baris berikut:  
`echo $this->upload->display_errors();`  
tambahkan baris baru di bawah baris diatas sehingga menjadi seperti berikut:  
```
echo $this->upload->display_errors();
echo ‘<pre>’;
print_r($this->upload->data());
echo ‘</pre>’;
```

Kemudian, Upload ulang file pdf anda, sekarang website akan menampilkan informasi dari file secara lebih mendetail, pada komputer saya, browser menampilkan data berikut:

```
The filetype you are attempting to upload is not allowed.

Array
(
   [file_name] => Curriculum Vitae.pdf
   [file_type] => application/download
   [file_path] => C:/xampp/htdocs/portal/uploads/materi_ajar/RPL/2010/
   [full_path] => C:/xampp/htdocs/portal/uploads/materi_ajar/RPL/2010/Curriculum Vitae.pdf
   [raw_name] => Curriculum Vitae
   [orig_name] =>
   [client_name] => Curriculum Vitae.pdf
   [file_ext] => .pdf
   [file_size] => 152639
   [is_image] =>
   [image_width] =>
   [image_height] =>
   [image_type] =>
   [image_size_str] =>
)
```

Perhatikan baris *[file_type] => application/download*,pada baris tersebut PHP mengenali tipe dari file yang kita upload sebagai `application/download`. Sekarang bukalah file mimes.php yang berada pada folder `application/config/` pada website anda.

Anda dapat lihat bahwa pada baris `key => value` dalam array, pdf tidak memiliki `application/download`, pada file saya, baris tersebut berisi: `'pdf' => array('application/pdf', 'application/x-download')`, Agar file pdf yang ingin kita upload dikenali sebagai bagian dari mime pdf pada file, tambahkan application/download pada elemen array diatas, sehingga menjadi:

```
'pdf' => array('application/pdf', 'application/x-download', 'application/download')
```
Sekarang, coba upload ulang file pdf yang anda inginkan, sekarang seharusnya file dapat diupload dengan lancar. Semoga bermanfaat
