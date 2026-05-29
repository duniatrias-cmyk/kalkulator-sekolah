# CONTEXT.md — Cermin Sekolah
> Dokumen ini berisi konteks project untuk digunakan di awal sesi Claude Code.
> Update dokumen ini setiap kali ada keputusan desain atau fitur baru.

---

## Tujuan

Membantu orang tua membandingkan calon sekolah sebelum keputusan final.
Kalkulator ini bukan alat rekomendasi — ia bekerja sebagai **cermin**, bukan hakim.
Tidak ada jawaban benar atau salah. Output-nya membantu orang tua melihat lebih jelas, bukan memutuskan untuk mereka.

---

## Pengguna

- Orang tua murid yang sedang mempertimbangkan pilihan sekolah untuk anaknya
- Kemungkinan 50:50 antara ayah dan ibu
- Mayoritas mengakses via mobile
- Diasumsikan **orang tua awam** — bukan pendidik atau akademisi
- Kemungkinan baru pertama kali menyekolahkan anak, atau memiliki anak yang sudah sekolah sebelumnya

---

## Filosofi Desain

- Bahasa harus sederhana — hindari istilah teknis atau jargon pendidikan
- Tone: hangat, tidak menghakimi, seperti teman yang membantu berpikir
- Semua wording ditulis dari sudut pandang orang tua awam
- Tidak ada label "terbaik" atau "pilih ini" — hanya "paling selaras"
- Hasil adalah refleksi, bukan keputusan

---

## Stack & Deploy

- **Single file HTML** — semua CSS dan JS dalam satu file `index.html`
- Tidak ada dependensi eksternal kecuali Google Fonts
- Semua chart dan visual dibuat dengan SVG murni (tanpa library)
- Deploy: **GitHub Pages** di `https://duniatrias-cmyk.github.io/kalkulator-sekolah/`
- Repository: `duniatrias-cmyk/kalkulator-sekolah`

---

## Fitur yang Sudah Ada

### Step 1 — Profil Keluarga
- Input anggaran bulanan (Rp)
- Pilih visi pendidikan keluarga (tag pilihan ganda: 8 opsi)
- Skala prioritas 3 dimensi via slider: Biaya Sekolah, Kecocokan Tujuan, Jarak dari Rumah
- Toleransi waktu tempuh (dropdown)
- Fitur konteks anak yang sudah sekolah: jika punya anak yang sudah sekolah, user mengisi biaya bulanan yang sudah berjalan — sistem otomatis menghitung sisa anggaran untuk anak berikutnya

### Step 2 — Data Sekolah
- Tab untuk 3 sekolah (Sekolah 3 opsional, minimal 2 wajib diisi)
- Per sekolah: nama, biaya masuk, biaya bulanan, jarak tempuh, arah pendidikan (tag pilihan ganda)
- Validasi: minimal 2 sekolah terisi sebelum bisa lanjut

### Step 3 — Hasil (Cermin)
- Skor keselarasan per sekolah (0–100), diurutkan dari tertinggi
- Label "Paling Selaras" untuk skor tertinggi
- Radar chart SVG murni (3 dimensi: Biaya Sekolah, Kecocokan Tujuan, Jarak dari Rumah)
- Bar detail per dimensi dengan perbandingan antar sekolah
- Narasi reflektif per sekolah — menunjukkan dimensi mana yang perlu dipertimbangkan lebih lanjut
- Catatan penutup: menjelaskan keterbatasan cermin + disclaimer biaya masuk tidak dihitung
- Instruksi screenshot per device (iPhone, Android, Laptop/PC) — karena hasil tidak tersimpan
- Tombol "Hitung Ulang" dengan dialog konfirmasi sebelum halaman di-reset

### Footer
- Link DM Instagram @triasabdullah untuk masukan
- Tombol traktir kopi (toggle) — menampilkan rekening Bank Jago dengan tombol copy

---

## Hal yang Sengaja Tidak Dimasukkan

| Yang tidak ada | Alasan |
|---|---|
| Rekomendasi pasti ("pilih sekolah ini") | Bertentangan dengan filosofi cermin — keputusan tetap di tangan orang tua |
| Biaya masuk / uang pangkal dalam kalkulasi | Biaya ini satu kali dan sangat bervariasi — bisa menyesatkan jika dijumlah dengan biaya rutin |
| Simpan / ekspor data | Sengaja tidak ada — user didorong screenshot agar sadar ini alat bantu, bukan arsip |
| Login atau akun | Tidak perlu — privasi terjaga, tidak ada data yang dikirim ke server |

---

## Keputusan Desain yang Sudah Dibuat

- **Warna:** Skema warm cream + amber + sage + rose — terasa hangat, tidak dingin seperti dashboard korporat
- **Font:** Lora (serif, untuk judul) + DM Sans (untuk body) — kombinasi personal tapi tetap bersih
- **Slider prioritas:** Skala 1–10 per dimensi, bukan alokasi 100% — lebih intuitif untuk orang awam
- **Tag visi:** Pilihan ganda, bukan radio button — orang tua bisa punya lebih dari satu prioritas
- **Chart:** SVG murni tanpa Chart.js — menghindari dependensi CDN yang bisa error di berbagai environment

---

## Fitur yang Direncanakan

Belum ada — menunggu feedback dari pengguna pertama.

---

## Catatan untuk Claude Code

- Selalu pertahankan single file — jangan pisahkan CSS atau JS ke file terpisah
- Setiap perubahan wording harus melewati filter: *"apakah orang tua awam akan langsung paham?"*
- Jika ada perubahan kalkulasi skor, dokumentasikan logikanya di komentar dalam kode
- Setelah selesai edit, selalu push ke branch `main`
- Test di tampilan mobile (lebar ~390px) sebelum dianggap selesai
