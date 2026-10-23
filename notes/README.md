# 📝 Catatan Belajar & Target

Folder untuk catatan pribadimu: ringkasan materi, catatan per program, progres latihan.

## Aturan penting

- **JANGAN commit data sensitif** ke repo publik: kredensial, token, session, data user asli,
  detail kerentanan yang belum diperbaiki, atau apa pun yang melanggar NDA/kebijakan program.
- Banyak program melarang membocorkan temuan sebelum diperbaiki & diizinkan. Simpan detail
  temuan aktif secara privat (lokal / repo privat), bukan di sini kalau repo ini publik.
- Gunakan file ini untuk hal yang aman dibagikan: ringkasan belajar, metodologi, progres.

## Saran struktur

- `catatan-xss.md`, `catatan-idor.md`, ... — ringkasan tiap kelas bug pakai kata-katamu
- `<nama-program>.md` — catatan scope & recon per program (tanpa detail sensitif)
- `progres.md` — jurnal belajar harian/mingguan

## Template catatan program

```markdown
# Program: <nama>

- Platform: HackerOne / Bugcrowd / ...
- Safe harbor: ya / tidak
- Tanggal baca scope: <tanggal>

## In-scope
- *.target.com
- ...

## Out-of-scope
- ...

## Aturan khusus
- Rate limit: ...
- Larangan: ...

## Recon / temuan (ringkas, tanpa data sensitif)
- ...
```
