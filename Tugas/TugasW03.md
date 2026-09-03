# Tugas Kelompok — Metode Komputasi (PAGF262102)

**Materi: Percabangan (`if` / `elif` / `else`), operator logika, dan perulangan**
Pengganti kuliah tatap muka · S1 Geofisika UGM · 2026

---

## 1. Struktur Kelas

- 70 mahasiswa → **20 kelompok**. Kelompok 1–10 berisi 4 orang, Kelompok 11–20 berisi 3 orang
- **10 paket tugas**; Kelompok k dan Kelompok k+10 mengerjakan Tugas k
  (Kelompok 1 & 11 → Tugas 1, … , Kelompok 10 & 20 → Tugas 10)
- Kedua kelompok pemegang tugas sama menjadi **pasangan reviewer** (Bagian 5)
- Daftar anggota: **Lampiran A**. Data yang harus diolah: **Lampiran B** — berbeda untuk setiap kelompok

**Pembagian peran** (tulis di halaman depan laporan):

| Peran | Tanggung jawab |
|---|---|
| Ketua | Menulis Bagian A (logika `if`/`elif`/`else`) |
| Anggota 2 | Menulis Bagian B (perulangan dan rekap) |
| Anggota 3 | Menguji semua kasus uji dan mencatat hasilnya |
| Anggota 4 *(Kelompok 1–10)* | Memimpin cross-review + menjawab pertanyaan analisis |

Semua anggota tetap wajib memahami seluruh kode.

---

## 2. Yang Boleh Dipakai

Hanya yang sudah diajarkan:

- variabel, `input()`, `float()`, `int()`, `print()`
- operator pembanding: `>` `<` `>=` `<=` `==` `!=`
- operator logika: `and` `or` `not`
- percabangan: `if` / `elif` / `else`
- perulangan: `for` / `while`, serta list sederhana untuk menyimpan data

**Tidak boleh** memakai `numpy`, `pandas`, `match-case`, atau library apa pun. Program cukup satu berkas `.py`.

**Program harus jelas saat dijalankan.** Cetak nilai yang sedang diperiksa dan hasil keputusannya, misalnya:

```
Data ke-3: magnitudo 6.2  ->  Strong
```

Jika ada data yang tidak masuk akal (misal magnitudo negatif), program **tidak boleh diam saja** — cetak pesan yang jelas, contoh:
`"Data ke-7 DITOLAK: kedalaman tidak boleh negatif (-25)"`.

---

## 3. Bentuk Tugas

Setiap paket punya dua bagian.

**Bagian A — satu data (wajib).**
Program meminta satu masukan dari pengguna lewat `input()`, lalu mencetak keputusannya memakai `if` / `elif` / `else`.

**Bagian B — banyak data (perulangan).**
Salin **12 baris data kelompok Anda** dari Lampiran B ke dalam list di dalam program. Gunakan `for` untuk memproses seluruh data, mencetak keputusan tiap baris, lalu **merekap jumlah tiap kategori** di akhir. Contoh keluaran akhir:

```
=== REKAP ===
Small    : 3
Moderate : 4
Strong   : 5
Total    : 12
```

---

## 4. Yang Dikumpulkan

1. **Kode program** `.py` (satu berkas, boleh dua bagian dalam satu berkas)
2. **Tangkapan layar** hasil menjalankan program (Bagian A dan Bagian B)
3. **Tabel hasil Bagian B** di laporan: 12 baris data dan kategorinya, plus rekap
4. **Penelusuran tangan (tulis tangan, difoto) — satu per orang.** Setiap anggota memilih **baris data yang berbeda**, lalu menuliskan langkah demi langkah kondisi mana yang diperiksa, hasilnya True atau False, dan mengapa cabang tertentu yang dijalankan. Ini yang paling menentukan nilai individu.
5. **Screencast 3 menit**: jalankan program sambil menjelaskan. Semua anggota bicara.
6. **Jawaban pertanyaan analisis** (ada di tiap paket tugas)
7. **Catatan cross-review** (Bagian 5)

> Boleh memakai AI, tapi **wajib ditulis di laporan** bagian mana dan prompt-nya. Yang dinilai adalah pemahaman — diuji lewat penelusuran tangan, screencast, dan tanya jawab lisan singkat saat saya kembali. Kode yang benar tetapi tidak bisa dijelaskan bernilai kecil.

---

## 5. Cross-Review

Dua kelompok pemegang tugas sama bertukar kode sebelum deadline. Setiap kelompok menuliskan:

