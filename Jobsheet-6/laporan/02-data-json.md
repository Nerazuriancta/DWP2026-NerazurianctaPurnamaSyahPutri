## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. Penjelasan File: `buku.json` & `anggota.json`
Sebelum membedah kode yang membaca file JSON ini, kenali dulu isi dan strukturnya.

## 2.1 `data/buku.json` 10 Objek Buku
```json
[
    { "judul": "Laskar Pelangi", "pengarang": "Andrea Hirata", "tahun": 2005, "stok": 4 },
    { "judul": "Bumi Manusia", "pengarang": "Pramoedya Ananta Toer", "tahun": 1980, "stok": 2 },
    { "judul": "Negeri 5 Menara", "pengarang": "Ahmad Fuadi", "tahun": 2009, "stok": 0 },
    { "judul": "Filosofi Teras", "pengarang": "Henry Manampiring", "tahun": 2018, "stok": 5 },
    { "judul": "Ronggeng Dukuh Paruk", "pengarang": "Ahmad Tohari", "tahun": 1982, "stok": 1 },
    { "judul": "Cantik Itu Luka", "pengarang": "Eka Kurniawan", "tahun": 2002, "stok": 3 },
    { "judul": "Pulang", "pengarang": "Tere Liye", "tahun": 2015, "stok": 2 },
    { "judul": "Sang Pemimpi", "pengarang": "Andrea Hirata", "tahun": 2006, "stok": 6 },
    { "judul": "Perahu Kertas", "pengarang": "Dee Lestari", "tahun": 2009, "stok": 0 },
    { "judul": "Gadis Kretek", "pengarang": "Ratih Kumala", "tahun": 2012, "stok": 4 }
]
```
Bandingkan dengan tabel Daftar Buku yang ada pada jobsheet-01: 5 buku pertama persis sama dengan data dummy yang dulu ditulis manual di HTML — hanya sekarang formatnya JSON, dan ditambah 5 buku baru (total jadi 10), yang tidak akan pernah tampil kalau kamu membuka HTML lama karena baris HTML lama memang statis dan tidak terhubung ke file ini sama sekali.

## 2.2 `data/anggota.json` 8 Objek Anggota
```json
[
    { "no_anggota": "A001", "nama": "Siti Aminah", "alamat": "Malang", "no_hp": "0812xxx" },
    { "no_anggota": "A002", "nama": "Budi Santoso", "alamat": "Batu", "no_hp": "0813xxx" },
    { "no_anggota": "A003", "nama": "Nerazuriancta", "alamat": "Probolinggo", "no_hp": "0814xxx" },
    { "no_anggota": "A004", "nama": "Sarah Geiza", "alamat": "Probolinggo", "no_hp": "0815xxx" },
    { "no_anggota": "A005", "nama": "Findi Findoy", "alamat": "Malang", "no_hp": "0816xxx" },
    { "no_anggota": "A006", "nama": "Firstyara Hilma", "alamat": "Batam", "no_hp": "0817xxx" },
    { "no_anggota": "A007", "nama": "Ayunda", "alamat": "Probolinggo", "no_hp": "0818xxx" },
    { "no_anggota": "A008", "nama": "Ahmad Rizky", "alamat": "Malang", "no_hp": "0819xxx" }
]
```
## 2.3 Kenapa Nama Kuncinya Persis Sama dengan Atribut `name` di Form?
Perhatikan kunci-kunci JSON ini: `judul`, `pengarang`, `tahun`, `stok` untuk buku; `no_anggota`, `nama`, `alamat`, `no_hp` untuk anggota, persis sama dengan atribut `name` pada input form Tambah Buku/Tambah Anggota. Ini bukan kebetulan — penamaan yang konsisten di seluruh aplikasi (HTML, JSON, dan nanti database sungguhan) membuat data jauh lebih mudah dilacak: satu field yang sama selalu punya nama yang sama di setiap lapisan, tidak perlu "menerjemahkan" nama field yang berbeda-beda di setiap tempat.

## 2.4 Tipe Data di Dalam JSON
JSON mendukung beberapa tipe nilai dasar, dan kedua file ini memakai 2 di antaranya:
| Tipe | Contoh di Data Ini | Ciri |
|---|---|---|
| **String** (teks) | `"Laskar Pelangi"`, `"A001"` | Selalu diapit tanda kutip dua. |
| **Number** (angka) | `2005`, `4`, `0` | **Tidak** diapit tanda kutip. |

Perhatikan `"tahun": 2005` dan `"stok": 4` ditulis tanpa tanda kutip, artinya JavaScript akan membacanya sebagai angka sungguhan, bukan teks. Ini penting: kalau kamu menuliskan `"tahun": "2005"` (dengan kutip), nilainya akan jadi teks `"2005"`, yang meskipun terlihat sama di layar, tidak bisa langsung dipakai untuk perbandingan angka seperti `tahun > 2000` tanpa dikonversi dulu (ingat `parseInt()` yang dipakai untuk keperluan serupa di dokumentasi [Jobsheet-5](../../Jobsheet-5/)). Sebaliknya, perhatikan `"no_anggota": "A001"` sengaja ditulis sebagai string (bukan angka) — konsisten dengan pembahasan dokumentasi [jobsheet-1](../../Jobsheet-1/), kenapa nomor anggota memakai huruf+angka, jadi tidak mungkin disimpan sebagai tipe angka murni.

## 2.5 Bagaimana Data Ini "Berubah" Jadi Objek JavaScript?
File .json ini hanyalah teks yang disimpan di server/folder — belum menjadi objek JavaScript yang bisa diakses lewat buku.judul sampai benar-benar diambil dan diuraikan (parse) oleh kode. Proses ini dilakukan oleh method .json() yang dipanggil setelah fetch() berhasil.