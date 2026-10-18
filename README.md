#  Modul Praktikum: CSS Box Model, Float, dan Semantic Layout

Dokumentasi lengkap langkah-langkah praktikum pembuatan tata letak (*layout*) web modern menggunakan konsep **CSS Box Model**, pengontrolan tata letak dengan properti **Float**, serta penerapan **HTML5 Semantic Elements**.

---

##  Langkah-Langkah Praktikum

### 1. Konsep Box Model & CSS Float (`lab4_box.html`)

Secara *default*, setiap elemen HTML diperlakukan oleh browser sebagai sebuah kotak (*box*) persegi panjang. Konsep **CSS Box Model** terdiri dari empat komponen utama: **Content** (isi elemen), **Padding** (jarak antara isi dan garis tepi), **Border** (garis tepi), dan **Margin** (jarak luar antar elemen).

Pada tahap awal ini, kita membuat tiga elemen `div` dasar di dalam kontainer `<section>` tanpa tambahan gaya tata letak agar terlihat bagaimana perilaku *block-level element* secara bawaan (tersusun secara vertikal dari atas ke bawah).

```html
<section>
    <div class="div1">Div 1</div>
    <div class="div2">Div 2</div>
    <div class="div3">Div 3</div>
</section>
```

> ** Penjelasan Teknis:** Elemen `div` merupakan *block-level element*, yang berarti elemen ini secara otomatis akan memakan seluruh lebar baris yang tersedia, membuat kotak-kotak tersebut menumpuk ke bawah meskipun ukurannya kecil.

> **📸 Preview (Tanpa Float):**  
> ![Langkah 1 - Box Element Tanpa Float](./screenshots/1.png)

---

### 2. Menerapkan CSS Float Property

Untuk mengubah perilaku *block-level* yang menumpuk ke bawah menjadi berdampingan secara horizontal, kita menggunakan properti `float: left`. Properti ini membuat elemen keluar dari alur dokumen normal (*normal flow*) dan menggeser elemen berikutnya ke sisi kanan atau kiri.

```css
div {
    float: left;
    padding: 10px;
}
.div1 { background: red; }
.div2 { background: yellow; color: #000; }
.div3 { background: green; }
```

> ** Penjelasan Teknis:** Dengan menambahkan `float: left`, ketiga kotak akan ditarik ke sebelah kiri secara berurutan. Penambahan `padding` berfungsi memberikan ruang internal di dalam kotak agar teks tidak menempel langsung pada tepi latar belakang warna.

> **📸 Preview (Dengan Float):**  
> ![Langkah 2 - Box Element Dengan Float](./screenshots/2.png)

---

### 3. Mengatur Clearfix Element

Salah satu efek samping dari penggunaan properti `float` adalah elemen di bawahnya atau kontainer pembungkus bisa kehilangan referensi tinggi (*height collapse*). Untuk mengatasinya, kita menggunakan properti `clear`.

Ketika ditambahkan elemen keempat (`div4`), kita menerapkan `clear: left` agar elemen tersebut menolak untuk berada di samping elemen yang melayang, sehingga dipaksa turun ke baris baru.

```css
.div4 {
    background-color: blue;
    clear: left;
    float: none;
}
```

> ** Penjelasan Teknis:** `clear: left` memberitahu browser bahwa tidak boleh ada elemen yang mengambang (*floating*) di sisi kiri elemen `div4`, yang secara efektif mengembalikan perilaku baris baru pada elemen tersebut.

> **📸 Preview (Clearfix):**  
> ![Langkah 3 - Clearfix Element](./screenshots/3.png)

---

### 4. Membangun Kerangka Semantic Layout (`lab4_layout/home.html`)

HTML5 memperkenalkan elemen semantik untuk memberikan arti yang jelas pada struktur dokumen web, bukan sekadar menggunakan `div` generik. Kita menyusun kerangka utama di dalam kontainer `<div id="container">` menggunakan elemen seperti `<header>`, `<nav>`, `<section>`, `<aside>`, dan `<footer>`.

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

> ** Penjelasan Teknis:** Penggunaan elemen semantik sangat membantu optimasi mesin pencari (SEO) dan aksesibilitas pembaca layar (*screen reader*), karena struktur dokumen menjadi mudah dipahami oleh mesin maupun pengembang lain.

> **📸 Preview (Kerangka Semantik):**  
> ![Langkah 4 - Kerangka Layout Semantik](./screenshots/4.png)

---

### 5. Penataan Header, Navigasi, dan Hero Panel

Setelah kerangka terbentuk, kita mempercantik tampilannya melalui file `style.css`. Kontainer utama diberi lebar tetap (`980px`), diposisikan di tengah layar menggunakan `margin: 0 auto`, serta diberi efek bayangan (`box-shadow`) agar tampak seperti kanvas halaman web profesional.

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

> ** Penjelasan Teknis:** Bilah navigasi (`nav`) ditata menggunakan tautan bergaya blok dengan warna latar biru khas korporat, lengkap dengan area *Hero Panel* yang berfungsi sebagai ruang sorot (*banner* atau *call-to-action*) di bawah menu.

> **📸 Preview (Header & Hero):**  
> ![Langkah 5 - Tampilan Header dan Hero Panel](./screenshots/5.png)

---

### 6. Pembagian Dua Kolom (Main Content & Sidebar Widget)

Tata letak web standar umumnya membagi area konten menjadi dua kolom: kolom utama untuk isi berita/artikel dan kolom samping (sidebar) untuk widget atau informasi tambahan. Kita membagi `#wrapper` menggunakan teknik `float: left` dengan alokasi lebar yang proporsional.

* **Kolom Utama (`#main`):** Lebar 640px.
* **Kolom Samping (`#sidebar`):** Lebar 260px.
* Di dalam kolom utama, disematkan tiga kotak gambar melingkar (`.box`, `.image-circle`) menggunakan persentase lebar `33.33%` agar tersusun rata tiga kolom.

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

> ** Penjelasan Teknis:** Properti `box-sizing: border-box` sangat penting agar perhitungan lebar elemen menyertakan padding dan border, sehingga layout tidak rusak akibat kelebihan lebar pixel.

> **📸 Preview (Main Content & Sidebar):**  
> ![Langkah 6 - Main Content dan Sidebar Widget](./screenshots/6.png)

---

### 7. Integrasi Artikel Featurette dan Footer

Tahap akhir adalah menyusun isi artikel (`.entry`) dengan teknik perataan gambar dinamis (`float: left` dan `float: right`) agar teks dapat mengalir di samping gambar (*text-wrapping*). 

Sebagai penutup, elemen `footer` diberi properti `clear: both` untuk memastikan footer selalu berada di bawah seluruh elemen yang menggunakan float, mencegah elemen meluap keluar dari kontainer.

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

> ** Penjelasan Teknis:** Penggunaan `clear: both` pada footer adalah kunci utama dalam teknik *float-based layout* untuk mengunci tinggi kontainer utama (`#container`) agar merangkum seluruh isi konten di dalamnya dengan sempurna.

> **📸 Preview (Tampilan Utuh Beranda / `home.html`):**  
> ![Langkah 7 - Tampilan Utuh Home Layout](./screenshots/7.png)

---
