## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. Perubahan pada CSS untuk Jobsheet 3

Pada Jobsheet 3, file [style.css](../assets/css/style.css) dimodifikasi dengan menambahkan pengaturan **tabel responsif, hamburger menu, dan responsive breakpoint** agar tampilan website dapat menyesuaikan ukuran layar.

## 2.1 Tabel Responsif
```css
.table-responsive {
    overflow-x: auto;
}
```
Kode tersebut ditambahkan agar tabel tetap dapat ditampilkan pada layar berukuran kecil. Jika ukuran tabel melebihi lebar layar, pengguna dapat melakukan scroll secara horizontal.

## 2.2 Hamburger Menu
```css
.nav-toggle {
    display: none;
}

.nav-toggle-label {
    display: none;
    font-size: 1.6rem;
    color: #fff;
    cursor: pointer;
}
```
Kode tersebut digunakan untuk mengatur checkbox dan ikon hamburger. Checkbox disembunyikan, sedangkan ikon hamburger awalnya juga disembunyikan dan akan ditampilkan pada ukuran layar mobile.

## 2.3 Responsive Breakpoint untuk Tablet
```css
@media (max-width: 768px) {
    main section:nth-of-type(2) {
        grid-template-columns: repeat(2, 1fr);
    }
}
```
Kode tersebut ditambahkan untuk menyesuaikan tampilkan kartu statistik pada perngkat dengan lebar layar maksimal 768px. Kartu statistik yang sebelumnya terdiri dari tiga kolom akan berubah menjadi dua kolom.

## 2.4 Responsive Breakpoint untuk Mobile
```css
@media (max-width: 480px) {
    header {
        position: relative;
    }

    .nav-toggle-label {
        display: block;
    }
}
```
Pada ukuran layar maksimal 480px, ikon hamburger akan ditampilkan dan header diatur menggunakan `position: relative`.

## 2.5 Navigasi Mobile
```css
header nav {
    display: none;
    width: 100%;
    order: 3;
    margin-top: 1rem;
}

.nav-toggle:checked ~ nav {
    display: block;
}
```
Navigasi disembunyikan secara default pada perangkat mobile. Ketika ikon hamburger ditekan dan checkbox aktif, navigasi akan ditampilkan.

## 2.6 Menu Navigasi Vertikal
```css
header nav ul {
    flex-direction: column;
    gap: 0.75rem;
}
```
Menu navigasi yang sebelumnya tersusun secara horizontal diubah menjadi vertikal pada perangkat mobile.

## 2.7 Kartu Statistik Mobile
```css
main section:nth-of-type(2) {
    grid-template-columns: 1fr;
}
```
Pada perangkat mobile, tiga kartu statistik akan ditampilkan dalam satu kolom agar lebih mudah dilihat.

## 2.8 Form Responsif
```css
form input, form select {
    max-width: 100%;
}
```
Kode tersebut membuat input dan select menggunakan lebar penuh pada layar mobile sehingga formulir lebih mudah digunakan.

## 2.9 Kesimpulan
Pada Jobsheet 3, file [style.css](../assets/css/style.css) ditambahkan dengan pengaturan responsif menggunakan `@media`. Perubahan tersebut meliputi tabel responsif, ikon hamburger, navigasi mobile, perubahan jumlah kolom kartu statistik, dan penyesuaian ukuran formulir. Dengan perubahan ini, tampilan SIMPUS-Mini dapat menyesuaikan diri dengan ukuran layar tablet dan mobile.