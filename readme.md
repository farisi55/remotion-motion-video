# Blueprint Studio - AI Video Motion Animation Generator

Repositori ini berisi panduan untuk membuat video animasi grafis bergerak (motion animation) secara gratis menggunakan Blueprint Studio yang dikombinasikan dengan Claude AI, ElevenLabs, dan Remotion berdasarkan workflow dari channel YouTube *Naseh Ngulik AI*.

## 📌 Catatan Penting Sebelum Mulai
* **Fungsi Aplikasi:** Blueprint Studio menghasilkan kode program animasi, teks cerita/naskah, dan prompt—**bukan file video langsung**. Video akhir akan dibuat melalui kode oleh Claude, lalu dirender secara lokal menggunakan PC/Laptop Anda.
* **Akun Claude:** Fitur AI di dalam aplikasi ini membutuhkan akun Claude (Claude.ai) yang aktif.
* **Batas Free Tier:** Untuk akun gratis (penggunaan chat 5 jam), maksimal pembuatan video idealnya adalah sekitar 3 kali video per sesi chat untuk menghindari limitasi usage.

---

## 🛠️ Prasyarat & Bahan yang Diperlukan

1. **Blueprint Studio & Prompt Perintah:** Unduh file aplikasi dan instruksi master prompt melalui link Google Drive yang disediakan di deskripsi video.
2. **Node.js:** Wajib terinstal di komputer Anda. Unduh versi terbaru di [nodejs.org](https://nodejs.org).
3. **Akun ElevenLabs:** Digunakan untuk membuat Voice Over (Text to Speech) dan menghasilkan file transkrip (SRT).

---

## 🚀 Langkah-Langkah Pembuatan (12 Tahapan Workflow)

### Langkah 1: Instalasi Node.js
* Unduh installer Node.js sesuai dengan sistem operasi Anda (Windows/Mac/Linux).
* Jalankan file installer, klik `Next`/`Yes` sampai selesai.
* Verifikasi instalasi dengan membuka Command Prompt (CMD) dan ketik: `node -v`.

### Langkah 2: Mengunggah Blueprint Studio ke Claude
* Buka chat baru di Claude.ai.
* Unggah file Blueprint Studio yang sudah Anda unduh.
* Salin master prompt perintah yang disediakan dalam paket download, paste ke chat Claude, lalu tekan Enter. Tunggu hingga Artifact Blueprint Studio muncul dan berjalan.

### Langkah 3: Menentukan Ide & Naskah Cerita
* Pada antarmuka Blueprint Studio di Claude, masukkan **Ide Konten** Anda (contoh: *"Apa yang terjadi jika bumi berhenti berputar"*).
* Atur **Durasi** (misal: 60 atau 90 detik) dan **Aspek Rasio** (pilih `9:16` untuk format Shorts/Reels/TikTok).
* Pilih **Audiens** (Umum/Pelajar/Profesional) dan **Nada Bicara** (Santai/Edukatif/Dramatis).
* Klik generate untuk membiarkan AI menulis naskah cerita lengkap beserta visual hooks-nya.

### Langkah 4: Memilih Gaya Visual (Style Animation)
* Pilih gaya animasi yang Anda inginkan berdasarkan deskripsi yang tersedia (misal: gaya cetak biru teknis, garis putih di atas biru, dll).
* *Tips:* Anda bisa memilih opsi **"Kejutkan Aku"** agar Claude menentukan gaya visual paling pas yang sesuai dengan tema cerita Anda secara acak/random.

### Langkah 5: Membuat Voice Over (VO) & File SRT
* Salin teks naskah cerita final yang sudah dibuat oleh Claude.
* Buka website **ElevenLabs** dan masuk ke menu *Text to Speech*. Pastikan pengaturan bahasa diubah ke **Indonesian** agar pelafalannya natural. Pilih model suara (misal: suara 'Bian'). Paste naskah cerita lalu klik Generate dan unduh file `.mp3`-nya.
* Pindah ke menu *Speech to Text* di ElevenLabs, unggah file `.mp3` suara yang baru saja diunduh tadi, lalu jalankan proses transkrip. Setelah selesai, ekspor hasilnya menjadi file format **SRT** (`.srt`).
* Buka file SRT tersebut menggunakan Notepad, salin seluruh teks transkrip beserta penanda waktunya.

### Langkah 6: Membuat Prompt Animasi Remotion di Claude
* Kembali ke Blueprint Studio, pilih opsi output **Remotion** (direkomendasikan untuk hasil terbaik) dan pilih perangkat sistem operasi Anda (**Windows**).
* Salin kode prompt animasi final yang dihasilkan oleh Blueprint Studio.
* Buka **New Chat** (chat baru) di Claude, lalu paste prompt tersebut. Claude akan memberikan sugesti visual per babak/bit cerita. Ketik **"Lanjutkan"** jika Anda setuju untuk membiarkan Claude menulis seluruh kode animasi dalam bentuk file ZIP. Unduh file `.zip` tersebut setelah selesai di-generate.

### Langkah 7: Setup Folder Aset Animasi Lokal
* Ekstrak file `.zip` proyek animasi dari Claude ke folder komputer Anda.
* Ambil file Voice Over `.mp3` dari ElevenLabs, lalu ubah namanya (*rename*) menjadi `narasi.mp3`.
* Buka folder hasil ekstrak animasi, masuk ke dalam folder bernama `public`, lalu paste dan timpa (*overwrite*) file `narasi.mp3` bawaan contoh di sana dengan file narasi milik Anda.

### Langkah 8: Menginstal Package via Command Prompt (CMD)
* Buka Command Prompt (CMD).
* Arahkan direktori CMD ke folder tempat Anda mengekstrak file animasi menggunakan perintah `cd` (contoh: `cd C:\path\ke\folder\animasi-bumi-berhenti`).
* Jalankan perintah berikut secara berurutan untuk memasang dependensi:
  ```bash
  npm install
  ```
* Tunggu hingga proses instalasi package selesai sepenuhnya.

### Langkah 9: Meninjau (Preview) Animasi di Browser
* Untuk melihat pratinjau animasi sebelum di-render menjadi video, jalankan perintah:
  ```bash
  npm run dev
  ```
* Browser Anda akan otomatis terbuka dan menampilkan halaman lokal Remotion Player. Tekan *Play* untuk meninjau kecocokan gerakan grafis dengan suara narasi Anda.
* *Catatan Penting:* Apabila terdapat ketimpangan durasi (misal narasi audio aslinya 1 menit 15 detik tetapi durasi project diset 90 detik), sisa waktu akhir akan menjadi layar diam/kosong. Hal ini normal dan bisa dipotong nanti saat editing akhir.

### Langkah 10: Proses Rendering Video Akhir
* Jika pratinjau sudah dirasa pas, kembali ke jendela CMD dan hentikan server lokal dengan menekan tombol kombinasi `Ctrl + C` (lalu ketik `y` dan Enter jika diminta).
* Jalankan perintah render video dengan mengetik:
  ```bash
  npm run render
  ```
* Tunggu proses rendering kode menjadi file video MP4 selesai.

### Langkah 11: Mengambil Output Video & Finishing
* Setelah proses render selesai, file video `.mp4` yang siap pakai dapat Anda temukan di dalam folder bernama `out` pada direktori proyek Anda.
* Buka aplikasi editing video pihak ketiga (seperti **CapCut**) untuk melakukan finishing ringan, seperti memotong kelebihan durasi kosong (blank space) di bagian akhir video agar durasinya benar-benar pas dengan audio SRT.

### Langkah 12: Siap Publikasi!
* Video animasi grafis bergerak Anda kini sudah rapi dan siap diunggah ke platform short-form video pilihan Anda (TikTok, YouTube Shorts, atau Instagram Reels).

---
*Tutorial ini dirangkum dari channel YouTube **Naseh Ngulik AI**. Silakan tinggalkan komentar di video aslinya jika Anda berhasil membuat video animasi keren menggunakan metode ini!*

