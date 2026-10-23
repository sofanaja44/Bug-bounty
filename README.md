# 🐛 Basecamp Belajar Bug Bounty

Repo ini adalah tempat belajar **bug bounty / pengujian keamanan web yang sah** dari nol.
Bug bounty = mencari celah keamanan di sistem yang **secara resmi mengizinkan** pengujian
(lewat sebuah *program*), dengan aturan jelas, dan bisa memberi **reputasi + hadiah uang (bounty)**.

> ⚠️ **Aturan paling penting:** hanya uji aset yang **in-scope** pada program yang **mengizinkan**.
> Mengetes website tanpa izin = ilegal, walau niatmu baik. Baca [`docs/02-etika-dan-scope.md`](docs/02-etika-dan-scope.md) dulu.

---

## 🗺️ Jalur Belajar (ikuti berurutan)

| Tahap | File | Isi |
|-------|------|-----|
| 0 | [`docs/00-roadmap.md`](docs/00-roadmap.md) | Peta belajar 8–12 minggu + cara pakai repo ini |
| 1 | [`docs/01-dasar-dasar.md`](docs/01-dasar-dasar.md) | Cara kerja web, HTTP, cookie, session — fondasi wajib |
| 2 | [`docs/02-etika-dan-scope.md`](docs/02-etika-dan-scope.md) | Legalitas, scope, safe harbor, do & don't |
| 3 | [`docs/03-metodologi.md`](docs/03-metodologi.md) | Alur kerja: recon → mapping → testing → report |
| 4 | [`docs/04-kerentanan-umum.md`](docs/04-kerentanan-umum.md) | Jenis bug populer (OWASP) + cara mengenalinya |
| 5 | [`docs/05-lab-dan-sumber-belajar.md`](docs/05-lab-dan-sumber-belajar.md) | Lab latihan legal & sumber belajar gratis |
| 6 | [`docs/06-tools.md`](docs/06-tools.md) | Perkakas umum & fungsinya |

## 📋 Alat bantu kerja

- [`templates/laporan-bug.md`](templates/laporan-bug.md) — template laporan yang rapi (pakai tiap submit)
- [`checklists/web-testing-checklist.md`](checklists/web-testing-checklist.md) — checklist saat menguji target
- [`notes/`](notes/) — catatan per target/program (jangan commit data sensitif!)

---

## 🚀 Mulai dari mana?

1. Baca [`docs/02-etika-dan-scope.md`](docs/02-etika-dan-scope.md) — **wajib, non-negosiasi**.
2. Ikuti [`docs/00-roadmap.md`](docs/00-roadmap.md).
3. Latihan di lab legal (PortSwigger Academy / Juice Shop) — **bukan** langsung ke website orang.
4. Setelah paham dasar, daftar program publik di HackerOne/Bugcrowd dan baca scope-nya.

Belajar pelan-pelan tapi konsisten jauh lebih baik daripada buru-buru. Semangat! 💪
