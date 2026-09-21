# Latihan Lomba MAPSI XXVII — PAI dan BTQ SD

Situs latihan soal statis untuk persiapan Lomba Mata Pelajaran PAI-BTQ tingkat SD, MAPSI XXVII Kabupaten Batang Tahun 2026. Berisi 5 paket, masing-masing 100 soal (94 pilihan ganda dan 6 menjodohkan), lengkap dengan petunjuk per soal dan pembahasan setelah dikumpulkan.

Materi soal mengikuti ruang lingkup Lampiran 1 Juknis: Al-Qur'an Hadis, Akidah, Akhlak, Fiqih, Sejarah Peradaban Islam, dan BTQ.

## Isi berkas

```
index.html          aplikasi (tampilan peserta + ruang admin)
data/paket1.js      bank soal paket 1
data/paket2.js      bank soal paket 2
data/paket3.js      bank soal paket 3
data/paket4.js      bank soal paket 4
data/paket5.js      bank soal paket 5
.nojekyll           agar GitHub Pages menayangkan berkas apa adanya
```

Tidak ada dependensi yang perlu dipasang. Seluruh CSS dan JavaScript menyatu di `index.html`.

## Deploy ke GitHub Pages

### Lewat web, tanpa Git
1. Buat repository baru, misalnya `mapsi-quiz`, pilih **Public**.
2. **Add file → Upload files**, seret seluruh isi folder ini termasuk folder `data`, lalu **Commit changes**.
3. Buka **Settings → Pages**. Source: **Deploy from a branch**, Branch: **main**, folder: **/ (root)**, lalu **Save**.
4. Tunggu satu sampai dua menit. Situs tayang di `https://<username>.github.io/mapsi-quiz/`.

### Lewat Git
```bash
git init
git add .
git commit -m "Latihan MAPSI XXVII"
git branch -M main
git remote add origin https://github.com/<username>/mapsi-quiz.git
git push -u origin main
```
Aktifkan Pages seperti langkah 3–4 di atas.

## Mengelola soal

Tombol **Kelola bank soal** ada di halaman depan. Kata sandi bawaan: `mapsi2026` (ganti lewat tombol di dalam).

Di dalam ruang admin, guru dapat mengubah soal, menambah soal pilihan ganda atau menjodohkan, menghapus soal, mengganti nama paket, serta memuat berkas paket dari komputer.

Alur menerbitkan soal baru ke situs:
1. Ubah atau tambah soal di ruang admin. Perubahan langsung tersimpan di browser yang sedang dipakai.
2. Klik **Unduh berkas paket ini**. Akan terunduh `paket1.js`, `paket2.js`, dan seterusnya.
3. Unggah berkas itu ke repositori untuk menimpa berkas lama di folder `data`.
4. GitHub Pages memperbarui situs beberapa saat kemudian, dan soal baru terlihat oleh semua peserta.

Tanpa langkah 2–4, perubahan hanya ada di browser guru dan tidak ikut tayang.

## Format soal

Pilihan ganda, satu baris satu soal:
```js
["pertanyaan", "A", "B", "C", "D", indeksKunci, "petunjuk", "pembahasan", "ruang lingkup"]
```
`indeksKunci` bernilai 0 untuk A, 1 untuk B, 2 untuk C, dan 3 untuk D.

Menjodohkan:
```js
{ "q":"perintah soal",
  "pasang":[["pernyataan","pasangan"], ...4 pasang],
  "h":"petunjuk", "e":"pembahasan", "s":"ruang lingkup" }
```
Pilihan pasangan diacak otomatis saat ditampilkan. Soal menjodohkan dihitung benar apabila keempat pasangan tepat, dan pasangan yang salah tetap ditandai satu per satu saat pembahasan.

## Catatan

- Nilai dan jawaban tersimpan di browser masing-masing peserta (`localStorage`), tidak terkirim ke server mana pun. Karena itu situs ini cocok untuk latihan mandiri, bukan untuk penilaian resmi yang hasilnya perlu direkap panitia.
- Kata sandi admin tersimpan di sisi browser dan dapat dibaca siapa pun yang membuka kode sumber halaman. Anggap sebagai pembatas kenyamanan, bukan pengaman.
- Repositori GitHub Pages gratis bersifat publik, sehingga seluruh soal dan kunci jawaban dapat dibaca umum. Bila soal perlu dirahasiakan sampai hari lomba, tunda pengunggahannya atau gunakan hosting tertutup.
