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

---

## 🎯 Berikutnya

- [ ] Lanjut lab Broken Access Control berikutnya (naik tingkat)
- [ ] Mulai sentuh IDOR (horizontal access control)

> Prinsip: satu kelas bug dikuasai dulu sampai paham, baru lanjut. Konsisten > buru-buru.
