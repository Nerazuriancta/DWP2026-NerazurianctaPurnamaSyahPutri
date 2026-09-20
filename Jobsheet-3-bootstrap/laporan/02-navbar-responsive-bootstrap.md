## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. Navbar Responsif ala Bootstrap
Bab ini membedah bagian yang paling banyak berubah dari versi CSS murni: menu hamburger yang dulunya murni CSS (checkbox hack) sekarang memakai komponen `.navbar` bawaan Bootstrap yang membutuhkan JavaScript untuk animasi buka-tutupnya.

## 2.1 Struktur HTML lengkap
```html
<header class="navbar navbar-expand-lg navbar-dark" style="background-color:#1d5b8a;">
    <div class="container">
        <a class="navbar-brand fw-semibold" href="index.html">SIMPUS-Mini</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu" aria-controls="navMenu" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <nav class="collapse navbar-collapse" id="navMenu">
            <ul class="navbar-nav ms-auto">
                <li class="nav-item"><a class="nav-link active" href="index.html">Beranda</a></li>
                <li class="nav-item"><a class="nav-link" href="buku/list.html">Daftar Buku</a></li>
                ...
            </ul>
        </nav>
    </div>
</header>
```

## 2.2 Class `.navbar`, `.navbar-expand-lg`, `.navbar-dark`
| Class | Fungsi |
|---|---|
| `.navbar` | Menandai elemen ini sebagai komponen navbar Bootstrap — mengaktifkan seluruh perilaku dasarnya (flexbox internal, padding, dst). |
| `.navbar-expand-lg` | Kunci responsivitasnya. Berarti: navbar tampil horizontal terbuka (seperti desktop) mulai breakpoint `lg` (≥992px) ke atas. Di bawah `lg` (tablet & HP), navbar otomatis "terlipat" jadi tombol hamburger. |
| `.navbar-dark` | Mengatur skema warna teks/ikon navbar supaya kontras di atas latar gelap (teks putih, dsb) — cocok dipakai bersama `style="background-color:#1d5b8a;"` (biru tua) yang ditulis manual karena warna brand ini bukan salah satu tema warna bawaan Bootstrap. |
Bandingkan dengan pendekatan CSS murni yang hanya punya satu breakpoint hamburger (480px), di Jobsheet ini, breakpoint kapan navbar "terlipat" bisa diganti hanya dengan mengubah infix di nama class (`navbar-expand-md`, `navbar-expand-sm`, dst), tanpa menyentuh CSS sama sekali.

## 2.3 Tombol Hamburger: `.navbar-toggler`
```html
<button class="navbar-toggler" type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navMenu"
        aria-controls="navMenu"
        aria-expanded="false"
        aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
</button>
```

Ini adalah tombol asli (`<button>`), bukan `<label>` yang berpura-pura jadi tombol. Beberapa atribut pentingnya:

| Atribut | Fungsi |
|---|---|
| `data-bs-toggle="collapse"` | Memberi tahu JavaScript Bootstrap: "tombol ini mengontrol komponen **collapse** (buka/tutup)". Ini adalah **data attribute** — atribut HTML custom berawalan `data-` yang boleh dibaca skrip, konsepnya mirip `id`/`class` tapi khusus dipakai sebagai "pengait" JavaScript, bukan untuk styling CSS. |
| `data-bs-target="#navMenu"` | Menentukan **elemen mana** yang dibuka/ditutup ketika tombol ini diklik — mengacu ke `id="navMenu"` pada `<nav>` di bawahnya. Konsepnya mirip `for="nav-toggle"` yang menghubungkan label ke checkbox lewat `id` — bedanya di sini yang membaca hubungan `id` ini adalah **JavaScript**, bukan CSS. |
| `aria-controls`, `aria-expanded`, `aria-label` | Atribut **aksesibilitas** (accessibility) untuk pembaca layar (screen reader) — menjelaskan tombol ini mengontrol elemen apa dan statusnya sedang terbuka/tertutup. Bootstrap otomatis mengubah nilai `aria-expanded` lewat JavaScript saat tombol diklik. |
| `<span class="navbar-toggler-icon">` | Elemen kosong yang diberi gaya CSS bawaan Bootstrap berupa **ikon garis tiga (☰)** memakai `background-image` — pengganti karakter HTML entity `&#9776;` yang dipakai manual di versi CSS murni |

## 2.4 Elemen yang Dibuka-Tutup: `.collapse.navbar-collapse`
```html
<nav class="collapse navbar-collapse" id="navMenu">
    <ul class="navbar-nav ms-auto">
        ...
    </ul>
</nav>
```

- `.collapse`: class umum Bootstrap untuk elemen yang bisa disembunyikan/ditampilkan dengan animasi geser (slide). Secara default elemen ini tersembunyi kalau ukuran layar di bawah breakpoint `.navbar-expand-lg`.
- `.navbar-collapse`: varian khusus `.collapse` yang disesuaikan untuk konteks navbar (misalnya otomatis kembali terlihat horizontal begitu layar ≥ breakpoint `lg`, tanpa perlu status "terbuka/tertutup" sama sekali di layar besar).
- `id="navMenu"`: inilah target yang dicari `data-bs-target="#navMenu"`
- `.navbar-nav` pada `<ul>`: mengubah daftar `<li>` di dalamnya jadi item navbar dengan spacing dan layout flexbox bawaan Bootstrap menggantikan `header nav ul { display: flex; gap: 1.25rem; }` manual dari Jobsheet 2
- `ms.auton` (margin-start: auto): mendorong seluruh menu ke sisi kanan navbar, menggantikan `justify-content: space-between` pada `<header>` dari CSS murni.