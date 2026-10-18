
## Langkah-Langkah Praktikum

### 1. Konsep Box Element dan CSS Float (`lab4_box.html`)

```html
<section>
    <div class="div1">Div 1</div>
    <div class="div2">Div 2</div>
    <div class="div3">Div 3</div>
</section>
```

```css
div {
    float: left;
    padding: 10px;
}
.div1 { background: red; }
.div2 { background: yellow; color: #000; }
.div3 { background: green; }
```

**Screenshot Hasil :**  
![Langkah 1 - Box Element Dan CSS Float](./screenshots/1.png)

Struktur HTML (<section> dan <div>):

Sebuah elemen induk <section> berisi tiga elemen anak berbentuk kotak (<div>) dengan kelas div1, div2, dan div3.

Aturan Umum untuk Semua div (div { ... }):

float: left;: Membuat ketiga kotak yang tadinya tersusun secara vertikal (kebawah) menjadi berjajar ke samping kiri secara horizontal.

padding: 10px;: Menambahkan ruang di dalam setiap kotak antara teks dan bagian tepinya.

Styling Spesifik per Kotak (.div1, .div2, .div3):

.div1: Memberikan warna latar belakang merah.
.div2: Memberikan warna latar belakang kuning dengan teks berwarna hitam (#000).
.div3: Memberikan warna latar belakang hijau.

### 2. Mengatur Clearfix Element

```css
.div4 {
    background-color: blue;
    clear: left;
    float: none;
}
```

**Screenshot Hasil (Clearfix):**  
![Langkah 2 - Clearfix Element](./screenshots/2.png)

background-color: blue;

Fungsi: Memberikan warna latar belakang (background) biru pada elemen dengan kelas .div4.

Kegunaan: Membantu Anda secara visual melihat batas atau area dari elemen div tersebut di dalam halaman web.

clear: left;

Fungsi: Menentukan sisi mana dari elemen yang tidak boleh berdekatan dengan elemen yang melayang (floating).

Kegunaan: Dengan nilai left, elemen .div4 dipaksa untuk turun ke bawah jika di sebelah kirinya terdapat elemen lain yang menggunakan properti float: left;. Properti ini memastikan .div4 tidak "menimpa" atau sejajar di samping elemen floating sebelah kiri, melainkan berada di bawahnya.

float: none;

Fungsi: Menonaktifkan sifat melayang (float) pada elemen tersebut.

Kegunaan: Memastikan bahwa elemen .div4 kembali ke perilaku tata letak (layout) normal (blok standar) dan tidak lagi mengambang, sehingga aman diposisikan setelah elemen-elemen floating sebelumnya.

Kesimpulan Konsep Clearfix
Secara keseluruhan, kombinasi properti clear dan float di atas sering digunakan untuk merapikan tata letak (layout) agar elemen di bawahnya tidak berantakan akibat elemen lain yang menggunakan properti float di sekitarnya.

### 3. Membangun Kerangka Semantic Layout (`lab4_layout/home.html`)

```html
<div id="container">
    <header><h1>Layout Sederhana</h1></header>
    <nav>
        <a href="home.html" class="active">Home</a>
        <a href="artikel.html">Artikel</a>
        <a href="about.html">About</a>
        <a href="kontak.html">Kontak</a>
    </nav>
    <section id="hero"></section>
    <section id="wrapper">
        <section id="main"></section>
        <aside id="sidebar"></aside>
    </section>
    <footer><p>&copy; 2021 - Universitas Pelita Bangsa</p></footer>
</div>
```

**Screenshot Hasil (Kerangka Semantik):**  
![Langkah 3 - Kerangka Layout Semantik](./screenshots/3.png)

<div id="container">: Sebagai pembungkus utama (wrapper) untuk menampung seluruh elemen halaman web agar mudah diatur posisinya di tengah layar.

<header>: Bagian kepala halaman yang biasanya berisi judul utama web atau logo (di sini berisi judul "Layout Sederhana").

<nav>: Bagian navigasi atau menu tautan (link) untuk berpindah halaman (Home, Artikel, About, Kontak). Kelas active pada menu Home menandakan halaman yang sedang aktif.

<section id="hero">: Area banner atau hero image di bawah navigasi, biasanya digunakan untuk menyoroti konten utama atau gambar menarik.

<section id="wrapper">: Pembungkus tambahan untuk mengatur tata letak dua kolom di bawah hero.

<section id="main">: Area untuk konten utama artikel atau informasi penting.

<aside id="sidebar">: Area sidebar (samping) yang biasanya berisi widget, menu tambahan, atau iklan.

<footer>: Bagian kaki halaman yang berisi informasi hak cipta (copyright) atau identitas pembuat (contoh: Universitas Pelita Bangsa).

### 5. Penataan Header, Navigasi, dan Hero Panel

```css
#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #cccccc;
}
nav {
    display: block;
    background-color: #1f5faa;
}
nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #ffffff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}
#hero {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}
```

**Screenshot Hasil (Header & Hero):**  
![Langkah 4 - Tampilan Header dan Hero Panel](./screenshots/4.png)

#container

Mengatur lebar total halaman web menjadi 980px.

margin: 0 auto; berfungsi untuk membuat posisi kontainer berada tepat di tengah layar secara horizontal.

box-shadow memberikan efek bayangan tipis berwarna abu-abu di sekeliling kontainer agar tampak menonjol seperti lembaran kertas.

nav

display: block; memastikan elemen navigasi bersifat blok penuh.

background-color: #1f5faa; memberikan warna latar belakang biru tua pada area menu navigasi.

nav a

Mengatur gaya untuk setiap tautan (link) di dalam menu.

padding: 15px 30px; memberikan ruang/jarak di dalam tombol menu agar lebih nyaman diklik.

display: inline-block; membuat tautan bisa diatur ukuran padding-nya namun tetap berjejer ke samping.

color, font-size, font-weight, dan text-decoration: none; mengatur teks agar berwarna putih, berukuran 14px, tebal (bold), dan menghilangkan garis bawah bawaan tautan.

#hero

background-color: #e4e4e5; memberikan warna latar belakang abu-abu terang pada area hero panel.

padding: 50px 20px; memberikan jarak isi di dalam area hero agar terlihat lebih luas dan lega.

margin-bottom: 20px; memberikan jarak kosong di bawah hero panel sebelum masuk ke bagian konten berikutnya.

### 6. Pembagian Dua Kolom (Main Content & Sidebar Widget)
Membagi area `#wrapper` menjadi dua kolom berdampingan menggunakan `float: left`:
- Kolom Utama (`#main`): selebar 640px.
- Kolom Samping (`#sidebar`): selebar 260px.
- Disertai pembuatan komponen widget (`.widget-box`) pada sidebar dan baris 3 kotak gambar lingkaran (`.box`, `.image-circle`) pada konten utama.

```css
#main {
    float: left;
    width: 640px;
    padding: 20px;
}
#sidebar {
    float: left;
    width: 260px;
    padding: 20px;
}
.box {
    display: block;
    float: left;
    width: 33.333333%;
    box-sizing: border-box;
    padding: 0 10px;
    text-align: center;
}
.image-circle {
    border-radius: 50%;
}
```

**Screenshot Hasil (Main Content & Sidebar):**  
![Langkah 5 - Main Content dan Sidebar Widget](./screenshots/5.png)


#main (Konten Utama)

float: left; membuat elemen konten utama mengambang ke sebelah kiri.

width: 640px; menetapkan lebar area konten utama.

padding: 20px; memberikan jarak bagian dalam agar teks atau elemen di dalamnya tidak menempel langsung pada tepi batas.

#sidebar (Sidebar Widget)

float: left; membuat sidebar ikut mengambang ke kiri sehingga berdampingan secara horizontal dengan #main.

width: 260px; menetapkan lebar area sidebar. Jika ditotal dengan lebar #main (640px + 20px+20px padding) dan sidebar (260px + 20px+20px padding), ukurannya pas berada di dalam kontainer utama.

padding: 20px; memberikan jarak dalam agar isi sidebar terlihat rapi.

.box (Kotak Grid / Kolom Tambahan)

width: 33.333333%; membagi elemen menjadi 3 bagian yang sama rata dalam satu baris (karena 100% dibagi 3).

float: left; dan display: block; membuat kotak-kotak tersebut berjejer ke samping.

box-sizing: border-box; memastikan ukuran lebar 33.3% sudah termasuk padding, sehingga tidak merusak tata letak.

padding: 0 10px; memberikan jarak antar kotak, dan text-align: center; membuat teks/gambar di dalamnya berada di tengah.

.image-circle

border-radius: 50%; membuat gambar atau elemen berbentuk kotak berubah menjadi bentuk lingkaran sempurna.

### 6. Integrasi Artikel Featurette dan Footer

```css
.entry img {
    float: left;
    border-radius: 5px;
    margin-right: 15px;
}
.entry .right-img {
    float: right;
    margin-right: 0;
    margin-left: 15px;
}
footer {
    clear: both;
    background-color: #1d1d1d;
    padding: 20px;
    color: #eee;
}
```

**Screenshot Hasil Utuh Halaman Beranda (`home.html`):**  
![Langkah 6 - Tampilan Utuh Home Layout](./screenshots/6.png)

.entry img (Gambar Artikel Standar)

float: left; membuat gambar diletakkan di sebelah kiri teks, sehingga teks dapat mengalir di sebelah kanan gambar.

border-radius: 5px; membuat sudut-sudut gambar menjadi sedikit melengkung (tidak lancip).

margin-right: 15px; memberikan jarak kosong di sebelah kanan gambar agar tidak menempel langsung dengan teks di sampingnya.

.entry .right-img (Gambar Artikel Posisi Kanan)

float: right; mengubah posisi gambar agar berada di sebelah kanan teks (mengambang ke kanan).

margin-right: 0; menghapus jarak kanan bawaan.

margin-left: 15px; memberikan jarak di sebelah kiri gambar agar teks di sebelah kirinya tidak menempel.

footer (Bagian Kaki Halaman)

clear: both; memastikan footer selalu berada di bawah elemen-elemen yang menggunakan properti float sebelumnya (seperti #main dan #sidebar), mencegah footer naik menimpa konten atasnya.

background-color: #1d1d1d; memberikan warna latar belakang hitam/abu-abu gelap.

padding: 20px; memberikan jarak isi di dalam area footer agar terlihat lega.

color: #eee; mengubah warna teks di dalam footer menjadi abu-abu terang agar mudah dibaca di atas latar belakang gelap.


