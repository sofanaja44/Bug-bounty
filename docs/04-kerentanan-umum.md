# 4. Kerentanan Umum (OWASP) + Cara Mengenalinya

Ini kelas-kelas bug paling sering ditemukan & dibayar. Untuk tiap bug: **apa itu**,
**kenapa bahaya**, **cara mengenali**, dan **cara buktikan dengan aman**.

> Latih semua ini di lab legal (PortSwigger Academy punya lab khusus tiap topik).
> Jangan latihan di website orang.

---

## 4.1 IDOR / Broken Access Control ⭐ (ramah pemula)

**Apa:** aplikasi tidak mengecek apakah kamu **berhak** mengakses suatu objek. Kamu ganti
ID milik orang lain → bisa lihat/ubah datanya.

**Contoh:** `GET /invoice?id=123` → ganti jadi `id=124` → muncul invoice user lain.

**Cara mengenali:** cari ID yang bisa ditebak (`id`, `user_id`, `uuid`, nomor urut) di URL,
body, atau API. Buat **2 akun** uji, coba akses objek akun A dari akun B.

**Buktikan dengan aman:** cukup tunjukkan akun B bisa melihat 1 field data akun A (keduanya
akunmu sendiri). Jangan akses data user asli.

**Kenapa bahaya:** kebocoran data, pengambilalihan, manipulasi data orang lain.

---

## 4.2 XSS — Cross-Site Scripting ⭐

**Apa:** kamu bisa menyuntikkan JavaScript yang jalan di browser **korban**.

**Jenis:**
- **Reflected**: payload di URL, langsung dipantulkan ke halaman.
- **Stored**: payload tersimpan (misal di komentar) dan jalan ke setiap pengunjung — paling berbahaya.
- **DOM-based**: terjadi di sisi JavaScript client.

**Cara mengenali:** masukkan string penanda unik ke input (misal `xss1234`), lihat apakah
muncul mentah di HTML tanpa di-*escape*. Lalu coba `"><img src=x onerror=alert(1)>`.

**Buktikan dengan aman:** `alert(document.domain)` sudah cukup. **Jangan** curi cookie user asli.

**Kenapa bahaya:** curi session, lakukan aksi atas nama korban, deface, phishing.

---

## 4.3 SQL Injection

**Apa:** input user ikut masuk ke query database tanpa disaring → kamu bisa mengubah query.

**Cara mengenali:** masukkan `'` ke parameter → kalau muncul error SQL atau perilaku berubah,
curiga. Uji lebih lanjut dengan payload boolean/time-based.

**Buktikan dengan aman:** cukup tunjukkan bisa mempengaruhi query (misal `' OR '1'='1`) atau
ambil versi database. **Jangan** dump seluruh data user.

**Kenapa bahaya:** bocornya seluruh database, bypass login, bahkan ambil alih server.

---

## 4.4 Authentication & Session flaws

**Apa:** kelemahan pada login, reset password, atau pengelolaan session.

**Contoh:** brute force tanpa rate limit, token reset password yang mudah ditebak, session
tidak invalid setelah logout, bypass 2FA.

**Cara mengenali:** telusuri alur login/registrasi/reset dengan teliti. Perhatikan token,
cara ekspirasi, dan apa yang terjadi saat kamu mengubah langkah.

**Kenapa bahaya:** pengambilalihan akun (account takeover) — severity tinggi.

---

## 4.5 SSRF — Server-Side Request Forgery

**Apa:** kamu membuat **server** mengirim request ke tujuan yang kamu tentukan (misal ke
jaringan internal mereka).

**Cara mengenali:** fitur yang menerima URL (ambil gambar dari URL, webhook, import dari link).
Coba arahkan ke server yang kamu kontrol & lihat apakah server target menghubunginya.

**Kenapa bahaya:** akses ke sistem internal, metadata cloud (bisa berujung ambil alih infrastruktur).

---

## 4.6 CSRF — Cross-Site Request Forgery

**Apa:** memaksa browser korban (yang sudah login) melakukan aksi tanpa sadar.

**Cara mengenali:** aksi penting (ubah email, transfer) yang **tidak** pakai token anti-CSRF
atau pengecekan yang kuat.

**Kenapa bahaya:** aksi berbahaya atas nama korban.

---

## 4.7 Security Misconfiguration & Information Disclosure

**Apa:** konfigurasi salah atau kebocoran info: `/.git` terbuka, direktori ter-listing,
panel admin default, pesan error bocor detail sistem, API key di JavaScript.

**Cara mengenali:** content discovery + perhatikan response & file yang seharusnya tidak publik.

**Kenapa bahaya:** bergantung konteks — bisa low (versi bocor) sampai critical (kredensial bocor).

---

## Prioritas belajar untuk pemula

1. **IDOR / Broken Access Control** — konsepnya paling mudah, sering ditemukan.
2. **XSS** — klasik, banyak lab bagus.
3. **Information disclosure / misconfiguration** — "low hanging fruit".
4. Baru lanjut ke SQLi, SSRF, auth flaws yang butuh lebih banyak dasar.

> Referensi lengkap & selalu update: **OWASP Top 10** dan **PortSwigger Web Security Academy**.
> Detail payload ada di dunia nyata sangat banyak — kuasai **konsep**-nya dulu, payload menyusul.