- **1 kesalahan atau kelemahan** pada kode pasangan (urutan kondisi salah, batas `>` vs `>=` keliru, ada kasus yang tidak tertangani, dll.)
- **1 saran perbaikan**

Yang menemukan kesalahan **mendapat nilai tambah**; yang ditemukan kesalahannya tidak dikurangi.

---

## 6. Penilaian

| Komponen | Bobot |
|---|---|
| Bagian A berjalan benar | 20 |
| Bagian B (perulangan + rekap) berjalan benar | 25 |
| Penelusuran tangan tiap anggota | 25 |
| Screencast + jawaban pertanyaan analisis | 20 |
| Cross-review | 10 |

---

# PAKET TUGAS

---

## Tugas 1 — Klasifikasi Magnitudo Gempa

**Bagian A.** Program meminta satu nilai magnitudo, lalu mencetak kategorinya.

| Syarat | Kategori |
|---|---|
| magnitudo ≥ 7.0 | Major |
| 6.0 ≤ magnitudo < 7.0 | Strong |
| 5.0 ≤ magnitudo < 6.0 | Moderate |
| magnitudo < 5.0 | Small |

**Bagian B.** Proses 12 data kelompok Anda, cetak kategori tiap baris, lalu rekap jumlah tiap kategori.

**Pertanyaan analisis.**
1. Jika urutan pemeriksaan dibalik (mulai dari `magnitudo >= 5.0`), apa yang terjadi pada gempa bermagnitudo 7.2? Coba jalankan dan jelaskan.
2. Apa bedanya hasil untuk magnitudo tepat 6.0 jika `>=` diganti `>`?

---

## Tugas 2 — Klasifikasi Kedalaman Gempa

**Bagian A.** Program meminta kedalaman (km), lalu mencetak kategorinya.

| Syarat | Kategori |
|---|---|
| kedalaman < 70 | Dangkal |
| 70 ≤ kedalaman ≤ 300 | Menengah |
| kedalaman > 300 | Dalam |

**Bagian B.** Proses 12 data kelompok Anda dan rekap jumlah tiap kategori.

**Pertanyaan analisis.**
1. Tuliskan kondisi untuk kategori Menengah dengan dua cara: memakai `and`, dan memakai perbandingan berantai (`70 <= d <= 300`). Buktikan keduanya memberi hasil sama.
2. Kedalaman tepat 300 km masuk kategori mana menurut aturan di atas? Tunjukkan baris kode yang menentukannya.

---

## Tugas 3 — Logika Peringatan Tsunami

**Bagian A.** Program meminta magnitudo dan kedalaman, lalu mencetak status.

| Syarat | Status |
|---|---|
| magnitudo ≥ 7.0 **dan** kedalaman < 70 | SIAGA TSUNAMI |
| magnitudo ≥ 6.5 **dan** kedalaman < 100 (dan bukan kasus di atas) | WASPADA |
| selain itu | AMAN |

**Bagian B.** Proses 12 data kelompok Anda, cetak status tiap baris, lalu rekap.

**Pertanyaan analisis.**
1. Seorang mahasiswa menulis `if magnitudo >= 7.0 or kedalaman < 70:`. Berikan satu contoh gempa yang salah diberi status SIAGA oleh kode itu, dan jelaskan mengapa.
2. Mengapa urutan pemeriksaan SIAGA harus diletakkan sebelum WASPADA?

---

## Tugas 4 — Pemeriksaan Kewajaran Data (Quality Control)

Data hasil rekaman kadang rusak. Program Anda menyaringnya sebelum dipakai.

**Bagian A.** Program meminta magnitudo dan kedalaman, lalu memutuskan:

| Syarat | Keputusan |
|---|---|
| magnitudo < 0 **atau** magnitudo > 10 **atau** kedalaman < 0 | TOLAK |
| selain itu | TERIMA |

Saat menolak, cetak **alasan spesifiknya**, misal: `DITOLAK: magnitudo 12.4 di luar rentang 0–10`.

**Bagian B.** Proses 12 data kelompok Anda (beberapa memang sengaja rusak). Cetak keputusan dan alasannya, lalu rekap jumlah TERIMA dan TOLAK.

**Pertanyaan analisis.**
1. Mengapa di sini dipakai `or`, bukan `and`? Apa yang terjadi jika ditukar?
2. Tuliskan kondisi TERIMA sebagai kebalikan kondisi TOLAK memakai `not`. Buktikan hasilnya sama untuk seluruh 12 data.

---

## Tugas 5 — Status Baterai Stasiun Seismik

**Bagian A.** Program meminta kode stasiun dan tegangan baterai (Volt), lalu mencetak status.

