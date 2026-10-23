# 📒 Jurnal Belajar Bug Bounty

Catatan perjalanan belajar — apa yang sudah dipelajari & dikuasai.

---

## ✅ Fondasi (selesai)

- [x] Paham **request & response** (perumpamaan restoran: client memesan, server melayani)
- [x] Paham **client vs server**
- [x] Konsep kunci: **"bug lahir karena server terlalu percaya pada input dari client"**
- [x] Bisa **mengintip request** pakai DevTools (F12) → tab Network
- [x] Paham **anatomi request**: Method, URL+Parameter, Headers, Body/Payload
- [x] Bisa baca sedikit **hex** (huruf yang menyamar jadi kode)

## ✅ Lab yang sudah diselesaikan

### Lab #1 — Unprotected admin functionality (PortSwigger) ✅
- **Kelas bug:** Broken Access Control (OWASP #1)
- **Cara solve:** buka `/robots.txt` → bocor letak panel admin → akses langsung URL-nya
  (tidak terkunci!) → hapus user `carlos`
- **Pelajaran:** panel admin cuma *disembunyikan*, bukan *dikunci*. Server tidak pernah
  mengecek apakah pengunjung benar-benar admin.
- **Cara perbaikan yang benar:** server wajib cek hak akses (authorization) di sisi server
  pada setiap halaman/aksi sensitif; kalau bukan admin → tolak. Menyembunyikan link ≠ keamanan.

### Lab #2 — Unprotected admin functionality with unpredictable URL (PortSwigger) ✅
- **Kelas bug:** Broken Access Control + Information Disclosure
- **Cara solve:** URL panel admin diacak (tak bisa ditebak), TAPI bocor di dalam
  kode sumber halaman (JavaScript). Buka `Ctrl+U` → cari "admin" → ketemu alamat
  rahasianya → akses → hapus `carlos`.
- **Skill baru:** membaca **source code / JavaScript** halaman untuk cari rahasia yang bocor.
- **Pelajaran:** apa pun yang dikirim ke browser (HTML/JS) bisa dibaca siapa saja.
  Menyembunyikan alamat di JavaScript ≠ keamanan. Developer sering ceroboh meninggalkan
  endpoint rahasia, komentar, bahkan API key di kode client-side.

---

## 🎯 Berikutnya

- [ ] Lab #3: "User role controlled by request parameter" (mulai MENGUBAH request!)
- [ ] Lanjut ke Parameter-based access control
- [ ] Mulai sentuh IDOR (horizontal access control)

> Prinsip: satu kelas bug dikuasai dulu sampai paham, baru lanjut. Konsisten > buru-buru.
