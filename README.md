
<h1 <p align="center"><b>Praktikum 1</b></p></h1> 

**Nama: Muhammad Reza Maulana**

**NIM: 312210303**

**Kelas: TI.22.A3**

---

# <p align="center">Praktikum11 : PHP FRAMEWORK (CODEIGNITER)</p>

# Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.
   
2. Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)
  
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

# Langkah-langkah praktikum

Sebelum memulai menggunakan Framework codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu di aktifkan untuk kebutuhan pengembangan Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan:

  -  php-json ekstension untuk bekerja dengan JSON;
  -  php-mysqlnd native driver untuk MySQL
  -  php-xml ekstension untuk bekerja dengan XML;
  -  php-intl ekstensi untuk membuat aplikasi multibahasa;
  -  libcurl (opsional), jika ingin pakai Curl.

## MEMBUAT FOLDER BARU

Pertama, buatlah folder baru dengan nama ```lab11_php_ci``` pada root directory web server(c:xampp/htdocs/Lab11Web)

Kemudian, sebelum memulai menggunakan Framework Codeigniter kita perlu melakukan konfigurasi dan juga mengaktifkan beberapa ekstentsi PHP seperti php-jose, php-mysqlnd, php-mxl, php-intl, dan libcurl.

## PENGAKTIFAN EKSTENSI DENGAN XAMPP CONTROL PANEL

Untuk dapat mengaktifkannya kalian perlu masuk kedalam control panel xampp kemudian pada bagian apache klik Config > ```PHP (php.ini)``` seperti gambar dibawah.

<img width="852" alt="1" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/3b992edb-bbdf-48cd-925b-4fee6e07a67b">

Setelahnya cukup hilangkan tanda ; pada ekstentsi yang akan diaktifkan seperti gambar dibawah. Kemudian simpan kembali file tersebut dan restart Apache web servernya.

![2](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/cea8fcd7-32d9-4734-88b2-e90917ea1f2d)

## PENGINSTALLAN CODEIGNITER 4

Untuk melakukan instalasi codeigniter 4 dapat dilakukan dengan dua cara , yaitu cara manual dan menggunakan composer. pada praktikum ini kita menggunakan cara manual.

  -  Unduh Codeigniter dari website https://codeigniter.com/download
  -  Extrak file zip Codeigniter ke directori htdocs/lab11_ci.
  -  Ubah nama direktory framework-4.x.xx menjadi ci4
  -  Buka browser dengan alamat http://localhost/Lab11Web/lab11_php_ci/ci4/public/

![3](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/30e57b5e-df08-4ca6-83ee-1e69e79ff90f)

Pilih codeigniter 4 kemudian tekan download dan tunggu hingga terinstall.

## PROSES MENJALANKAN CLI (COMMAND LINE INTERFACE)

Codeigniter 4 menyediakan CLI untuk dapat mempermudah proses development. Untuk mengakses CLI bukalah terminal/command prompt. Kemudian arahkan lokasi direktori sesuai dengan direktori kerja project dibuat. (xampp/htdocs/Lab11Web/Lab11_php_ci/ci4)

Dan masukan perintah dibawah untuk dapat menjalankan guna memanggil CLI Codeigniter.

```php
php spark
```

![4](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/c0476dba-8f70-4a7e-bc95-91a47f10d6e3)

## PENGAKTIFAN MODE DEBUGGING

Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. Secara default fitur ini belum aktif. 

Maka untuk mengaktifkannya, Pertama ubahlah file env menjadi .env . Kemudian ubah nilai konfigurasi pada environment variable CI_ENVIRONMENT menjadi development seperti gambar berikut.

<img width="419" alt="5" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/309ef73e-672c-4806-9ae1-b85084b18a2a">

Selanjutnya hilangkanlah ; pada akhir kode ketika kalian membuka file app/Controller/Home.php seperti berikut.

<img width="440" alt="6" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/57ff6d51-b915-4843-8bda-a4591e714e47">

Dan terjadilah error pada aplikasi yang akan ditampilkan pesan kesalahan seperti berikut.

![7](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/6fd5e680-deda-4a57-b0ac-fe9eb660da94)

## PEMBUATAN ROUTE BARU

Untuk menambahkan route baru cukup tambahkan kode berikut.

```php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```

Kemudian buka CLI dan jalankan perintah berikut

```php
php spark routes
```

Jika mendapat tampilan seperti dibawah maka penambahan routes sudah benar.

<img width="960" alt="8" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/805f9a87-2127-4a6d-90dd-cf9c73f8758f">

Selanjutnya cobalah untuk mengakses route yang telah dibuat dengan mengakses alamat URL http://localhost:8080/about

<img width="841" alt="9" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/70baf9f6-d792-4064-9d8e-89c50761aa61">

Jika mendapat tampilan seperti diatas, maka artinya file atau pages tersebut tidak ada. Dan untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Controller yang sesuai dengan routing yang dibuat yaitu Controller Page.

## MEMBUAT CONTROLLER

![10](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/3fe81243-474d-473a-8152-5b1553c90162)

Selanjutnya adalah membuat Controller Page seperti diatas. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.

```php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "INI HALAMAN ABOUT";
    }
    public function contact()
    {
        echo "INI HALAMAN CONTACT";
    }
    public function faqs()
    {
        echo "INI HALAMAN FAQ";
    }
}
```

## AUTO ROUTING

Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroutenya dapat diubah menggunakan nilai variabelnya. Dan ntuk menonaktifkannya ubah nilai true menjadi false.

```php
$routes->setAutoRoute(true);
```

Tambahkan method baru pada Controller Page seperti berikut.

![11](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/36bde419-9a36-4830-b48f-6f209c361248)

## MEMBUAT VIEW

<img width="960" alt="12" src="https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/bbc8ac65-1262-4b04-91d6-61a41e0d922f">

Selanjutnya adalah membuat view untuk tampilan web agar lebih menarik seperti diatas dengan membuat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.

```php
public function about()
    {
        return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }
```

## MEMBUAT LAYOUT WEB DENGAN CSS

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Hanya saja yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Pertama, buatlah file css pada direktori public dengan nama style.css lalu buat juga folder pada direktori view yang didalamnya diisi dengan file header.php dan juga footer.php

Isi bagian header dengan kode berikut.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
    <header>
        <h1>Layout Sederhana</h1>
    </header>
    <nav>
        <a href="<?= base_url('/');?>" class="active">Home</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/about');?>">About</a>
        <a href="<?= base_url('/contact');?>">Kontak</a>
    </nav>
<section id="wrapper">
    <section id="main">
```

Dan isi bagian footer dengan kode berikut.
```php
</section>
    <aside id="sidebar">
        <div class="widget-box">
            <h3 class="title">Widget Header</h3>
            <ul>
                <li><a href="#">Widget Link</a></li>
                <li><a href="#">Widget Link</a></li>
            </ul>
        </div>
        <div class="widget-box">
            <h3 class="title">Widget Text</h3>
            <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada
tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis.
Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
        </div>
    </aside>
</section>
<footer>
    <p>&copy; 2022 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>
```

Selanjutnya, ubahlah file about pada app view dengan kode berikut.

```php
<?= $this->include('template/header'); ?>

<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>

<?= $this->include('template/footer'); ?>
```

Maka ketika halaman web tersebut kalian refresh, kalian akan mendapat tampilan seperti gambar dibawah ini.

![13](https://github.com/MuhammadReza1234/Lab11_php_ci/assets/115516607/8d34de11-9f3e-45c4-b375-d542dc06b2ab)