| Syarat | Status |
|---|---|
| tegangan ≥ 12.4 | NORMAL |
| 11.8 ≤ tegangan < 12.4 | WASPADA |
| tegangan < 11.8 | KRITIS |

**Bagian B.** Proses 12 stasiun milik kelompok Anda. Cetak status tiap stasiun, rekap jumlah tiap status, dan **cetak daftar kode stasiun yang berstatus KRITIS** (yang perlu dikunjungi teknisi lebih dulu).

**Pertanyaan analisis.**
1. Bagaimana cara program Anda mengumpulkan daftar stasiun KRITIS di dalam perulangan? Jelaskan barisnya.
2. Jika ambang WASPADA dinaikkan dari 11.8 menjadi 12.0, berapa stasiun yang berpindah status pada data Anda? Jalankan dan laporkan.

---

## Tugas 6 — Tingkat Guncangan dari PGA

PGA (percepatan tanah puncak) dipakai untuk memperkirakan seberapa kuat guncangan dirasakan.

**Bagian A.** Program meminta nilai PGA (dalam %g), lalu mencetak tingkatnya.

| Syarat | Tingkat |
|---|---|
| PGA ≥ 100 | VIII+ (Berat) |
| 40 ≤ PGA < 100 | VII (Kuat) |
| 10 ≤ PGA < 40 | V–VI (Sedang) |
| 2 ≤ PGA < 10 | III–IV (Ringan) |
| PGA < 2 | I–II (Tidak terasa) |

**Bagian B.** Proses 12 data kelompok Anda dan rekap jumlah tiap tingkat.

**Pertanyaan analisis.**
1. Ada lima kategori tetapi cukup empat kondisi yang dituliskan. Mengapa? Bagian mana yang menangani kategori kelima?
2. Apa yang terjadi jika urutan `elif` diacak? Tunjukkan satu contoh nilai PGA yang jadi salah kategori.

---

## Tugas 7 — Identifikasi Litologi dari Kecepatan Gelombang P

**Bagian A.** Program meminta nilai Vp (m/s), lalu menebak jenis batuannya.

| Syarat | Perkiraan litologi |
|---|---|
| Vp < 2000 | Sedimen lepas |
| 2000 ≤ Vp < 3500 | Batupasir |
| 3500 ≤ Vp < 5500 | Batugamping |
| Vp ≥ 5500 | Batuan beku |

**Bagian B.** Proses 12 data kelompok Anda, cetak litologi tiap baris, lalu rekap.

**Pertanyaan analisis.**
1. Tambahkan pemeriksaan agar Vp ≤ 0 ditolak dengan pesan yang jelas. Tunjukkan kodenya dan hasil ujinya.
2. Nilai Vp tepat 3500 masuk kategori mana? Ubah satu tanda pembanding sehingga masuk kategori sebelahnya, lalu jelaskan tanda mana yang Anda ubah.

---

## Tugas 8 — Apakah Gempa Terasa di Suatu Kota?

Gempa terasa bila cukup besar **dan** cukup dekat.

**Bagian A.** Program meminta magnitudo dan jarak episenter (km), lalu memutuskan:

| Syarat | Keputusan |
|---|---|
| (magnitudo ≥ 5.0 **dan** jarak ≤ 150) **atau** (magnitudo ≥ 6.5 **dan** jarak ≤ 300) | TERASA |
| selain itu | TIDAK TERASA |

**Bagian B.** Proses 12 data kelompok Anda, cetak keputusan tiap baris, lalu rekap.

**Pertanyaan analisis.**
1. Mengapa tanda kurung pada kondisi gabungan itu penting? Berikan satu contoh data yang hasilnya berubah kalau kurungnya dihapus.
2. Cari satu baris data Anda yang TERASA hanya karena syarat kedua (bukan yang pertama). Tunjukkan barisnya dan jelaskan.

---

## Tugas 9 — Penandaan Anomali Gravitasi

**Bagian A.** Program meminta nilai anomali gravitasi (mGal), lalu mencetak penandaannya.

| Syarat | Penandaan |
|---|---|
| anomali > 25 | POSITIF |
| anomali < −15 | NEGATIF |
| −15 ≤ anomali ≤ 25 | NORMAL |

**Bagian B.** Proses 12 data kelompok Anda. Cetak penandaan tiap baris, rekap jumlahnya, dan cetak **nilai terbesar serta nilai terkecil** dari seluruh data — dicari di dalam perulangan, bukan dengan `max()` atau `min()`.

