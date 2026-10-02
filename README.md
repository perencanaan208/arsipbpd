# Arsip & Data BPD Desa Baleharjo (Vercel)

Repo ini hanya **pembungkus iframe**. Semua tampilan dan logika tetap di Google Apps Script,
jadi setiap perubahan cukup dilakukan di Apps Script (Deploy → Manage deployments → Edit → New version).
URL web app tidak berubah selama Anda mengedit deployment yang sama.

## Cara pakai
1. Buka `index.html`, ganti nilai `GAS_URL` dengan URL Web App (berakhiran `/exec`).
2. Upload folder ini ke repo GitHub.
3. Di Vercel: **Add New → Project → Import** repo tersebut. Framework: *Other*, tanpa build command, tanpa output directory. Klik Deploy.

## Syarat di sisi Apps Script
- `doGet` harus memakai `setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL)` (sudah ada di Code.gs).
- Saat Deploy web app, **Who has access** harus **Anyone**. Jika "Only myself", iframe akan menampilkan
  halaman login Google yang diblokir di dalam iframe.
- Di `appsscript.json` bagian `webapp`, ubah `"access": "MYSELF"` menjadi `"access": "ANYONE_ANONYMOUS"`.

## Keamanan
Dengan akses "Anyone", siapa pun yang memiliki link bisa membuka dan mengubah data. Jangan bagikan link
sembarangan. Jika perlu, minta ditambahkan PIN/login di aplikasi.

## PWA (bisa di-install dengan ikon E-ARSIP BPD)
File yang ditambahkan: `manifest.webmanifest`, `sw.js`, `favicon.ico`, dan folder `icons/`.
Setelah deploy ke Vercel:
- **PC (Chrome/Edge):** buka situsnya, klik ikon install di ujung kanan address bar (atau menu ⋮ → *Install E-Arsip BPD*).
- **Android (Chrome):** menu ⋮ → *Install app* / *Tambahkan ke layar utama*.
- **iPhone (Safari):** tombol Share → *Add to Home Screen* (memakai `apple-touch-icon.png`).

Jika sebelumnya sudah pernah dipasang dengan ikon lama, hapus dulu aplikasinya lalu install ulang agar ikon baru muncul.
Catatan: aplikasi tetap membutuhkan internet karena isinya dimuat dari Apps Script.
