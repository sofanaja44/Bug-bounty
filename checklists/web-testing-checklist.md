# ✅ Checklist Pengujian Web

Checklist praktis saat menguji target **yang in-scope & diizinkan**. Centang sambil jalan.
Salin per target ke `notes/`. Hormati scope & rate limit di setiap langkah.

> Bukan untuk dijalankan membabi buta — pakai sebagai pengingat area, bukan pengganti berpikir.

---

## 0. Pra-pengujian
- [ ] Baca **scope** & aturan program sampai paham
- [ ] Catat aset in-scope / out-of-scope
- [ ] Catat batasan (rate limit, akun uji, larangan scanner)
- [ ] Siapkan file catatan target di `notes/`

## 1. Recon (dalam scope)
- [ ] Enumerasi subdomain (untuk wildcard scope) → cek mana yang in-scope
- [ ] Identifikasi teknologi (framework, server, versi)
- [ ] Content discovery (direktori/file tersembunyi) sesuai kewajaran
- [ ] Kumpulkan endpoint & parameter (juga dari arsip/JS)
- [ ] Cari `robots.txt`, `sitemap.xml`, `/.well-known/security.txt`

## 2. Mapping (pakai aplikasi sebagai user normal)
- [ ] Daftar / login dengan **akun uji** sendiri (buat 2 akun untuk tes akses)
- [ ] Jelajahi semua fitur; lewatkan via proxy (Burp)
- [ ] Tandai: titik input, data sensitif, perbedaan peran (user vs admin)

## 3. Access Control / IDOR
- [ ] Ganti ID objek (`id`, `uuid`, nomor urut) milik akun A dari akun B
- [ ] Coba akses endpoint admin/privileged sebagai user biasa
- [ ] Uji akses langsung ke URL/objek tanpa melalui alur normal

## 4. Input / Injection
- [ ] XSS: sisipkan penanda unik → cek apakah muncul mentah → uji payload
- [ ] SQLi: sisipkan `'` dan amati error/perubahan perilaku
- [ ] Uji injeksi lain yang relevan (command, template, dll) bila konteks cocok

## 5. Authentication & Session
- [ ] Rate limit pada login / reset password?
- [ ] Token reset password: acak & kedaluwarsa dengan benar?
- [ ] Session invalid setelah logout / ganti password?
- [ ] Alur 2FA bisa di-bypass?

## 6. Business Logic
- [ ] Bisakah langkah alur dilewati / diubah urutannya?
- [ ] Manipulasi harga / kuantitas / nilai negatif?
- [ ] Race condition pada aksi penting?

## 7. Konfigurasi & Kebocoran Info
- [ ] File sensitif terekspos (`/.git`, backup, config)?
- [ ] Directory listing aktif?
- [ ] Pesan error bocorkan detail sistem?
- [ ] API key / kredensial di JavaScript / response?
- [ ] Header keamanan (sebagai temuan pendukung, biasanya low)

## 8. Lain-lain
- [ ] SSRF pada fitur yang menerima URL
- [ ] CSRF pada aksi penting tanpa token
- [ ] Open redirect
- [ ] Upload file: tipe/konten tervalidasi?

## 9. Pelaporan
- [ ] Reproduksi ulang dari awal untuk pastikan langkah akurat
- [ ] Ambil PoC (request/screenshot/video), sensor data sensitif
- [ ] Tulis pakai `templates/laporan-bug.md`
- [ ] Pastikan tidak ada eksploitasi berlebihan / data user asli terdampak