**Pertanyaan analisis.**
1. Jelaskan cara program Anda mencari nilai terbesar di dalam perulangan. Nilai awal pembandingnya Anda isi berapa, dan mengapa pilihan itu aman?
2. Apa yang terjadi jika nilai awal pembanding diisi 0? Uji pada data Anda dan laporkan.

---

## Tugas 10 — Kelayakan Akuisisi Data Lapangan

Akuisisi hanya dijalankan bila cuaca dan peralatan mendukung.

**Bagian A.** Program meminta tiga masukan: apakah hujan (`ya`/`tidak`), kecepatan angin (km/jam), dan apakah alat siap (`ya`/`tidak`).

| Syarat | Keputusan |
|---|---|
| tidak hujan **dan** angin < 25 **dan** alat siap | AKUISISI |
| selain itu | TUNDA |

Saat menunda, cetak **semua alasan yang berlaku**, misalnya: `TUNDA: sedang hujan; angin 31 km/jam terlalu kencang`.

**Bagian B.** Proses 12 baris jadwal kelompok Anda, cetak keputusan dan alasannya, lalu rekap jumlah AKUISISI dan TUNDA.

**Pertanyaan analisis.**
1. Tuliskan kondisi TUNDA memakai `not` terhadap kondisi AKUISISI. Buktikan hasilnya sama untuk 12 data Anda.
2. Bagaimana cara mencetak **beberapa** alasan sekaligus, padahal `elif` hanya menjalankan satu cabang? Jelaskan pendekatan yang Anda pakai.

---

## Lampiran A — Contoh Kerangka Program

```python
# ---------- BAGIAN A: satu data ----------
print("=== BAGIAN A ===")
magnitudo = float(input("Masukkan magnitudo: "))

if magnitudo >= 7.0:
    kategori = "Major"
elif magnitudo >= 6.0:
    kategori = "Strong"
else:
    kategori = "Small"          # lengkapi sendiri sesuai tabel

print("Magnitudo", magnitudo, "->", kategori)

# ---------- BAGIAN B: banyak data ----------
print()
print("=== BAGIAN B ===")

data = [5.2, 6.8, 4.1]          # ganti dengan 12 data kelompok Anda

jumlah_major = 0
jumlah_strong = 0
jumlah_small = 0

nomor = 0
for nilai in data:
    nomor = nomor + 1

    if nilai >= 7.0:
        kategori = "Major"
        jumlah_major = jumlah_major + 1
    elif nilai >= 6.0:
        kategori = "Strong"
        jumlah_strong = jumlah_strong + 1
    else:
        kategori = "Small"
        jumlah_small = jumlah_small + 1

    print("Data ke-", nomor, ": magnitudo", nilai, "->", kategori)

print()
print("=== REKAP ===")
print("Major  :", jumlah_major)
print("Strong :", jumlah_strong)
print("Small  :", jumlah_small)
print("Total  :", nomor)
```

Kerangka ini contoh untuk Tugas 1. Sesuaikan dengan tabel aturan paket tugas Anda.

---

## Lampiran B — Contoh Penelusuran Tangan

Contoh untuk data magnitudo 6.4 pada Tugas 1. Setiap anggota membuat tabel seperti ini untuk **satu baris data yang berbeda**, ditulis tangan:

| Langkah | Kondisi yang diperiksa | Hasil | Tindakan |
|---|---|---|---|
| 1 | `6.4 >= 7.0` | False | lanjut ke `elif` |
| 2 | `6.4 >= 6.0` | True | jalankan blok ini, sisanya dilewati |
| 3 | — | — | cetak "Strong", `jumlah_strong` menjadi 1 |

Tuliskan juga satu kalimat: mengapa baris `else` tidak pernah dijalankan untuk data ini.

---

## Lampiran D — Pembagian Kelompok

Pengacakan seed 20260904; seluruh 70 peserta aktif terdistribusi tepat satu kali.

### Kelompok 1 — Tugas 1 · seed data = **720**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/563752/PA/23720 | Gilang Pranata |
| 2 | 25/556169/PA/23346 | Maida Kirana Vania Raya |
| 3 | 25/568385/PA/23993 | Latifah Permata Sari |
| 4 | 25/559820/PA/23568 | Dimas Zakiy Fadhillah |

### Kelompok 2 — Tugas 2 · seed data = **335**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/556063/PA/23335 | Theophilus Khrisna Aji Baskoro |
| 2 | 25/559555/PA/23541 | Aditya Eka Pramana |
| 3 | 25/559543/PA/23539 | Khafif Muntaqo |
| 4 | 25/563651/PA/23713 | Sabda Bima Firmayo |

