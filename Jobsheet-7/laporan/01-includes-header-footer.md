## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. `includes/header.php` & `includes/footer.php`

Ini fitur PHP pertama yang benar-benar menyelesaikan masalah nyata:
sejak jobsheet-01, `<header>` dan `<footer>` yang **persis sama**
diulang-ulang di **setiap** file HTML. Kalau suatu saat menu navigasi perlu ditambah satu tautan baru, kamu
harus mengedit **semua** file satu-satu. PHP `include` menyelesaikan
masalah ini sekali untuk selamanya.

## 1.1 `includes/header.php` — Kode Lengkap

```php
<?php
session_start();

$__jobsheetRoot = dirname(__DIR__);
$__scriptDir = dirname($_SERVER['SCRIPT_FILENAME']);
$__rel = ltrim(str_replace('\\', '/', substr($__scriptDir, strlen($__jobsheetRoot))), '/');
$base = $__rel === '' ? '' : str_repeat('../', substr_count($__rel, '/') + 1);
?>
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>SIMPUS-Mini<?php echo isset($page_title) ? ' | ' . $page_title : ''; ?></title>
    <link rel="stylesheet" href="<?php echo $base; ?>assets/css/style.css">
</head>
<body>
    <header>
        <h1>SIMPUS-Mini</h1>
        <button type="button" id="nav-toggle-btn" class="nav-toggle-label" aria-label="Menu">&#9776;</button>
        <nav>
            <ul>
                <li><a href="<?php echo $base; ?>index.php">Beranda</a></li>
                <li><a href="<?php echo $base; ?>buku/list.php">Daftar Buku</a></li>
                <li><a href="<?php echo $base; ?>buku/tambah.php">Tambah Buku</a></li>
                <li><a href="<?php echo $base; ?>anggota/list.php">Daftar Anggota</a></li>
                <li><a href="<?php echo $base; ?>anggota/tambah.php">Tambah Anggota</a></li>
            </ul>
        </nav>
    </header>

    <main>
```

Perhatikan file ini **tidak ditutup rapi** — tag `<main>` dibuka tapi
tidak pernah ditutup, `<body>` dan `<html>` juga tidak ditutup.

## 1.2 Memanggil `include`

```php
<?php
$page_title = "Beranda";
include __DIR__ . '/includes/header.php';
```

- **`include`** adalah pernyataan PHP yang **menyisipkan** seluruh isi file lain **tepat di posisi itu** — efeknya seolah-olah seluruh isi `header.php` "ditempel" langsung menggantikan baris `include` ini.
- **`__DIR__`** adalah konstanta bawaan PHP yang selalu berisi path folder tempat file yang sedang berjalan berada. Menggabungkannya dengan `'/includes/header.php'` menghasilkan path yang **selalu benar**, tidak peduli dari halaman mana `include` ini dipanggil — beda dengan path relatif (`../`) yang harus dihitung manual tergantung kedalaman folder. Bandingkan pemanggilannya di `index.php` (`__DIR__ . '/includes/header.php'`) dengan di `buku/list.php` (`__DIR__ . '/../includes/header.php'`) — keduanya benar karena `__DIR__` otomatis menyesuaikan diri dengan lokasi file masing-masing.
- **`$page_title = "Beranda";`** ditulis **sebelum** baris `include` — urutan ini penting! Variabel yang dibuat di `index.php` **tetap bisa diakses** di dalam `header.php` setelah di-include (PHP menyatukan keduanya seolah-olah satu file besar), sehingga baris `<?php echo isset($page_title) ? ' | ' . $page_title : ''; ?>` di dalam `header.php` bisa "melihat" nilai `$page_title` yang baru saja diset oleh halaman yang memanggilnya.

## 1.3 Path Relatif Otomatis di `includes/header.php`

Bandingkan tautan menu di `header.php` sekarang:
```php
<li><a href="<?php echo $base; ?>index.php">Beranda</a></li>
<li><a href="<?php echo $base; ?>buku/list.php">Daftar Buku</a></li>
```

dengan versi jobsheet-05/06 yang memakai path **relatif** tulis-tangan (`index.html`, `list.html`)

**Kenapa path relatif tulis-tangan tidak cukup di sini?** Karena `header.php` sekarang **dipakai bersama** oleh halaman-halaman di kedalaman folder yang **berbeda-beda** (`index.php` di root, `buku/list.php` satu folder lebih dalam). Kalau menu ditulis dengan path relatif tetap seperti di jobsheet-05/06, satu tautan yang sama (misalnya ke Beranda) akan butuh `index.php` kalau dipanggil dari root, tapi `../index.php` kalau dipanggil dari `buku/list.php` — **tidak mungkin** menulis satu baris HTML yang benar untuk kedua situasi itu sekaligus dalam satu file `header.php` yang sama.

**Solusi yang dipakai: hitung prefix-nya otomatis pakai PHP**, bukan
ditulis manual. Inilah isi 4 baris yang belum dijelaskan:

```php
$__jobsheetRoot = dirname(__DIR__);
$__scriptDir = dirname($_SERVER['SCRIPT_FILENAME']);
$__rel = ltrim(str_replace('\\', '/', substr($__scriptDir, strlen($__jobsheetRoot))), '/');
$base = $__rel === '' ? '' : str_repeat('../', substr_count($__rel, '/') + 1);
```

