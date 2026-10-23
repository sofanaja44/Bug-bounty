# 1. Dasar-Dasar: Cara Kerja Web & HTTP

Sebelum cari celah, kamu harus paham **cara kerja normalnya** dulu. Bug = sesuatu yang
menyimpang dari cara kerja normal. Kalau tidak tahu normalnya, tidak akan lihat yang anehnya.

---

## 1.1 Client & Server

- **Client**: browser/aplikasi kamu. Mengirim **request**.
- **Server**: komputer milik website. Mengirim **response**.

Setiap kali kamu buka halaman, browser mengirim request ke server, server membalas dengan response (HTML, data, dll).

```
[Browser kamu] --- request ---> [Server website]
[Browser kamu] <-- response --- [Server website]
```

## 1.2 HTTP Request

Contoh request (bisa kamu lihat di DevTools → tab Network, atau di Burp Suite):

```http
GET /profil?id=123 HTTP/1.1
Host: contoh.com
User-Agent: Mozilla/5.0 ...
Cookie: session=abc123xyz
```

Bagian-bagiannya:

| Bagian | Penjelasan |
|--------|-----------|
| **Method** | Aksi yang diminta: `GET` (ambil data), `POST` (kirim data), `PUT`, `DELETE`, dll |
| **Path** | Alamat sumber daya: `/profil` |
| **Query string** | Parameter setelah `?`: `id=123` — **sering jadi titik rawan** |
| **Header** | Metadata: `Host`, `User-Agent`, `Cookie`, `Authorization`, dll |
| **Body** | Isi data (biasanya di `POST`/`PUT`) — misal form login |

## 1.3 HTTP Response

```http
HTTP/1.1 200 OK
Content-Type: text/html
Set-Cookie: session=abc123xyz

<html>...isi halaman...</html>
```

**Status code** penting dihafal garis besarnya:

| Kode | Arti | Contoh |
|------|------|--------|
| `2xx` | Sukses | `200 OK` |
| `3xx` | Pengalihan | `301`, `302` (redirect) |
| `4xx` | Kesalahan client | `401` (belum login), `403` (dilarang), `404` (tidak ada) |
| `5xx` | Kesalahan server | `500` (error di server — **kadang petunjuk adanya bug**) |

## 1.4 Cookie & Session

- **Cookie**: potongan data yang disimpan browser, dikirim otomatis tiap request ke situs itu.
- **Session**: cara server mengingat "kamu siapa" setelah login. Biasanya server kasih cookie
  `session=...` yang mewakili identitasmu.

👉 Banyak bug soal keamanan muncul di sini: misal apakah session bisa dicuri, apakah ganti
`id=123` jadi `id=124` membuat kamu melihat data orang lain (ini namanya **IDOR**).

## 1.5 Parameter = tempat input user

Di mana pun user bisa memasukkan data, di situ ada kemungkinan bug:

- Query string: `?search=sepatu`
- Body form: `username=...&password=...`
- Header: `Cookie`, `User-Agent`, `Referer`
- Path: `/user/123`
- JSON di API: `{"id": 123}`

**Pola pikir hacker:** "Apa yang terjadi kalau input ini saya ubah jadi hal yang tidak diharapkan server?"
Misalnya memasukkan `'` ke kolom pencarian, atau mengganti `id` orang lain.

## 1.6 Tools untuk melihat semua ini

- **Browser DevTools** (tekan `F12`) → tab **Network** untuk lihat request/response.
- **Burp Suite Community** (gratis) → *proxy* yang menangkap & memungkinkan kamu **mengubah** request sebelum dikirim. Ini alat utama hacker web.

---

## ✅ Cek pemahaman

Sebelum lanjut, pastikan kamu bisa jawab ini:

1. Apa beda GET dan POST?
2. Di mana saja user bisa memasukkan input ke aplikasi?
3. Apa fungsi cookie `session`?
4. Status code `500` menandakan apa, dan kenapa itu menarik bagi hacker?

Kalau masih bingung, ulangi bagian terkait. Fondasi yang kuat = belajar bug jadi mudah nanti.