### Kelompok 3 — Tugas 3 · seed data = **296**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/555624/PA/23296 | Luna Maharani Santoso |
| 2 | 25/563619/PA/23711 | Bragi Yusuf Laceza |
| 3 | 25/555895/PA/23320 | Ganendra Perwira Ahsan |
| 4 | 25/560362/PA/23613 | Aleron Ahmad |

### Kelompok 4 — Tugas 4 · seed data = **562**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/559779/PA/23562 | Laura Abigail Hutagaol |
| 2 | 25/556397/PA/23363 | Kezia Celine Putri Marbun |
| 3 | 25/559710/PA/23557 | Naura Putri Mazri |
| 4 | 25/564059/PA/23738 | Fachri Anugrah Pratama |

### Kelompok 5 — Tugas 5 · seed data = **457**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/558098/PA/23457 | Reffi Callista Hindargo |
| 2 | 25/566089/PA/23887 | FALAH NABHAN YUARI |
| 3 | 25/561581/PA/23675 | Bisyarah Aulia Izzati |
| 4 | 25/557065/PA/23397 | Mhd.Haqqi Cendikia |

### Kelompok 6 — Tugas 6 · seed data = **980**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/568050/PA/23980 | Davina Putri Sabila |
| 2 | 25/564390/PA/23765 | IVANA PUTRI SALSABILA |
| 3 | 25/559366/PA/23525 | Aldila Salwa Savaira |
| 4 | 25/566317/PA/23900 | ERLINDA MAGDALENA |

### Kelompok 7 — Tugas 7 · seed data = **892**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/566130/PA/23892 | Adilla Dewi Agustin |
| 2 | 25/568111/PA/23982 | MUHAMMAD HAIDAR AL MUJAHID |
| 3 | 25/563609/PA/23708 | WIKA AMIRUL AKBAR |
| 4 | 25/561893/PA/23692 | Raisa Alfi Kusuma |

### Kelompok 8 — Tugas 8 · seed data = **547**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/559642/PA/23547 | Raziq Nayanda |
| 2 | 25/562097/PA/23700 | Asyifa Chaerinisa |
| 3 | 25/555412/PA/23282 | Almira Ryke Mahara |
| 4 | 25/561532/PA/23673 | Krisna Fathan Kalimasada |

### Kelompok 9 — Tugas 9 · seed data = **826**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/565092/PA/23826 | Farras Althaf Ali Mohamad |
| 2 | 25/557447/PA/23417 | Syafiq Khairi Zakiy |
| 3 | 25/556798/PA/23382 | Hanifa Priti Norita |
| 4 | 25/555356/PA/23278 | Nur Faizah Rahmadini |

### Kelompok 10 — Tugas 10 · seed data = **839**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/565277/PA/23839 | Khansya Maesayu Mutiandra |
| 2 | 25/559665/PA/23552 | Viola Beby Harso |
| 3 | 25/556910/PA/23386 | Icha Shylvana Mustofa Putri |
| 4 | 25/564062/PA/23739 | Puji Lestari |

### Kelompok 11 — Tugas 1 · seed data = **946**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/567332/PA/23946 | PANDYA DHAIRYA ATYANTA DIANASTYA |
| 2 | 25/558151/PA/23465 | Muhammad Azfa Hidayat |
| 3 | 25/565478/PA/23851 | Uswatun Hasanah |

### Kelompok 12 — Tugas 2 · seed data = **302**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/555671/PA/23302 | Dhia Weningtyas |
| 2 | 25/566623/PA/23918 | Muhammad Akbar Zulkarnain |
| 3 | 25/565504/PA/23852 | MUHAMMAD FAIRUZ SAFRI RIDHO |

### Kelompok 13 — Tugas 3 · seed data = **289**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/555559/PA/23289 | Muhammad Fahri Rahim Furkan |
| 2 | 25/568068/PA/23981 | ADITYA WISNU WARDANA |
| 3 | 25/561068/PA/23654 | Jonathan Marchell Herrnawan |

### Kelompok 14 — Tugas 4 · seed data = **409**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/557225/PA/23409 | Naura Najwa Salsabila Ramadhani |
| 2 | 25/566019/PA/23885 | MUHAMMAD SURYA ALAM |
| 3 | 25/561061/PA/23652 | Vina Mahmudah Ashidqi |

### Kelompok 15 — Tugas 5 · seed data = **587**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/560090/PA/23587 | Mattew Jilldanio Anthony |
| 2 | 25/564227/PA/23750 | Muhammad Athallah Ramadhan |
| 3 | 25/559569/PA/23542 | Anatasya Gabriella Talakua |

