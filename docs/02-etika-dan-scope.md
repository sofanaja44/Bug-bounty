# 2. Etika, Legalitas & Scope — WAJIB DIBACA

Ini bab paling penting di seluruh repo. Skill teknis tanpa paham bab ini = berbahaya buat
kamu sendiri. Perbedaan antara **bug bounty hunter** dan **kriminal** cuma satu: **izin**.

---

## 2.1 Apa yang membuat bug bounty itu LEGAL?

Legal **hanya kalau** pemilik sistem memberi izin lewat sebuah **program**. Program itu
berisi aturan tertulis tentang apa yang boleh dan tidak boleh kamu lakukan.

✅ **Boleh diuji:**
- Website/aplikasi/API yang terdaftar sebagai **in-scope** pada program yang aktif.
- Target lab latihan yang memang dibuat untuk dihack (Juice Shop, PortSwigger Academy, dll).
- Sistem milikmu sendiri.

❌ **TIDAK boleh (ilegal):**
- Website yang **tidak punya program** bug bounty / VDP — walau "cuma iseng" atau "mau bantu".
- Aset yang **out-of-scope** meski perusahaannya punya program.
- Melanggar aturan program (lihat bawah).

> **Ingat:** menemukan celah di situs tanpa izin lalu melaporkannya tetap bisa dituntut
> secara hukum di banyak negara. Niat baik **bukan** pembelaan hukum.

## 2.2 Scope — baca sampai hafal

Setiap program punya halaman **scope**. Contoh isinya:

```
IN SCOPE:
  *.target.com          (semua subdomain)
  api.target.com
  Aplikasi Android: com.target.app

OUT OF SCOPE:
  blog.target.com       (pakai WordPress pihak ketiga)
  staff.target.com      (internal)
  Social engineering ke karyawan
  Serangan DoS/DDoS
```

Aturan emas: **kalau ragu apakah sesuatu in-scope, anggap TIDAK, dan tanya program.**

## 2.3 Rules of Engagement (aturan main umum)

Hampir semua program melarang hal-hal ini — **jangan dilakukan**:

| Dilarang | Kenapa |
|----------|--------|
| **DoS / DDoS / stress test** | Mengganggu layanan, merugikan user asli |
| **Spam / brute force masif** | Membebani server, mengganggu operasi |
| **Mengakses/mengubah/menghapus data user lain** | Pelanggaran privasi; cukup buktikan *bisa*, jangan eksploitasi penuh |
| **Social engineering / phishing ke karyawan** | Di luar ranah teknis, merugikan orang |
| **Serangan fisik** | Jelas berbahaya & ilegal |
| **Melanjutkan eksploitasi setelah bukti cukup** | Cukup PoC minimal, jangan "pivot" lebih dalam |
| **Membocorkan bug ke publik sebelum diperbaiki** | Melanggar *responsible disclosure* |

## 2.4 Safe Harbor

Program yang baik punya pernyataan **Safe Harbor**: janji bahwa mereka **tidak akan menuntut**
peneliti yang mematuhi aturan dengan itikad baik. **Prioritaskan program yang punya safe harbor.**
Kalau tidak ada, risikonya lebih besar.

## 2.5 Responsible / Coordinated Disclosure

Alur yang benar setelah menemukan bug:

1. **Laporkan privat** ke program (lewat platform), **bukan** ke publik/Twitter.
2. Beri waktu mereka memperbaiki.
3. Jangan sebar detail sebelum diizinkan / sudah diperbaiki.
4. Jangan pernah **menuntut bayaran dengan ancaman** ("bayar atau saya bocorkan") — ini
   namanya **pemerasan (extortion)**, tindak pidana serius, bukan bug bounty.

## 2.6 Minimal impact principle

Saat membuktikan bug, lakukan **sesedikit mungkin** untuk membuktikannya:

- Butuh buktikan bisa baca data orang lain? Cukup ambil 1 data **milikmu sendiri lewat akun kedua**,
  atau tunjukkan 1 field, lalu berhenti. Jangan dump seluruh database.
- Butuh buktikan XSS? `alert(document.domain)` sudah cukup — jangan curi cookie user asli.

---

## ✅ Kontrak dengan diri sendiri

Sebelum menguji apa pun, tanya:

1. Apakah ada **program** resmi untuk target ini?
2. Apakah aset ini **in-scope**?
3. Apakah yang akan saya lakukan **dilarang** oleh rules?
4. Apakah saya bisa membuktikan bug **tanpa merugikan user asli**?

Kalau salah satu jawabannya meragukan → **berhenti**. Tidak ada bounty yang sepadan dengan masalah hukum.