- **`$__jobsheetRoot = dirname(__DIR__);`** — `__DIR__` di dalam `header.php` selalu berisi folder `includes/`. `dirname()` naik satu tingkat dari situ, jadi `$__jobsheetRoot` adalah folder root proyek ini (`jobsheet-07/`) — **selalu benar**, tidak peduli lewat domain apa proyek ini diakses.
- **`$__scriptDir = dirname($_SERVER['SCRIPT_FILENAME']);`** — `$_SERVER['SCRIPT_FILENAME']` adalah superglobal lain (mirip `$_SESSION`/`$_POST`) berisi path lengkap file PHP yang **pertama kali dijalankan** untuk request ini — misalnya `buku/list.php`, **bukan** `header.php` walaupun kode ini sedang berjalan di dalam `header.php` (ingat lagi `include`: setelah di-*include*, semuanya jadi "satu file besar", termasuk nilai `$_SERVER['SCRIPT_FILENAME']`-nya).
- **`$__rel = ...`** — mengambil bagian path **setelah** folder root proyek. Kalau halaman yang dibuka adalah `index.php`, hasilnya string kosong. Kalau halaman yang dibuka `buku/list.php`, hasilnya `"buku"`. `str_replace('\\', '/', ...)` diperlukan karena Windows memakai `\` sebagai pemisah folder, beda dengan `/` yang dipakai di URL.
- **`$base = ...`** — kalau `$__rel` kosong, `$base` jadi string kosong (tidak perlu naik folder sama sekali). Kalau `$__rel` berisi satu segmen folder (`"buku"`), `$base` jadi satu `"../"`. Rumus ini otomatis menghasilkan `"../../"`, dst. kalau suatu saat ada halaman yang lebih dalam lagi.

Intinya: `$base` menghitung **"berapa level saya perlu naik untuk
sampai ke root proyek ini"**, dihitung dari **struktur folder di disk**
(lewat `__DIR__` dan `SCRIPT_FILENAME`) — bukan dari alamat domain di
browser. Perhitungannya dilakukan **sekali** di `header.php`, hasilnya
dipakai berulang di setiap `href`/`src` lewat `<?php echo $base; ?>` —
prinsip yang sama dengan alasan `header.php`/`footer.php` sendiri
dibuat: **jangan ulang pekerjaan yang sama di banyak tempat**.

**Konsekuensinya**: proyek ini **tidak lagi terikat** harus dijalankan
dengan folder `jobsheet-07/` sebagai akar server. `php -S localhost:8000`
dari dalam folder `jobsheet-07/` tetap valid dan paling sederhana untuk
latihan mandiri — tapi proyek ini **juga** tetap benar diakses lewat
Laragon meskipun document root Apache-nya bukan folder `jobsheet-07/`
itu sendiri (misalnya `http://dp2026.test/kode-praktikum/jobsheet-07/`),
karena `$base` menyesuaikan diri secara otomatis, bukan digantungkan ke
akar domain seperti pendekatan *root-relative path* (`/index.php`) yang
lebih sederhana tapi mengharuskan server persis di folder proyek.

## 1.4 Bagaimana Dua Potongan Ini Disatukan?

Membuka tag `<main>` tapi tidak menutupnya. Ini karena **konten spesifik** tiap halaman (misalnya `<section>` "Selamat Datang..." di Beranda) ditulis **di antara** pemanggilan `include header.php` dan `include footer.php`:

```php
<?php
$page_title = "Beranda";
include __DIR__ . '/includes/header.php';
?>
        <section>
            <h2>Selamat Datang di Sistem Perpustakaan Mini</h2>
            ...
        </section>
<?php include __DIR__ . '/includes/footer.php'; ?>
```

Dan `includes/footer.php`:

```php
    </main>

    <footer>
        <p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 7</p>
    </footer>
    <script src="<?php echo $base; ?>assets/js/app.js"></script>
    <?php if (!empty($extra_scripts)): foreach ($extra_scripts as $src): ?>
    <script src="<?php echo $src; ?>"></script>
    <?php endforeach;
    endif; ?>
</body>
</html>
```

Perhatikan `footer.php` ikut memakai `<?php echo $base; ?>` untuk
`<script src="...">`-nya — variabel `$base` yang dihitung di
`header.php` **tetap tersedia** di sini karena `header.php` dan `footer.php` di-*include* dari file yang sama, jadi keduanya berbagi variabel yang sama persis seolah-olah satu file besar.

`footer.php` **menutup** apa yang dibuka `header.php`: `</main>`,
`<footer>`, lalu `</body></html>`. Ketika PHP memproses `index.php`,
urutan penggabungannya:

1. Seluruh isi `header.php` (buka `<html>`...`<main>`).
2. Konten `<section>` khusus Beranda yang ditulis di `index.php`.
3. Seluruh isi `footer.php` (`</main>`...tutup `</html>`).

Hasil akhirnya: **satu dokumen HTML utuh dan valid** yang dikirim ke browser — persis strukturnya seperti file HTML statis di jobsheet-jobsheet sebelumnya, hanya saja sekarang "dirakit" dari 3 potongan file berbeda di server, bukan ditulis manual berulang di
setiap file.

## 1.5 Pola `$extra_scripts` untuk Script Tambahan per Halaman

```php
<?php if (!empty($extra_scripts)): foreach ($extra_scripts as $src): ?>
<script src="<?php echo $src; ?>"></script>
<?php endforeach;
endif; ?>
```

Ini contoh **sintaks alternatif** PHP untuk struktur kontrol — `if (...): ... endif;` dan `foreach (...): ... endforeach;` alih-alih kurung kurawal `{ }` biasa. Sintaks ini **sengaja dipilih** untuk kode PHP yang bercampur dengan HTML (seperti di sini) karena lebih mudah
dibaca dibanding kurung kurawal yang bisa membingungkan di antara tag-tag HTML. `!empty($extra_scripts)` memeriksa apakah variabel ini **ada isinya** (variabel ini sendiri belum pernah dipakai secara aktif di jobsheet-07 — disiapkan sebagai "kait" untuk kebutuhan mendatang, mirip semangat menyiapkan struktur
lebih awal  saat merancang sebelum coding).