### Kelompok 16 — Tugas 6 · seed data = **714**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/563656/PA/23714 | Yumna Eka Salsabila |
| 2 | 25/557578/PA/23427 | Alifa Idzfa Adha |
| 3 | 25/564718/PA/23800 | Fahad Raya Fakhry Az-Zahary |

### Kelompok 17 — Tugas 7 · seed data = **949**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/567376/PA/23949 | AILSA RAHMA CLORINDA |
| 2 | 25/555318/PA/23273 | Indy Isma Wardani |
| 3 | 25/556091/PA/23339 | Gabriella Kirana Stefhania |

### Kelompok 18 — Tugas 8 · seed data = **951**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/567405/PA/23951 | Nasyadilla Priska Eka Putranti |
| 2 | 25/564535/PA/23778 | Auliya Citra Ayu Wardani |
| 3 | 25/567978/PA/23975 | Syifa Salsabila |

### Kelompok 19 — Tugas 9 · seed data = **598**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/560189/PA/23598 | Danty Risma Putri |
| 2 | 25/567608/PA/23956 | Wildan Fajrul Falah |
| 3 | 25/561209/PA/23657 | Sulthan Rafi Sukata |

### Kelompok 20 — Tugas 10 · seed data = **784**

| | NIM | Nama |
|---|---|---|
| **Ketua** | 25/564592/PA/23784 | Ilyasa Ihsan Yeni |
| 2 | 25/559657/PA/23550 | Oscar Fernanda Darius Patuan Siahaan |
| 3 | 25/557392/PA/23415 | Muhammad Fatih Sadidan Riyawan |

---

## Lampiran E — Data untuk Bagian B

Salin **hanya data kelompok Anda** ke dalam program. Data tiap kelompok berbeda, jadi rekap akhirnya juga berbeda.

### Data Kelompok 1 — Tugas 1

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 7.0 | 383 | 171 |
| 2 | 7.6 | 533 | 205 |
| 3 | 6.2 | 173 | 368 |
| 4 | 5.8 | 3 | 206 |
| 5 | 5.3 | 481 | 166 |
| 6 | 7.6 | 94 | 262 |
| 7 | 5.3 | 540 | 183 |
| 8 | 6.4 | 468 | 159 |
| 9 | 6.3 | 17 | 152 |
| 10 | 5.4 | 186 | 335 |
| 11 | 7.5 | 564 | 229 |
| 12 | 7.4 | 5 | 122 |


### Data Kelompok 2 — Tugas 2

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 4.9 | 407 | 446 |
| 2 | 5.5 | 136 | 309 |
| 3 | 7.0 | 51 | 274 |
| 4 | 5.6 | 106 | 221 |
| 5 | 4.7 | 23 | 142 |
| 6 | 4.9 | 64 | 366 |
| 7 | 5.4 | 587 | 422 |
| 8 | 3.5 | 280 | 352 |
| 9 | 3.3 | 584 | 89 |
| 10 | 6.9 | 416 | 21 |
| 11 | 3.6 | 38 | 471 |
| 12 | 6.4 | 19 | 459 |


### Data Kelompok 3 — Tugas 3

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 4.4 | 386 | 449 |
| 2 | 3.5 | 146 | 474 |
| 3 | 5.2 | 223 | 421 |
| 4 | 4.2 | 549 | 145 |
| 5 | 7.5 | 443 | 415 |
| 6 | 6.5 | 344 | 392 |
| 7 | 6.3 | 209 | 429 |
| 8 | 6.8 | 22 | 448 |
| 9 | 4.6 | 133 | 46 |
| 10 | 3.3 | 41 | 161 |
| 11 | 3.6 | 284 | 135 |
| 12 | 4.8 | 597 | 72 |


### Data Kelompok 4 — Tugas 4

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 3.0 | 198 | 129 |
| 2 | 5.2 | 534 | 463 |
| 3 | 5.3 | 504 | 172 |
| 4 | 11.6 | 236 | 117 |
| 5 | 5.6 | 343 | 460 |
| 6 | 5.4 | 41 | 156 |
| 7 | 7.3 | 348 | 27 |
| 8 | 3.0 | -32 | 230 |
| 9 | 3.1 | 568 | 390 |
| 10 | -1.2 | 51 | 19 |
| 11 | 4.2 | 237 | 401 |
| 12 | 6.1 | 27 | 351 |


### Data Kelompok 5 — Tugas 5

