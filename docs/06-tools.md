# 6. Perkakas (Tools) & Fungsinya

Jangan terjebak "mengoleksi tools". Untuk pemula, **3–4 tools inti sudah cukup**. Pahami
cara kerjanya, bukan sekadar menjalankannya. Tools mempercepat, tapi **otak & metodologi** yang menemukan bug.

> Semua tools di bawah untuk pengujian **in-scope** yang diizinkan. Hormati rate limit program.

---

## Wajib (mulai dari sini)

| Tool | Fungsi |
|------|--------|
| **Browser + DevTools** (F12) | Lihat request/response, DOM, storage, network. Gratis, sudah ada. |
| **Burp Suite Community** | *Proxy* untuk menangkap & **mengubah** request. Alat utama web hacking. |
| **Editor teks / VS Code** | Menulis catatan, script, menganalisis JavaScript. |

### Fitur Burp yang penting dipelajari (Community edition):
- **Proxy / Intercept** — tangkap & ubah request sebelum dikirim.
- **Repeater** — kirim ulang satu request berkali-kali sambil diubah-ubah (inti testing manual).
- **Target / Sitemap** — peta aplikasi dari semua request yang lewat.
- **Decoder** — encode/decode base64, URL, dll.

## Recon (saat sudah paham dasar)

| Tool | Fungsi |
|------|--------|
| **subfinder / amass** | Enumerasi subdomain |
| **httpx** | Cek subdomain mana yang hidup |
| **ffuf / dirsearch** | Content discovery (cari direktori/file) |
| **nuclei** | Pemindaian berbasis template untuk isu umum |
| **waybackurls / gau** | Kumpulkan URL historis dari arsip |

## Lain-lain yang berguna

| Tool | Fungsi |
|------|--------|
| **curl** | Kirim request manual dari terminal (bagus untuk PoC di laporan) |
| **jq** | Olah output JSON (API testing) |
| **Python** | Tulis script otomasi kecil sendiri |

---

## Urutan menguasai tools

1. **DevTools** — pahami dulu request/response secara visual.
2. **Burp Suite** — khususnya **Proxy** + **Repeater**. Habiskan waktu di sini.
3. Baru pelajari tools recon (subfinder, ffuf, nuclei) saat mulai program nyata.

> ⚠️ **Jangan jalankan scanner otomatis berlebihan** ke target. Banyak program melarang
> scanner agresif karena membebani server. Baca aturan program soal automated tooling.

## Setup lab lokal (opsional, direkomendasikan)

Jalankan target latihan di komputermu sendiri (100% legal):

```bash
# OWASP Juice Shop via Docker
docker run --rm -p 3000:3000 bkimminich/juice-shop
# lalu buka http://localhost:3000
```

Dengan lab lokal, kamu bebas bereksperimen tanpa khawatir scope atau rate limit.
