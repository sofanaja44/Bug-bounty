# [Jenis Bug] di [Lokasi/Endpoint]

<!--
Template laporan bug. Salin file ini untuk tiap temuan.
Laporan jelas = bounty cepat cair. Isi semua bagian, hapus komentar <!-- --> ini.
-->

## Ringkasan
<!-- 1–2 kalimat: apa bugnya dan di mana. -->
Terdapat kerentanan **[jenis]** pada **[endpoint/fitur]** yang memungkinkan penyerang untuk [dampak singkat].

## Severity (perkiraan)
<!-- Low / Medium / High / Critical — dan kenapa. Program yang menentukan final. -->
**[Medium]** — karena [alasan: butuh interaksi? data sensitif? dll].

## Aset Terdampak
- URL/Endpoint: `https://target.com/...`
- Parameter: `...`
- (Konfirmasi aset ini **in-scope** di program.)

## Dampak
<!-- Kenapa ini berbahaya bagi bisnis/user? Konkret. -->
Penyerang dapat [mis. membaca data pribadi user lain / mengambil alih akun / dll],
yang berakibat [kebocoran data / kerugian / dll].

## Langkah Reproduksi
<!-- Nomor urut, sedetail mungkin, bisa diikuti triager tanpa menebak. -->
1. Login sebagai user A di `...`
2. Buka `...`
3. Ubah parameter `id=123` menjadi `id=124`
4. Amati bahwa [hasil yang membuktikan bug]

## Proof of Concept (PoC)
<!-- Bukti nyata: request mentah, payload, screenshot, atau video. -->

Contoh request:
```http
GET /invoice?id=124 HTTP/1.1
Host: target.com
Cookie: session=...
```

Respons menunjukkan: [data milik user lain / hasil XSS / dll]

<!-- Lampirkan screenshot/video bila membantu. Redaksi/sensor data sensitif nyata. -->

## Bukti Dampak (minimal & aman)
<!-- Tunjukkan cukup untuk membuktikan, TANPA merugikan user asli.
     Gunakan akun uji milikmu sendiri. Jangan dump data / curi sesuatu. -->

## Saran Perbaikan
<!-- Menunjukkan kamu paham & menambah nilai laporan. -->
- [mis. Terapkan pengecekan otorisasi di sisi server untuk memastikan user hanya bisa
  mengakses objek miliknya.]
- [mis. Lakukan output encoding pada data yang ditampilkan.]

## Referensi
- OWASP: [tautan halaman OWASP terkait jenis bug ini]
- CWE: [nomor CWE bila tahu]