| No | Kode stasiun | Tegangan baterai (V) |
|---|---|---|
| 1 | ST20 | 11.87 |
| 2 | ST20 | 11.7 |
| 3 | ST66 | 11.94 |
| 4 | ST89 | 12.76 |
| 5 | ST74 | 12.4 |
| 6 | ST86 | 13.17 |
| 7 | ST44 | 12.5 |
| 8 | ST77 | 12.94 |
| 9 | ST73 | 13.11 |
| 10 | ST89 | 11.46 |
| 11 | ST62 | 13.19 |
| 12 | ST28 | 12.67 |


### Data Kelompok 6 — Tugas 6

| No | PGA (%g) |
|---|---|
| 1 | 23.8 |
| 2 | 16.4 |
| 3 | 130.7 |
| 4 | 10.2 |
| 5 | 43.7 |
| 6 | 38.3 |
| 7 | 105.2 |
| 8 | 37.4 |
| 9 | 2.5 |
| 10 | 53.2 |
| 11 | 63.7 |
| 12 | 16.3 |


### Data Kelompok 7 — Tugas 7

| No | Vp (m/s) |
|---|---|
| 1 | 2709 |
| 2 | 4320 |
| 3 | 3137 |
| 4 | 2659 |
| 5 | 3982 |
| 6 | 1078 |
| 7 | 4961 |
| 8 | 3739 |
| 9 | 3451 |
| 10 | 1864 |
| 11 | 6372 |
| 12 | 3071 |


### Data Kelompok 8 — Tugas 8

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 5.8 | 600 | 283 |
| 2 | 4.6 | 63 | 110 |
| 3 | 6.1 | 3 | 449 |
| 4 | 5.2 | 84 | 293 |
| 5 | 3.6 | 593 | 96 |
| 6 | 4.9 | 457 | 229 |
| 7 | 5.2 | 217 | 24 |
| 8 | 7.4 | 436 | 344 |
| 9 | 3.1 | 264 | 17 |
| 10 | 7.5 | 214 | 128 |
| 11 | 7.4 | 4 | 173 |
| 12 | 6.5 | 17 | 137 |


### Data Kelompok 9 — Tugas 9

| No | Anomali gravitasi (mGal) |
|---|---|
| 1 | -32.5 |
| 2 | 14.0 |
| 3 | 2.5 |
| 4 | 40.8 |
| 5 | 17.9 |
| 6 | -25.7 |
| 7 | 36.6 |
| 8 | -34.7 |
| 9 | 52.1 |
| 10 | 11.4 |
| 11 | 16.1 |
| 12 | -20.1 |


### Data Kelompok 10 — Tugas 10

| No | Hujan | Angin (km/jam) | Alat siap |
|---|---|---|---|
| 1 | tidak | 8 | ya |
| 2 | tidak | 32 | tidak |
| 3 | ya | 34 | tidak |
| 4 | tidak | 23 | tidak |
| 5 | tidak | 16 | ya |
| 6 | tidak | 23 | ya |
| 7 | ya | 23 | tidak |
| 8 | tidak | 35 | tidak |
| 9 | tidak | 32 | ya |
| 10 | ya | 26 | tidak |
| 11 | ya | 10 | tidak |
| 12 | ya | 32 | ya |


### Data Kelompok 11 — Tugas 1

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 7.4 | 543 | 170 |
| 2 | 7.0 | 17 | 40 |
| 3 | 7.6 | 59 | 391 |
| 4 | 4.8 | 13 | 370 |
| 5 | 7.5 | 477 | 126 |
| 6 | 3.4 | 352 | 17 |
| 7 | 5.1 | 27 | 148 |
| 8 | 3.9 | 488 | 70 |
| 9 | 4.1 | 196 | 248 |
| 10 | 4.6 | 44 | 278 |
| 11 | 6.2 | 279 | 87 |
| 12 | 6.6 | 342 | 384 |


### Data Kelompok 12 — Tugas 2

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 5.1 | 469 | 120 |
| 2 | 4.3 | 220 | 469 |
| 3 | 6.9 | 381 | 214 |
| 4 | 3.4 | 19 | 244 |
| 5 | 6.4 | 338 | 99 |
| 6 | 6.2 | 21 | 393 |
| 7 | 4.8 | 566 | 96 |
| 8 | 5.7 | 195 | 359 |
| 9 | 4.4 | 288 | 437 |
| 10 | 7.5 | 191 | 338 |
| 11 | 5.1 | 65 | 460 |
| 12 | 5.0 | 572 | 417 |


