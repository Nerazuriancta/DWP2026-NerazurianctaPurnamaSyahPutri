## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. Perubahan Path `CSS` pada File `HTML`

Penambahan file `CSS` pada setiap halaman `HTML` menggunakan path yang berbeda sesuai dengan lokasi file `HTML`.

| File `HTML` | Path `CSS` | Penjelasan |
|---|---|---|
| `index.html` | `assets/style.css` | Karena file `index.html` berada di folder utama, file css dapat langsung diakses melalui folder ke folder utama, kemudian masuk ke folder `assets` |
| `buku/list.html` | `../assets/style.css` | Karena file berada di dalam folder `buku`, `../` digunakan untuk kembali satu folder ke folder utama, kemudian masuk ke folder `assets`. |
| `buku/tambah.html` | `../assets/style.css` | Karena dile berada di dalam folder `buku`. path menggunakan `../` untuk kembali ke folder utama sebelum menuju folder `assets`. |
| `anggota/list.html` | `../assets/style.css` | Karena file berada di dalam folder `anggota`, `../` digunakan untuk kembali satu folder ke folder utama, kemudian menuju folder `assets`. |
| `anggota/tambah.html` | `../assets/style.css` | Karena file berada di dalam folder `anggota`, path menggunakan `../` untuk kembali satu folder sebelum masuk ke folder `assets`. |

## 1.1 Kesimpulan
Path file CSS disesuaikan dengan lokasi masing-masing file HTML. File yang berada di folder utama menggunakan `assets/style.css`, sedangkan file yang berada satu tingkat di dalam folder seperti `buku` dan `anggota` menggunakan `../assets/style.css`.