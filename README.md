# Affiliate AI Studio — Muzammil

Aplikasi HTML untuk menyusun narasi TikTok Affiliate, **satu prompt gambar utama** dan prompt video 10 detik dengan empat scene.

## Fitur
- Upload foto produk dan foto deskripsi; tanpa upload foto model.
- Pilih model **Cewek / Perempuan** atau **Cowok / Laki-laki**.
- Hasilkan **satu prompt gambar 9:16** sebagai referensi visual utama, bukan empat gambar.
- Prompt video utama dan empat scene video menjaga **model yang sama** dari awal sampai akhir (wajah, rambut, pakaian, postur).
- Produk wajib sama dengan foto referensi pada seluruh video: bentuk, warna, merek, logo, teks, dan kemasan.
- Narasi, hook, CTA, dan tombol salin prompt.
- Integrasi Gemini dengan API key yang dimasukkan pengguna; tersedia fallback lokal.

## Jalankan
Buka `index.html` di browser modern atau aktifkan GitHub Pages pada branch `main`, folder `/ (root)`. Tidak memerlukan build.

## Upload GitHub
Unggah `index.html` dan `README.md` ke root repository, lalu commit. Jika sudah ada `index.html` lama, timpa dengan yang baru.

## Alur penggunaan
1. Upload foto produk dan deskripsi produk.
2. Pilih model perempuan atau laki-laki, gaya narasi, dan opsi lainnya.
3. Klik **Buat Narasi Sekarang**.
4. Salin **satu prompt gambar utama** dan gunakan untuk membuat gambar referensi.
5. Gunakan gambar itu sebagai referensi image-to-video bersama master prompt video dan empat scene video.

## Penting
Prompt menginstruksikan konsistensi identitas model dan detail produk, tetapi hasil akhir tetap bergantung pada kemampuan generator gambar/video. Periksa logo, tulisan, bentuk dan klaim produk sebelum publikasi. Aplikasi membuat **prompt**, bukan gambar/video secara langsung. Jangan memasukkan API key ke kode GitHub publik; untuk produksi gunakan backend yang aman.

Dibuat oleh **Muzammil**.
