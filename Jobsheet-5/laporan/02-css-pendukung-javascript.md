## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. CSS Pendukung Fitur JavaScript
Beberapa baris `style.css` berubah atau ditambah, semuanya untuk mendukung fitur JavaScript baru.

## 2.1 Hamburger: dari `.nav-toggle` ke Tombol Asli
Dihapus dari `style.css`:
```css
.nav-toggle {
    display: none;
}
```
Aturan ini dulu menyembunyikan elemen `<input type="checkbox">`. Karena elemen checkboxnya sendiri sudah dihapus dari HTML, aturan CSS utuk menyembunyikannya juga tidak diperlukan lagi.

Ditambahkan ke `.nav-toggle-label` (yang sekarang menata elemen `<button>`, bukan `<label>`):
```css
.nav-toggle-label {
    display: none;
    font-size: 1.6rem;
    color: #fff;
    background: none;
    border: none;
    cursor: pointer;
}
```
Dua baris baru, `background: none;` dan `border: none;`, tidak diperluka saat elemennya masih `<label>` (label tidak punya latar atau bingkai bawaan), tapi wajib sekarang karena elemennya adalah `<button>` dan tombol HTML secara default punya latar abu-abu dan bingkai 3D bawaan browser. Tanpa dua baris ini tombol hamburger akan terlihat seperti kotak abu-abu biasa, bukan ikon ☰ polos yang menyatu dengan warna header biru.

Berubah di dalam `@media (max-width: 480px;)`:
```css
header nav.nav-open {
    display: block;
}
```
Sebelumnya (jobsheet-03): `.nav-toggle:checked ~ nav { display: block; }`, selector berbasis status checkbox (`:checked`) dan sibling combinator `~`. Sekarang selectornya jauh lebih sederhana: `header nav.nav-open`, elemen `<nav>` di dalam `<header>` yang punya class `nav-open`. Tidak ada lagi pseudo-class atau sibling combinator sama sekali, karena status "menu terbuka" sekarang murni ditentukan oleh ada atau tidaknya class `nav-open` dan yang menambah/menghapus class itu adalah JavaScript, bukan lagi status tercentang sebuah checkbox tersembunyi.

## 2.2 Gaya Baru: Pesan Error Validasi
```css
/* ===== Pesan Error Validasi ===== */
.error {
    display: block;
    color: #d9534f;
    font-size: 0.85rem;
    margin-top: 0.25rem;
}
```
Class `error` ini belum ada di HTML manapun secara statis, class ini akan dibuat dan disisipkan sepenuhnya oleh JavaScript setiap kali validasi form gagal. CSS ini menyiapkan bagaimana rupanya kalau elemen `<span class="error">` itu benar-benar muncul nanti:
- `display: block;` memastikan pesan error tampil di baris baru sendiri, di bawah kotak input, bukan menempel sejajar di sampingnya (elemen `<span>` secara default bersifat inline).
- `color: #d9534f` warna merah sama persis dengan warna tombol Hapus, konsisten menandakan "sesuatu yang perlu perhatian/tindakan" di seluruh aplikasi.
- `font-size: 0.85rem;` dan `margin-top: 0.25rem;`, teks sedikit lebih kecil dari input di atasnya, dengan jarak tipis supaya terlihat jelas sebagai keterangan tambahan, bukan menyatu dengan input.

## 2.3 Gaya Baru: Kolom Pencarian
```css
/* ===== Kolom Pencarian ===== */
.search-box {
    margin-bottom: 1rem;
}

.search-box input {
    width: 100%;
    max-width: 320px;
    padding: 0.5rem 0.75rem;
    border: 1px solid #cdd4da;
    border-radius: 4px;
}
```
- `.search-box { margin-bottom: 1rem; }` memberi jarak antara kotak
  pencarian dan tabel di bawahnya.
- `.search-box input` menata kotak input pencarian mirip gaya input form pada jobsheet 2, border tipis, sudut membulat, padding nyaman — hanya saja `max-width` dibuat lebih sempit (`320px`, dibanding `400px` pada input form) karena kolom pencarian memang tidak perlu selebar field form biasa.