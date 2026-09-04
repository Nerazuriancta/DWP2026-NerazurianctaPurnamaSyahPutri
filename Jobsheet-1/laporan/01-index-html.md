## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. Penjelasan File `index.html`

File [index.html](../index.html) merupakan **halaman utama** atau beranda dari website SIMPUS-Mini. Halaman ini berfungsi sebagai tampilan awal sistem perpustakaan sederhana.

Di dalam halaman terdapat header yang menampilkan judul SIMPUS-Mini dan menu navigasi menuju halaman **Beranda**, **Daftar Buku**, **Tambah Buku**, dan **Daftar Anggota**.

Bagian main berisi ucapan selamat datang serta ringkasan data perpustakaan, yaitu total buku sebanyak 10, total anggota sebanyak 8, dan jumlah buku yang sedang dipinjam sebanyak 0.

Pada bagian bawah terdapat footer yang menampilkan informasi copyright SIMPUS-Mini dan keterangan Jobsheet 1.

## 1.1 Fungsi Tiap Bagian

| Tag | Fungsi |
|---|---|
| `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| `<html lang="id">` | Membuka dokumen HTML dan menentukan bahasa Indonesia. |
| `<head>` | Berisi informasi halaman yang tidak ditampilkan langsung. |
| `<meta charset="UTF-8">` | Mengatur format karakter.|
| `<title>` | Menentukan judul pada tab browser. |
| `<body>` | Menampung seluruh konten halaman. |
| `<header>` | Menampilkan bagian kepala halaman. |
| `<h1>` | Menampilkan judul utama SIMPUS-Mini. |
| `<nav>` | Menampung menu navigasi. |
| `<ul>` dan `<li>` | Membuat daftar menu. |
| `<a href="...">` | Membuat tautan ke halaman lain. |
| `<main>` | Menampung konten utama halaman. |
| `<section>` | Mengelompokkan konten berdasarkan bagian. |
| `<article>` | Menampilkan informasi ringkasan secara terpisah. |
| `<h2>` dan `<h3>`	| Menampilkan judul dan subjudul. |
| `<p>`	| Menampilkan teks atau informasi. |
| `<footer>` | Menampilkan bagian bawah halaman. |

## 1.2 Penjelasan Kode Tiap Baris

| Baris | Kode | Penjelasan |
|---|---|---|
| 1 | `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| 2 | `<html lang="id">` | Membuka dokumen HTML dengan bahasa Indonesia. |
| 3 | `<head>` | Membuka bagian informasi dokumen. |
| 4 | `<meta charset="UTF-8">` | Mengatur karakter agar teks dapat ditampilkan dengan benar. |
| 5 | `<title>SIMPUS-Mini \| Beranda</title>` | Menampilkan judul halaman pada tab browser. |
| 6 | `</head>` | Menutup bagian `head`. |
| 7 | `<body>` | Membuka bagian isi halaman. |
| 8 | `<header>` | Membuka bagian header. |
| 9 | `<h1>SIMPUS-Mini</h1>` | Menampilkan judul utama aplikasi. |
| 10 | `<nav>` | Membuka bagian navigasi. |
| 11 | `<ul>` | Membuka daftar menu. |
| 12 | `<li><a href="index.html">Beranda</a></li>` | Membuat tautan menuju halaman beranda. |
| 13 | `<li><a href="buku/list.html">Daftar Buku</a></li>` | Membuat tautan menuju halaman daftar buku. |
| 14 | `<li><a href="buku/tambah.html">Tambah Buku</a></li>` | Membuat tautan menuju halaman tambah buku. |
| 15 | `<li><a href="anggota/list.html">Daftar Anggota</a></li>` | Membuat tautan menuju halaman daftar anggota. |
| 16–18 | `</ul>`, `</nav>`, `</header>` | Menutup daftar menu, navigasi, dan header. |
| 19 | `<main>` | Membuka bagian konten utama. |
| 20–23 | `<section> ... </section>` | Menampilkan bagian ucapan selamat datang dan deskripsi aplikasi. |
| 24 | `<section>` | Membuka bagian ringkasan. |
| 25 | `<h2>Ringkasan</h2>` | Menampilkan judul Ringkasan. |
| 26–29 | `<article> ... </article>` | Menampilkan informasi total buku, yaitu 10. |
| 30–33 | `<article> ... </article>` | Menampilkan informasi total anggota, yaitu 8. |
| 34–37 | `<article> ... </article>` | Menampilkan informasi buku yang sedang dipinjam, yaitu 0. |
| 38–39 | `</section>`, `</main>` | Menutup bagian ringkasan dan konten utama. |
| 40 | `<footer>` | Membuka bagian footer. |
| 41 | `<p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 1</p>` | Menampilkan copyright dan keterangan Jobsheet 1. |
| 42 | `</footer>` | Menutup bagian footer. |
| 43 | `</body>` | Menutup seluruh isi halaman. |
| 44 | `</html>` | Menutup dokumen HTML. |

## 1.3 Kesimpulan

File [index.html](../index.html) berfungsi sebagai halaman utama SIMPUS-Mini yang menyediakan navigasi dan informasi singkat mengenai data perpustakaan. Penggunaan struktur HTML seperti `header`, `nav`, `main`, `section`, `article`, dan `footer` membuat halaman menjadi lebih terstruktur dan mudah dipahami.