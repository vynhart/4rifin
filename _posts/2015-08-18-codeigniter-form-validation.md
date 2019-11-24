---
layout: post
title:  "Tutorial CodeIgniter Form Validation"
date:   2015-08-18 19:19:00 +0700
categories: web-development
permalink: tutorial-codeigniter-form-validation/
---

Form validation diperlukan untuk memastikan data yang dikirim ke server sudah sesuai dengan ketentuan sebelum diproses ke database. CodeIgniter menyediakan fungsi validasi yang sangat mudah digunakan, stay tuned.

Yang perlu kita pahami sebelumnya adalah alur dari validation itu sendiri, yaitu sebagai berikut:

1. User memasukkan data ke form.
2. User mengirim data ke server.
3. Server melakukan validasi data, jika data masih belum sesuai dengan ketentuan yang diinginkan, server akan kembali me-load halaman form dan user kembali mengisi form.
4. Proses diulangi sampai semua data memenuhi persyaratan.
5. Jika data sudah memenuhi persyaratan, data akan dilanjutkan ke proses berikutnya seperti diteruskan ke database atau melalui proses sanitizing terlebih dahulu.

Di dalam tutorial ini kita akan memerlukan tiga file yaitu:

1. File view dari form, disini kita gunakan php yang diletakkan di dalam folder application/views.
2. File view ketika data yang dikirimkan sesuai dengan persyaratan yang ditentukan, disini kita gunakan php yang diletakkan di dalam folder application/views.
3. File controller, pada tutorial ini kita menggunakan controller php.

Pertama-tama kita membuat file *signup_view.php* dan mengisi filenya dengan kode berikut:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Validation Form</title>
</head>
<body>

<div id="container">
  <h1>Belajar validation</h1>

  <div id="body">
    <p>Berikut ini adalah percobaan validation form di PHP menggunakan class validation dari CodeIgniter.</p>
    <p><?php echo validation_errors(); ?></p>
    <form method="POST">
      <div><input name="username" type="text" placeholder="Username" value="<?php echo set_value('username') ?>"></input> </div>
      <div><input name="password" type="text" placeholder="Password" value="<?php echo set_value('password') ?>"></input> </div>
      <div> <input type="submit" value="Login"></input> </div>
    </form>
  </div>

  <p class="footer">Page rendered in <strong>{elapsed_time}</strong> seconds</p>
</div>

</body>
</html>
{% endhighlight %}

Baris kode `<?php echo validation_errors(); ?>` digunakan untuk menampilkan pesan error jika terdapat data yang dikirimkan tidak sesuai dengan ketentuan yang telah disyaratkan. Baris kode `<?php echo set_value(‘nama field’); ?>` digunakan untuk mengatur value pada field berdasarkan data yang dikirim jika terjadi kesalahan, jadi user tidak perlu mengulang untuk mengisi semua form dari nol/kosong. Perhatikan bahwa parameter yang digunakan harus sama dengan nama field pada form. Berikutnya kita membuat file *sukses_view.php* dan mengisi filenya dengan kode berikut:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Sukses View</title>
</head>
<body>

<div id="container">
  <h1>Data valid</h1>

  <div id="body">
    Data telah divalidation dan berhasil masuk sampai sini.
  </div>

  <p class="footer">Page render ed in <strong>{elapsed_time}</strong> seconds</p>
</div>

</body>
</html>
{% endhighlight %}

File terakhir, yaitu file controller *signup.php* berisi kode berikut.

{% highlight php %}
<?php if ( ! defined('BASEPATH')) exit('No direct script access allowed');
class Signup extends CI_Controller {
  public function index()
  {
    //$this->load->helper(array('form', 'url'));
    $this->load->library('form_validation');
    $this->form_validation->set_rules('username', 'Username', 'required');
    $this->form_validation->set_rules('password', 'Password', 'required');
    if($this->form_validation->run() == FALSE){
      $this->load->view('signup_view');
    } else {
      $th is->load->view('success_view');
    }
  }
}
{% endhighlight %}

Baris kode `this->load->library(‘form_validation’);` digunakan untuk me-load class *form_validation*. Baris kode ini harus ditulis sebelum kita menggunakan fungsi-fungsi validasi yang tersedia. Jika mau, baris kode ini dapat diletakkan di dalam Constructor controller agar ter-load secara otomatis tiap kali controller diakses.

Persyaratan validasi untuk setiap field ada pada baris

`$this->form_validation->set_rules(‘password’, ‘Password’, ‘required’);`

Baris ini memiliki tiga parameter, yang pertama adalah nama field yang kita gunakan di dalam form `(atribut name=”” pada HTML)`. Parameter ke-2 adalah `nama manusia` untuk field, digunakan ketika terjadi error, misalkan kita menggunakan user pada field, namun pada tulisan error pengguna website akan lebih mengerti jika kita menampilkan pesan error `Username is required` daripada `user is required`. Yang ketiga adalah rules yang kita tetapkan untuk validasi sebuah field, pada kode diatas artinya “field password harus diisi”, rules tidak hanya `required` namun masih banyak yang lain seperti panjang minimum/maksimum, harus numeric, penulisan email, dll.

*Rules* pada sebuah field dapat lebih dari satu, misalkan selain tidak boleh kosong, kita juga ingin agar user hanya menuliskan angka pada kolom nomor handphone, maka jika kita menggunakan field no_hp, dapat menulis:

`$this->form_validation->set_rules(‘no_hp’, ‘Password’, ‘required|numeric’);`

Setiap rule dipisahkan dengan tanda pipe `|`. Untuk rules apa saja yang dapat digunakan, dapat langsung check ke dokumentasi resmi CodeIgniter.

Semoga bermanfaat