### Data Kelompok 13 — Tugas 3

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 5.2 | 449 | 406 |
| 2 | 5.0 | 135 | 213 |
| 3 | 3.2 | 353 | 288 |
| 4 | 4.0 | 38 | 293 |
| 5 | 3.1 | 3 | 340 |
| 6 | 4.0 | 30 | 381 |
| 7 | 7.0 | 31 | 33 |
| 8 | 3.3 | 41 | 112 |
| 9 | 5.7 | 46 | 199 |
| 10 | 3.8 | 580 | 90 |
| 11 | 6.3 | 11 | 347 |
| 12 | 6.6 | 393 | 86 |


### Data Kelompok 14 — Tugas 4

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 4.1 | 25 | 306 |
| 2 | 6.8 | 597 | 405 |
| 3 | 6.0 | 533 | 380 |
| 4 | 11.5 | 488 | 438 |
| 5 | 3.1 | 78 | 210 |
| 6 | 6.1 | 187 | 26 |
| 7 | 6.6 | 395 | 247 |
| 8 | 3.3 | -19 | 122 |
| 9 | 4.0 | 46 | 266 |
| 10 | -1.6 | 100 | 109 |
| 11 | 4.9 | 57 | 316 |
| 12 | 6.4 | 428 | 22 |


### Data Kelompok 15 — Tugas 5

| No | Kode stasiun | Tegangan baterai (V) |
|---|---|---|
| 1 | ST37 | 12.94 |
| 2 | ST75 | 11.84 |
| 3 | ST92 | 11.33 |
| 4 | ST30 | 11.8 |
| 5 | ST46 | 11.64 |
| 6 | ST96 | 12.67 |
| 7 | ST84 | 11.84 |
| 8 | ST99 | 12.5 |
| 9 | ST33 | 11.22 |
| 10 | ST70 | 11.38 |
| 11 | ST50 | 12.41 |
| 12 | ST27 | 12.9 |


### Data Kelompok 16 — Tugas 6

| No | PGA (%g) |
|---|---|
| 1 | 18.6 |
| 2 | 25.1 |
| 3 | 12.6 |
| 4 | 125.6 |
| 5 | 38.5 |
| 6 | 132.9 |
| 7 | 3.0 |
| 8 | 2.0 |
| 9 | 17.0 |
| 10 | 1.5 |
| 11 | 152.1 |
| 12 | 22.0 |


### Data Kelompok 17 — Tugas 7

| No | Vp (m/s) |
|---|---|
| 1 | 2536 |
| 2 | 5961 |
| 3 | 5416 |
| 4 | 4070 |
| 5 | 5293 |
| 6 | 1200 |
| 7 | 5303 |
| 8 | 2118 |
| 9 | 5749 |
| 10 | 5506 |
| 11 | 5989 |
| 12 | 3677 |


### Data Kelompok 18 — Tugas 8

| No | Magnitudo | Kedalaman (km) | Jarak (km) |
|---|---|---|---|
| 1 | 6.9 | 544 | 217 |
| 2 | 4.9 | 515 | 240 |
| 3 | 5.2 | 271 | 435 |
| 4 | 6.1 | 200 | 433 |
| 5 | 3.2 | 19 | 167 |
| 6 | 5.1 | 54 | 288 |
| 7 | 3.6 | 5 | 286 |
| 8 | 5.4 | 178 | 470 |
| 9 | 4.1 | 599 | 62 |
| 10 | 4.2 | 368 | 242 |
| 11 | 6.9 | 492 | 121 |
| 12 | 7.2 | 148 | 269 |


### Data Kelompok 19 — Tugas 9

| No | Anomali gravitasi (mGal) |
|---|---|
| 1 | 24.4 |
| 2 | -21.8 |
| 3 | -15.2 |
| 4 | 8.7 |
| 5 | 55.4 |
| 6 | -36.5 |
| 7 | 54.6 |
| 8 | -36.7 |
| 9 | 10.5 |
| 10 | 57.7 |
| 11 | 11.1 |
| 12 | -8.0 |


### Data Kelompok 20 — Tugas 10

| No | Hujan | Angin (km/jam) | Alat siap |
|---|---|---|---|
| 1 | tidak | 29 | tidak |
| 2 | ya | 29 | tidak |
| 3 | tidak | 19 | ya |
| 4 | tidak | 10 | ya |
| 5 | ya | 19 | ya |
| 6 | ya | 35 | ya |
| 7 | ya | 34 | tidak |
| 8 | ya | 13 | tidak |
| 9 | ya | 10 | tidak |
| 10 | ya | 21 | tidak |
| 11 | tidak | 22 | ya |
| 12 | tidak | 22 | ya |
