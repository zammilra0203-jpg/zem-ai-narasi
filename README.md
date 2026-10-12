# Affiliate AI Studio — Muzammil

Aplikasi web berbasis satu file HTML untuk membantu membuat materi promosi produk affiliate: narasi, prompt video, **prompt gambar utama**, dan **empat prompt gambar per scene** yang saling berkaitan.

## Fitur

- Input informasi/deskripsi dan foto produk.
- Penyusunan narasi affiliate serta prompt video promosi.
- Satu prompt gambar utama sebagai referensi visual/frame pembuka.
- Empat prompt gambar terpisah untuk adegan video (scene 1–4).
- Tombol salin prompt agar mudah digunakan di layanan AI gambar/video lainnya.
- Opsi menggunakan Gemini API Key dari pengguna, serta mekanisme cadangan lokal jika tersedia pada fitur terkait.
- Tidak memerlukan unggahan foto model yang memegang produk.

> Aplikasi ini membuat **teks prompt**, bukan merender gambar atau video secara langsung.

## Cara menjalankan

1. Buka `index.html` di Chrome, Edge, atau browser modern lainnya.
2. Isi informasi produk dan unggah foto produk sesuai kebutuhan.
3. Jika ingin memakai fitur Gemini, masukkan Gemini API Key pada kolom yang tersedia.
4. Pilih pengaturan konten, kemudian klik **Buat Narasi Sekarang**.
5. Salin prompt gambar utama, prompt gambar scene 1–4, dan prompt video untuk digunakan di platform generatif pilihan Anda.

## Cara upload ke GitHub

1. Buat repository baru di GitHub (contoh: `affiliate-ai-studio`).
2. Upload **`index.html`** dan **`README.md`** ke bagian utama/root repository.
3. Klik **Commit changes**.
4. Jika ingin aplikasi bisa dibuka sebagai website, buka **Settings → Pages**.
5. Pada **Build and deployment**, pilih **Deploy from a branch**, branch **main**, folder **/(root)**, lalu simpan.
6. Tunggu proses deploy. Situs biasanya tersedia di `https://USERNAME.github.io/NAMA-REPOSITORY/` (ganti sesuai akun dan repository).

## Keamanan API Key

- **Jangan menuliskan API Key langsung ke kode HTML atau README, dan jangan mengunggah kunci rahasia ke GitHub.**
- Masukkan API Key secara manual saat menggunakan aplikasi. Opsi **Ingat API Key di perangkat ini** menyimpan kunci pada penyimpanan browser perangkat tersebut; hindari opsi ini pada komputer bersama.
- Karena ini aplikasi HTML sisi klien, permintaan Gemini dilakukan dari browser pengguna. Untuk aplikasi publik dengan API Key milik pengelola, sebaiknya gunakan backend/proxy yang menyimpan kunci secara aman, bukan menaruhnya dalam JavaScript publik.
- Perhatikan kuota, biaya, dan kebijakan layanan Gemini.

## Struktur repository

```text
affiliate-ai-studio/
├── index.html
└── README.md
```

## Catatan

Versi ini dapat dijalankan sebagai file HTML lokal maupun di-host sebagai situs statis melalui GitHub Pages. Ketersediaan fitur Gemini bergantung pada API Key, koneksi internet, akses model, dan kebijakan layanan.

---

Dikembangkan untuk **Affiliate AI Studio · Muzammil**.
