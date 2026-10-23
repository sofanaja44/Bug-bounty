# 3. Metodologi: Alur Kerja dari Recon sampai Report

Hacker pemula langsung "tembak-tembak". Hacker yang menghasilkan bounty punya **proses**.
Proses ini membuat kamu sistematis, tidak melewatkan area, dan tetap di dalam scope.

```
1. Baca Scope  →  2. Recon  →  3. Mapping  →  4. Testing  →  5. Report
      ↑_______________________________________________________|
                 (ulang untuk aset berikutnya)
```

---

## Tahap 0 — Baca Scope (selalu pertama)

- Catat semua aset **in-scope** dan **out-of-scope** di `notes/<program>.md`.
- Catat aturan khusus (rate limit, akun uji yang disediakan, dll).
- **Jangan sentuh apa pun sebelum ini selesai.**

## Tahap 1 — Recon (pengintaian)

Mengumpulkan informasi tentang target **yang in-scope**. Makin banyak permukaan serangan
yang kamu temukan, makin besar peluang menemukan bug yang orang lain lewatkan.

Untuk scope `*.target.com` (wildcard), contoh yang dilakukan:

- **Subdomain enumeration**: cari subdomain (`api.`, `dev.`, `staging.`, dll).
- **Content discovery**: cari direktori/file tersembunyi (`/admin`, `/backup`, `/.git`).
- **Teknologi**: framework apa, server apa, versi apa (petunjuk kerentanan known).
- **Endpoint & parameter**: kumpulkan URL, parameter, endpoint API.

> ⚠️ Recon tetap harus **in-scope**. Subdomain yang kamu temukan pun harus dicek apakah masuk scope.
> Recon aktif (mengirim banyak request) harus hormati rate limit program.

## Tahap 2 — Mapping (pemetaan)

Pahami aplikasinya **sebagai pengguna normal** dulu:

- Daftar/login, pakai fitur-fiturnya, perhatikan alur.
- Catat: di mana ada input user? di mana ada data sensitif? di mana ada peran berbeda
  (user biasa vs admin)?
- Lewati semua request lewat Burp supaya tercatat di *sitemap*.

Dari sini kamu dapat **daftar target uji**: form, parameter, endpoint, fungsi.

## Tahap 3 — Testing (pengujian)

Untuk tiap titik input, uji kelas-kelas bug yang relevan (lihat [`04-kerentanan-umum.md`](04-kerentanan-umum.md)
dan [`checklists/web-testing-checklist.md`](../checklists/web-testing-checklist.md)).

Pola kerja:

1. Amati perilaku normal.
2. Kirim input tak terduga (payload) — satu per satu, kecil.
3. Amati respons: apa ada yang menyimpang? error? data bocor? perilaku berubah?
4. Kalau ada petunjuk, kejar sampai jadi bukti yang jelas (PoC).
5. **Berhenti di titik "cukup membuktikan"** — jangan eksploitasi berlebihan (lihat etika).

> 💡 Catat **semua** yang kamu lakukan sambil jalan. Saat menulis laporan, kamu butuh langkah persis.

## Tahap 4 — Report (laporan)

Laporan bagus = bounty cair cepat. Laporan buruk = ditolak walau bugnya nyata.

Pakai [`templates/laporan-bug.md`](../templates/laporan-bug.md). Yang wajib ada:

- **Judul** jelas: jenis bug + lokasi.
- **Dampak**: kenapa ini bahaya? (pencurian data? ambil alih akun?)
- **Langkah reproduksi**: nomor urut, sedetail mungkin, bisa diikuti orang lain.
- **Proof of Concept (PoC)**: request/payload/screenshot/video.
- **Saran perbaikan**: nilai tambah, menunjukkan kamu paham.

---

## Severity (tingkat keparahan)

Program menilai bug pakai skala (biasanya **CVSS**): `Low → Medium → High → Critical`.
Makin besar dampak + makin mudah dieksploitasi = makin tinggi = bounty makin besar.

| Contoh | Severity kira-kira |
|--------|--------------------|
| Ambil alih akun tanpa interaksi (account takeover) | Critical / High |
| Baca data user lain (IDOR data sensitif) | High / Medium |
| Stored XSS | High / Medium |
| Info disclosure minor | Low |
| Masalah "best practice" tanpa dampak nyata | Sering **informational** (tidak dibayar) |

> Jangan kecewa kalau temuan pertamamu "low". Itu tetap belajar & menambah reputasi.
