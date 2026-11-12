# Tangkap Bentuk

Game menangkap bentuk yang jatuh dengan keranjang. Perintah diucapkan lewat suara
("Tangkap bentuk lingkaran"), keranjang digerakkan dengan kamera, atau sementara dengan keyboard.

## Struktur folder

```
index.html
assets/
  bulat/            bulat1.png, bulat2.png, ...
  segitiga/         segitiga1.png, segitiga2.png, ...
  kotak/            kotak1.png, kotak2.png, ...
  persegipanjang/   persegipanjang1.png, persegipanjang2.png, ...
```

## Menambah gambar baru

Taruh gambar di folder bentuknya dengan nomor berurutan: `bulat2.png`, `bulat3.png`, dan seterusnya
(format `.png` atau `.jpg`). Game mencari nomor satu per satu sampai tidak ada file lagi,
jadi **jangan melompati nomor**. Tidak perlu mengubah kode.

Saran ukuran: PNG transparan 128x128 piksel, di bawah 15 KB per gambar.

## Menambah jenis bentuk baru (misalnya bintang)

1. Buat folder `assets/bintang/` berisi `bintang1.png`, dst.
2. Di `index.html`, tambahkan satu baris pada daftar `SHAPES`:
   `{ key: 'bintang', label: 'bintang' },`

`label` adalah kata yang diucapkan dan ditampilkan.

## Kontrol

| Kontrol | Fungsi |
|---|---|
| A / panah kiri | Keranjang ke kiri |
| D / panah kanan | Keranjang ke kanan |
| Kamera | Geser badan ke kiri dan kanan |
| Sentuh atau tahan klik mouse lalu geser | Keranjang mengikuti jari atau kursor |
| P atau Esc | Jeda |
| C | Kalibrasi ulang kamera |
| M | Suara hidup atau mati |
| V | Tampilkan atau sembunyikan pratinjau kamera |
| R atau klik kotak kuning | Ulangi perintah suara |

## Cara kerja kamera

Saat mulai, game meminta pemain keluar dari bingkai selama beberapa detik untuk merekam latar belakang.
Setelah itu, bagian gambar yang berbeda dari latar dianggap pemain, dan posisi kiri-kanannya
menggerakkan keranjang. Gambar kamera diperkecil menjadi 64x48 piksel dan hanya diproses di perangkat,
tidak ada yang dikirim ke server.

Tips: cahaya cukup, latar tidak ramai, dan hanya satu orang di depan kamera.
Pengaturan sensitivitas ada di objek `CAM` pada bagian konfigurasi `index.html`.

## Menjalankan

Kamera hanya bisa dipakai lewat `https` atau `localhost`.

- **GitHub Pages**: upload semua file, lalu aktifkan Settings > Pages (branch `main`, folder `/root`).
- **Lokal**: jalankan `python -m http.server 8000` di folder ini, lalu buka `http://localhost:8000`.

Suara perintah memakai suara bahasa Indonesia bawaan perangkat. Jika perangkat tidak punya suara Indonesia,
tulisan perintah tetap tampil di layar.
