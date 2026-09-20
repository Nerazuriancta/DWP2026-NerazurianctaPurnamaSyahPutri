## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 5. CSS: Gaya Flash Message

Satu-satunya perubahan `style.css` di jobsheet ini — mendukung tampilan flash message.

## 6.1 Kode CSS

```css
/* ===== Flash Message ===== */
.flash {
    padding: 0.75rem 1rem;
    border-radius: 6px;
    margin-bottom: 1rem;
    font-weight: 500;
}

.flash-success {
    background-color: #d4edda;
    color: #155724;
}

.flash-error {
    background-color: #f8d7da;
    color: #721c24;
}
```

## 6.2 Gaya Dasar (`.flash`)

`.flash` berisi gaya yang **selalu sama** untuk kedua jenis pesan: padding nyaman, sudut membulat (`border-radius`), jarak di bawahnya, dan teks yang sedikit tebal (`font-weight: 500`, konsisten dengan bobot yang dipakai label form).

## 6.3 Gaya Spesifik per Jenis (`.flash-success`, `.flash-error`)

Elemen flash message selalu punya **dua** class sekaligus: `flash` dan salah satu dari `flash-success`/`flash-error`. Kedua class tambahan ini memberi **warna berbeda** tergantung jenis pesannya:

| Class | Warna Latar | Warna Teks | Kesan |
|---|---|---|---|
| `.flash-success` | `#d4edda` (hijau sangat muda) | `#155724` (hijau tua) | Positif — data berhasil disimpan |
| `.flash-error` | `#f8d7da` (merah muda pucat) | `#721c24` (merah tua/marun) | Peringatan — ada yang perlu diperbaiki |

Pola warna hijau=sukses, merah=gagal ini konsisten dengan konvensi warna yang sudah kamu pakai sejak awal — ingat warna merah pada tombol Hapus dan pesan error validasi
memakai kombinasi merah yang senada (`#d9534f`) untuk maksud yang sama: menandakan sesuatu yang butuh perhatian pengguna.