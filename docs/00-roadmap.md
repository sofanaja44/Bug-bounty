# 🗺️ Roadmap Belajar Bug Bounty (8–12 Minggu)

Ini peta jalan realistis untuk pemula total. Jangan skip tahap. Setiap orang beda kecepatan —
yang penting **konsisten** dan **banyak latihan di lab legal**, bukan baca teori terus.

---

## Prinsip belajar

1. **Teori secukupnya, praktik sebanyak-banyaknya.** Baca 20%, latihan di lab 80%.
2. **Latihan hanya di lab legal** (PortSwigger Academy, Juice Shop, dsb) sampai kamu paham.
   Jangan pernah tes website yang tidak punya program.
3. **Tulis catatan** setiap belajar sesuatu (folder `notes/`). Menulis ulang = cara terbaik mengingat.
4. **Satu jenis bug dalam satu waktu.** Kuasai XSS dulu sampai paham, baru lanjut IDOR, dst.

---

## Minggu 1–2 — Fondasi

**Tujuan:** paham cara kerja web dan HTTP, sampai bisa membaca request/response.

- [ ] Baca [`01-dasar-dasar.md`](01-dasar-dasar.md)
- [ ] Paham: client vs server, request/response, method (GET/POST), status code, header, cookie, session
- [ ] Install browser + DevTools; belajar tab **Network**
- [ ] Belajar dasar 1 bahasa scripting (Python atau JavaScript) — cukup bisa baca & tulis sederhana
- [ ] (Opsional) dasar Linux command line

## Minggu 3–4 — Keamanan Web & Mindset

**Tujuan:** paham etika, scope, dan pola pikir "bagaimana sesuatu bisa disalahgunakan".

- [ ] Baca [`02-etika-dan-scope.md`](02-etika-dan-scope.md) — **wajib**
- [ ] Baca [`04-kerentanan-umum.md`](04-kerentanan-umum.md) sekilas (belum perlu hafal)
- [ ] Buat akun **PortSwigger Web Security Academy** (gratis) → mulai modul pertama
- [ ] Pasang **Burp Suite Community** (gratis) → belajar intercept request

## Minggu 5–8 — Latihan Kerentanan (inti!)

**Tujuan:** bisa menemukan & reproduksi bug di lab. Satu kelas bug per beberapa hari.

- [ ] XSS (Cross-Site Scripting) — lab PortSwigger
- [ ] Access Control / IDOR
- [ ] SQL Injection
- [ ] Authentication flaws
- [ ] SSRF
- [ ] CSRF
- [ ] Information disclosure & misconfiguration
- [ ] Selesaikan **OWASP Juice Shop** sebanyak mungkin

> 💡 Target realistis: setiap kali selesai 1 kelas bug, tulis ringkasan di `notes/` pakai kata-katamu sendiri.

## Minggu 9–12 — Program Nyata (pelan-pelan)

**Tujuan:** baca scope program nyata, lakukan recon, kirim laporan pertama.

- [ ] Daftar **HackerOne** dan/atau **Bugcrowd**
- [ ] Pilih **1 program publik** dengan scope luas & ramah pemula (lihat `*.domain` wildcard, ada safe harbor)
- [ ] Baca policy & scope sampai paham betul → catat di `notes/<nama-program>.md`
- [ ] Ikuti [`03-metodologi.md`](03-metodologi.md): recon → mapping → testing
- [ ] Temukan sesuatu → reproduksi → tulis pakai [`templates/laporan-bug.md`](../templates/laporan-bug.md) → submit
- [ ] Laporan ditolak? **Normal.** Baca feedback triager, perbaiki, lanjut.

---

## Setelah 3 bulan

- Spesialisasi: pilih area yang kamu suka (misal: web app, API, mobile, cloud).
- Ikuti writeup bug bounty (di HackerOne Hacktivity, blog peneliti) — belajar dari laporan nyata.
- Bangun otomasi recon sendiri untuk aset yang **sudah in-scope**.

> **Jangan patah semangat.** Bounty pertama sering butuh waktu berbulan-bulan. Yang bertahan adalah yang menang.
