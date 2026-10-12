# Affiliate AI Studio V4.1 — Dua Versi Video

Aplikasi HTML statis untuk membuat prompt konten affiliate dengan Gemini API Key dari Google AI Studio.

## Fitur
- Satu prompt gambar utama vertikal 9:16 untuk frame pembuka video.
- Model dewasa Indonesia, pilihan perempuan atau laki-laki, tampilan fotografis realistis.
- Dua prompt video 10 detik: (1) lengkap narasi Bahasa Indonesia; (2) tanpa narasi/dialog/lip-sync/musik bawaan, untuk ditambahkan backsound TikTok saat editing.
- Konsistensi identitas model dan produk dari foto referensi sepanjang empat scene.
- Analisis produk, lima hook, narasi, arahan visual, negative prompt, tombol salin.
- Pemeriksaan model Gemini yang tersedia untuk API Key pengguna.

## Cara pakai
1. Buka `index.html` di Chrome, atau terbitkan melalui GitHub Pages.
2. Masukkan Gemini API Key milik sendiri (jangan pernah commit key ke GitHub).
3. Unggah foto produk, isi deskripsi, pilih model perempuan/laki-laki dan gaya konten.
4. Klik tombol untuk menghasilkan hasil, lalu salin satu prompt gambar dan salah satu dari dua prompt video.
5. Untuk versi tanpa narasi, tambahkan musik yang memiliki izin penggunaan sesuai kebijakan platform saat editing.

## Batasan
- Aplikasi menghasilkan **teks prompt**, bukan gambar atau video langsung.
- Konsistensi wajah/produk merupakan instruksi untuk generator video, bukan jaminan hasil.
- Mode cadangan lokal tidak membaca foto produk dengan Gemini.
- Penyimpanan API Key di browser bersifat opsional dan kurang aman pada perangkat bersama; untuk aplikasi publik, gunakan backend/proxy yang aman.
- Hak penggunaan musik mengikuti ketentuan lisensi dan platform.

## GitHub Pages
Unggah `index.html` dan `README.md` ke root repository. Buka Settings → Pages → Deploy from a branch → main / (root).


## V4.2 — Simpan, buka, hapus proyek

- **Simpan Proyek** untuk menyimpan nama proyek, pilihan, foto produk, deskripsi, dan hasil prompt.
- **Buka** untuk memulihkan proyek tersimpan; **Hapus** untuk menghapus proyek dengan konfirmasi.
- **Penyimpanan otomatis** memulihkan pekerjaan setelah refresh atau membuka tab baru pada browser dan origin yang sama.
- Menggunakan **IndexedDB** secara lokal, tanpa server atau biaya tambahan.
- Data hanya ada pada browser/perangkat yang digunakan. Membersihkan data situs, mode privat, atau mengganti domain dapat menghapus/memisahkan data.
- **API Key tidak disimpan dalam proyek**; pengaturan Ingat API Key tetap terpisah dan opsional. Hindari menyimpan key pada perangkat bersama.
- Untuk hasil terbaik, gunakan URL GitHub Pages yang sama setiap kali.


## Pembaruan V4.3 — Karakter model pria
Jika memilih model laki-laki, prompt gambar utama dan kedua versi prompt video menetapkan pria Indonesia tampan usia 25–27 tahun, kulit putih/cerah, brewok tipis rapi, pose santai, ekspresi spontan natural dan tidak kaku. Identitas wajah, pakaian, karakter serta detail produk dijaga konsisten sepanjang video. Pilihan perempuan tetap tersedia tanpa karakteristik pria.
