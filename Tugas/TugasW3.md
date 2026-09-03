# Tugas Kelompok — Metode Komputasi (Geofisika)

**Pengganti kuliah tatap muka** · Dikerjakan berkelompok · Deadline: (05.09.26:23.59 @myemail)

---

## 1. Struktur Kelas

- **70 mahasiswa aktif** (S1 Geofisika angkatan 2025) → **20 kelompok**
- Kelompok 1–10 beranggotakan **4 orang**; Kelompok 11–20 beranggotakan **3 orang**
- Tersedia **10 paket tugas**; setiap paket dikerjakan oleh **2 kelompok secara independen**
- Pembagian tugas: **Kelompok k dan Kelompok k+10 mengerjakan Tugas k**
  (Kelompok 1 & 11 → Tugas 1, Kelompok 2 & 12 → Tugas 2, … , Kelompok 10 & 20 → Tugas 10)
- Kedua kelompok pemegang tugas yang sama menjadi **pasangan reviewer** satu sama lain (lihat Bagian 4)

**Daftar anggota lengkap ada di Lampiran C.** Pembagian dilakukan secara acak (seed 20260904) tanpa mempertimbangkan urutan presensi maupun kedekatan pertemanan.

**Pembagian peran di dalam kelompok** (tuliskan di halaman depan laporan):

| Peran | Tanggung jawab |
|---|---|
| Ketua | Implementasi inti algoritma + koordinasi; NIM-nya menjadi sumber seed data |
| Anggota 2 | Implementasi bagian pendukung (pembangkitan data, fungsi pembanding) |
| Anggota 3 | Validasi numerik, plot, dan penulisan laporan |
| Anggota 4 *(khusus Kelompok 1–10)* | Memimpin cross-review ke kelompok pasangan + menjawab pertanyaan analisis |

Setiap orang tetap wajib **memahami seluruh kode**, bukan hanya bagiannya.

---

## 2. Aturan Umum (WAJIB DIBACA)

**Bahasa pemrograman:** Python (boleh juga Fortran/C/Julia/MATLAB).

**Yang boleh dipakai:** `numpy` hanya untuk array & operasi elementer, `matplotlib` untuk plot.

**Yang TIDAK boleh dipakai:** fungsi jadi yang langsung menyelesaikan inti tugas —
`numpy.linalg.solve`, `numpy.linalg.inv`, `numpy.linalg.det`, `numpy.polyfit`,
`scipy.interpolate.*`, `scipy.integrate.*`, `scipy.optimize.*`.
Fungsi-fungsi tersebut **hanya boleh dipakai sebagai pembanding/validasi** di akhir, dan wajib disebutkan.

**Data unik per kelompok.** Setiap kelompok sudah mendapat **angka seed sendiri** (lihat Lampiran C — diambil dari 3 digit terakhir NIM ketua kelompok). Semua data sintetik wajib dibangkitkan dengan `np.random.seed(SEED)` memakai angka tersebut, dan nilai SEED dicetak di awal program. Karena itu angka hasil setiap kelompok berbeda, termasuk antara dua kelompok yang memegang tugas sama — laporan dengan angka identik akan otomatis terdeteksi.

**Standar penulisan kode (ini dinilai):**
- Setiap tahap program mencetak log: tahap apa yang mulai, tahap apa yang selesai
- Untuk loop panjang: tampilkan **persentase progres dan waktu berjalan/ETA**
- Program harus **gagal dengan pesan jelas** yang menyebut tahap mana yang bermasalah — jangan diam lalu crash
- Setiap fungsi diberi docstring dan **nama anggota kelompok yang menulisnya**

---

## 3. Yang Dikumpulkan Setiap Kelompok

1. **Kode program** (`.py`), rapi, berjalan, dengan logging seperti di atas
2. **Laporan singkat maksimal 3 halaman**: metode, hasil, grafik, jawaban pertanyaan analisis
3. **Screencast 5 menit**: rekam layar sambil menjalankan kode dan menjelaskannya. **Ketiga anggota wajib bicara**, masing-masing menjelaskan bagian yang ia tulis
4. **Refleksi individu ½ halaman per orang (tulis tangan, difoto)**: bagian mana yang saya tulis, kesulitan apa yang saya temui, apa yang akhirnya saya pahami
5. **Catatan cross-review** (lihat Bagian 4)

> Catatan: penggunaan AI tidak dilarang, tetapi **wajib dicantumkan** di laporan (bagian mana, prompt apa). Yang dinilai adalah pemahaman kalian, dan itu diuji lewat screencast, pertanyaan analisis, dan tanya jawab lisan saat saya kembali.

---

## 4. Cross-Review / Bug Hunt (wajib)

Dua kelompok yang memegang tugas yang sama saling bertukar kode **sebelum deadline**.

Setiap kelompok harus menemukan dan menuliskan:
- Minimal **2 kelemahan atau bug** pada kode kelompok pasangan (boleh: kasus batas tidak ditangani, pivot nol, indeks salah, konvergensi tidak dicek, dsb.)
- **1 saran perbaikan konkret**

Hasil cross-review dikumpulkan bersama laporan. Kelompok yang bugnya ditemukan **tidak dikurangi nilainya** — justru yang menemukan bug mendapat nilai tambahan. Ini mendorong pembacaan kode secara sungguh-sungguh.

---

## 5. Penilaian

| Komponen | Bobot |
|---|---|
| Implementasi algoritma dari nol (benar & rapi) | 30 |
| Validasi dan uji numerik (konvergensi, pembanding) | 20 |
| Jawaban pertanyaan analisis di laporan | 20 |
| Screencast + refleksi individu | 20 |
| Cross-review | 10 |

Saat saya kembali, setiap kelompok mendapat **tanya jawab lisan 3 menit**. Nilai individu dapat berbeda dari nilai kelompok berdasarkan sesi ini.

---

# PAKET TUGAS

---

## Tugas 1 — Interpolasi Spline Kubik pada Profil Anomali Gravitasi

**Konteks.** Pengukuran gravitasi di lapangan dilakukan pada titik-titik yang jaraknya tidak seragam. Untuk membuat peta atau profil yang halus, nilai di antara titik ukur harus diinterpolasi.

**Data.** Bangkitkan profil sintetik sepanjang x = 0–100 km:
`g(x) = 25*exp(-((x-30)/8)^2) - 15*exp(-((x-65)/12)^2) + 0.05*x + noise`
Ambil 15 titik ukur pada posisi acak (pakai seed kelompok), lalu buang informasi kurva aslinya.

**Yang diimplementasikan.**
- Natural cubic spline dari nol: susun sistem tridiagonal untuk momen kedua, selesaikan dengan **algoritma Thomas** (tulis sendiri)
- Bandingkan dengan interpolasi linear yang juga kalian tulis sendiri

**Validasi.** Plot spline, interpolasi linear, dan kurva asli dalam satu gambar. Hitung RMS error terhadap kurva asli.

**Pertanyaan analisis.**
1. Apa yang terjadi jika dua titik ukur sangat berdekatan? Jalankan dan tunjukkan.
2. Mengapa matriks sistemnya tridiagonal, dan berapa kompleksitas algoritma Thomas dibanding eliminasi Gauss biasa?
3. Ganti syarat batas natural (turunan kedua = 0) menjadi clamped. Apa efeknya di ujung profil?

---

## Tugas 2 — Interpolasi Lagrange & Newton untuk Mengisi Gap Survei Magnetik

**Konteks.** Satu segmen lintasan survei magnetik hilang karena gangguan alat. Rekan kalian mengusulkan interpolasi polinomial berderajat tinggi melewati semua titik. Uji apakah usul itu bijak.

**Data.** Bangkitkan anomali dipol sintetik sepanjang lintasan, ambil 11 titik ukur berjarak sama, lalu hapus 3 titik di tengah sebagai "gap".

**Yang diimplementasikan.**
- Polinomial Lagrange (bentuk langsung)
- Polinomial Newton dengan **tabel divided difference** (cetak tabelnya)
- Interpolasi piecewise derajat rendah (kuadratik lokal) sebagai pembanding

**Validasi.** Tunjukkan bahwa Lagrange dan Newton menghasilkan polinomial yang sama secara numerik. Bandingkan biaya komputasi saat menambah satu titik data baru.

**Pertanyaan analisis.**
1. Naikkan jumlah titik menjadi 21 berjarak sama. Tunjukkan **fenomena Runge** dan jelaskan mengapa terjadi.
2. Ulangi dengan titik Chebyshev. Apa yang berubah?
3. Metode mana yang kalian rekomendasikan untuk mengisi gap survei nyata, dan mengapa?

---

## Tugas 3 — Diferensiasi Numerik Sinyal Seismik

**Konteks.** Seismometer merekam kecepatan tanah. Untuk mendapat percepatan, sinyal perlu diturunkan secara numerik — tetapi diferensiasi memperkuat derau.

**Data.** Sintetik Ricker wavelet frekuensi dominan 10 Hz, dt = 0.002 s, panjang 2 s. Tambahkan derau Gaussian dengan SNR = 20 dB (pakai seed kelompok).

**Yang diimplementasikan.**
- Beda maju, beda mundur, beda tengah (orde 2)
- Skema beda tengah 5 titik (orde 4)
- Turunan analitik Ricker sebagai kebenaran acuan

**Validasi.** Plot error terhadap turunan analitik untuk sinyal **tanpa derau**, pada dt = 0.008, 0.004, 0.002, 0.001. Buat plot log-log error vs dt dan hitung kemiringannya.

**Pertanyaan analisis.**
1. Apakah kemiringan sesuai orde teoretis (2 dan 4)? Jika tidak, mengapa?
2. Ulangi dengan sinyal berderau. Apa yang terjadi saat dt diperkecil, dan mengapa error justru bisa membesar?
3. Usulkan satu cara mengatasinya (misal smoothing sebelum turunan) dan buktikan dengan percobaan.

---

## Tugas 4 — Integrasi Numerik untuk Energi Gelombang Seismik

**Konteks.** Energi yang dibawa suatu fase gelombang sebanding dengan integral kuadrat kecepatan partikel terhadap waktu. Nilai ini dipakai antara lain untuk estimasi magnitudo dan atenuasi.

**Data.** Seismogram sintetik: dua paket gelombang Gaussian-modulated sinus (fase P dan fase S) dengan waktu tiba berbeda, dt = 0.005 s.

**Yang diimplementasikan.**
- Aturan trapesium
- Aturan Simpson 1/3 (tangani kasus jumlah interval ganjil dengan benar — ini sering jadi bug)
- Integrasi adaptif sederhana (bagi dua interval sampai toleransi tercapai)

**Validasi.** Uji ketiga metode pada fungsi yang integralnya diketahui analitik. Plot log-log error vs jumlah titik, hitung orde konvergensi masing-masing.

**Pertanyaan analisis.**
1. Berapa orde konvergensi yang kalian ukur untuk trapesium dan Simpson? Cocok dengan teori?
2. Hitung rasio energi fase S terhadap fase P pada seismogram kalian.
3. Pada titik mana penambahan jumlah sampel berhenti memperbaiki hasil? Jelaskan penyebabnya (petunjuk: presisi mesin).

---

## Tugas 5 — Eliminasi Gauss-Jordan untuk Sistem Inversi Resistivitas Kecil

**Konteks.** Inversi geolistrik linear (bentuk sederhana) menghasilkan sistem persamaan linear yang harus diselesaikan untuk memperoleh resistivitas tiap lapisan.

**Data.** Bangun matriks kernel A berukuran 6×6 dan vektor model asli m (pakai seed kelompok), lalu hitung d = A·m. Tugas kalian: dapatkan kembali m dari A dan d.

**Yang diimplementasikan.**
- Eliminasi Gauss-Jordan **tanpa pivoting**
- Eliminasi Gauss-Jordan **dengan partial pivoting**
- Perhitungan residual ‖A·m_hitung − d‖

**Validasi.** Bandingkan hasil kedua versi dan bandingkan dengan `numpy.linalg.solve` (hanya sebagai pembanding akhir).

**Pertanyaan analisis.**
1. Buat kasus di mana versi tanpa pivoting gagal total atau sangat tidak akurat. Tunjukkan matriksnya dan jelaskan.
2. Tambahkan derau kecil (0.1%) pada d. Seberapa besar perubahan pada m? Kaitkan dengan bilangan kondisi matriks (hitung sendiri, boleh pakai norma-1).
3. Apa arti praktis hasil nomor 2 bagi inversi data lapangan yang selalu berderau?

---

## Tugas 6 — Dekomposisi LU untuk Inversi Gravitasi dengan Banyak Sisi Kanan

**Konteks.** Dalam inversi gravitasi, matriks kernel sering tetap sama sementara data diukur berulang kali (banyak lintasan, banyak waktu survei). Menyelesaikan ulang dari awal setiap kali adalah pemborosan.

**Data.** Matriks kernel A berukuran n×n dari model prisma sederhana (n = 8), dan 50 vektor data d berbeda.

**Yang diimplementasikan.**
- Dekomposisi LU metode **Doolittle** (dengan partial pivoting, simpan vektor permutasi)
- Forward substitution dan back substitution terpisah
- Penyelesaian 50 sistem dengan LU yang **hanya dihitung sekali**

**Validasi.** Verifikasi P·A = L·U secara numerik. Bandingkan waktu total LU sekali + 50 substitusi versus Gauss lengkap 50 kali (ukur dengan `time.perf_counter`, tampilkan progres).

**Pertanyaan analisis.**
1. Berapa rasio waktu yang kalian ukur? Bandingkan dengan prediksi teoretis O(n³) vs O(n²).
2. Naikkan n ke 20, 50, 100. Plot waktu vs n dalam log-log dan hitung kemiringannya.
3. Kapan LU **tidak** menguntungkan dibanding Gauss biasa?

---

## Tugas 7 — Determinan dan Invers Matriks untuk Transformasi Koordinat Geodetik

**Konteks.** Transformasi koordinat antar sistem (misal lokal ke UTM) memerlukan matriks transformasi dan inversnya. Determinan menentukan apakah transformasi tersebut valid.

**Data.** Matriks transformasi 3×3 dan 4×4 (rotasi + skala + translasi homogen), serta beberapa matriks uji yang hampir singular.

**Yang diimplementasikan.**
- Determinan dengan **ekspansi kofaktor rekursif**
- Determinan lewat **eliminasi Gauss** (hasil kali diagonal, perhatikan tanda dari pertukaran baris)
- Invers matriks dengan metode **matriks augmented [A|I]**

**Validasi.** Verifikasi A·A⁻¹ = I sampai toleransi tertentu. Verifikasi det(A·B) = det(A)·det(B).

**Pertanyaan analisis.**
1. Ukur waktu ekspansi kofaktor untuk n = 3 sampai 10. Buat tabel dan tunjukkan pertumbuhan faktorial. Estimasi waktu untuk n = 15.
2. Ambil matriks yang hampir singular. Bagaimana perilaku invers dan determinannya?
3. Mengapa dalam praktik komputasi geofisika, orang lebih suka **menyelesaikan sistem** daripada menghitung invers secara eksplisit?

---

## Tugas 8 — Kuadrat Terkecil untuk Kurva Travel-Time Refraksi

**Konteks.** Pada seismik refraksi, waktu tiba gelombang langsung dan gelombang bias membentuk dua garis lurus. Kemiringannya memberi kecepatan lapisan, perpotongannya memberi ketebalan.

**Data.** Bangkitkan data travel-time dua lapisan: V1 dan V2 (V2 > V1) dan kedalaman h dipilih dari seed kelompok. Tambahkan derau pada waktu tiba. 24 geofon.

**Yang diimplementasikan.**
- Regresi linear kuadrat terkecil lewat **persamaan normal** yang diturunkan sendiri (jangan pakai polyfit)
- Pemisahan otomatis dua segmen: coba semua titik potong yang mungkin, pilih yang total RMS-nya minimum
- Hitung V1, V2, crossover distance, dan kedalaman h

**Validasi.** Bandingkan V1, V2, h hasil hitungan dengan nilai asli yang kalian pakai untuk membangkitkan data.

**Pertanyaan analisis.**
1. Estimasi ketidakpastian kemiringan dan titik potong. Bagaimana pengaruhnya ke ketidakpastian h?
2. Naikkan level derau bertahap. Pada level berapa penentuan crossover mulai gagal?
3. Persamaan normal dikenal buruk secara numerik untuk polinomial derajat tinggi. Tunjukkan dengan mencocokkan polinomial derajat 8 pada data kalian, dan jelaskan penyebabnya.

---

## Tugas 9 — Pencarian Akar untuk Menentukan Batas Lapisan Seismik

**Konteks.** Menentukan jarak kritis, sudut datang, atau kedalaman batas lapisan sering berujung pada persamaan nonlinear yang tidak bisa diselesaikan secara analitik.

**Data.** Fungsi travel-time nonlinear dua lapisan; cari jarak x di mana waktu tiba gelombang bias sama dengan gelombang langsung. Parameter dari seed kelompok.

**Yang diimplementasikan.**
- Metode **bisection**
- Metode **Newton-Raphson** (turunan boleh analitik atau numerik — sebutkan pilihan kalian)
- Metode **secant**
- Semua metode mencetak tabel iterasi: iterasi, nilai x, error, dan **cetak log progres**

**Validasi.** Bandingkan akar dari ketiga metode. Tampilkan jumlah iterasi untuk mencapai toleransi 1e-10.

**Pertanyaan analisis.**
1. Buat tabel error tiap iterasi. Tunjukkan bahwa bisection konvergen linear dan Newton konvergen kuadratik.
2. Berikan tebakan awal yang membuat Newton **divergen** atau melompat ke akar lain. Tunjukkan dan jelaskan.
3. Metode mana yang kalian pilih untuk dipakai dalam program otomatis tanpa pengawasan manusia? Beri alasan.

---

## Tugas 10 — Euler vs Runge-Kutta untuk Respons Seismometer

**Konteks.** Seismometer adalah osilator harmonik teredam. Responsnya terhadap gerakan tanah dimodelkan oleh persamaan diferensial orde dua — inti dari kalibrasi instrumen.

**Persamaan.** ẍ + 2ζω₀ẋ + ω₀²x = −ü_ground, dengan ω₀ = 2π f₀. Ambil f₀ = 1 Hz, ζ dipilih dari seed kelompok (antara 0.2 dan 0.9). Input tanah: Ricker wavelet.

**Yang diimplementasikan.**
- Ubah menjadi sistem dua persamaan orde satu
- **Euler eksplisit**
- **RK2 (midpoint)**
- **RK4**
- Semua dengan logging tahap dan progres persentase

**Validasi.** Untuk kasus getaran bebas tanpa gaya luar, solusi analitiknya diketahui. Plot log-log error akhir vs dt untuk ketiga metode dan hitung orde konvergensinya.

**Pertanyaan analisis.**
1. Apakah orde yang terukur sesuai teori (1, 2, 4)? Tunjukkan tabelnya.
2. Perbesar dt bertahap sampai Euler menjadi **tidak stabil** (solusi meledak). Pada dt berapa itu terjadi, dan bagaimana kaitannya dengan periode natural?
3. Untuk akurasi target yang sama, mana yang lebih murah secara total: Euler dengan dt kecil, atau RK4 dengan dt besar? Ukur dan buktikan.

---

## Lampiran A — Contoh Kerangka Logging yang Diharapkan

```python
import time

def log_stage(name):
    print(f"[MULAI ] {name}", flush=True)
    return time.perf_counter()

def log_done(name, t0):
    print(f"[SELESAI] {name} — {time.perf_counter()-t0:.3f} s", flush=True)

def log_progress(i, n, t0):
    frac = (i + 1) / n
    elapsed = time.perf_counter() - t0
    eta = elapsed / frac - elapsed
    print(f"  progres {100*frac:6.2f}%  elapsed {elapsed:6.1f}s  ETA {eta:6.1f}s",
          end="\r", flush=True)

# contoh pemakaian
t0 = log_stage("Dekomposisi LU")
for i in range(n):
    if n > 20 and i % max(1, n // 50) == 0:
        log_progress(i, n, t0)
    ...
log_done("Dekomposisi LU", t0)

# gagal dengan pesan jelas
if abs(pivot) < 1e-14:
    raise ValueError(
        f"GAGAL pada tahap 'Dekomposisi LU', baris {i}: "
        f"pivot terlalu kecil ({pivot:.3e}). "
        f"Gunakan partial pivoting atau periksa matriks input."
    )
```

---

## Lampiran B — Teks Pengumuman untuk Mahasiswa

> Selamat pagi. Kuliah Metode Komputasi hari ini diganti dengan **tugas kelompok** karena saya sedang tugas luar kota.
>
> Kelompok **sudah saya bagi secara acak** — silakan cek nama Anda di **Lampiran C** berkas terlampir. Ada 20 kelompok. Nomor kelompok menentukan paket tugas: Kelompok 1 & 11 → Tugas 1, Kelompok 2 & 12 → Tugas 2, dan seterusnya. Tidak ada pertukaran anggota.
>
> Baca **Bagian 2 dan 3** dengan teliti — ada ketentuan tentang seed data khusus tiap kelompok, standar logging kode, screencast 5 menit, refleksi tulis tangan per orang, dan cross-review dengan kelompok pasangan.
>
> Penggunaan AI tidak dilarang, tapi **wajib dicantumkan** di laporan. Yang saya nilai adalah pemahaman kalian, dan itu akan saya uji lewat screencast dan tanya jawab lisan singkat saat saya kembali.
>
> Deadline: (isi). Silakan tanyakan lewat (kanal) kalau ada yang kurang jelas.

---

## Lampiran C — Pembagian Kelompok (berdasarkan NIM)

Pengacakan seed 20260904; 70 peserta aktif terdistribusi tepat satu kali.
Cari NIM Anda sendiri. Daftar dengan nama lengkap dibagikan lewat eLOK / grup kelas.


**Kelompok 1** — Tugas 1 · seed data **720** · ketua: `25/563752/PA/23720`

- `25/563752/PA/23720`
- `25/556169/PA/23346`
- `25/568385/PA/23993`
- `25/559820/PA/23568`

**Kelompok 2** — Tugas 2 · seed data **335** · ketua: `25/556063/PA/23335`

- `25/556063/PA/23335`
- `25/559555/PA/23541`
- `25/559543/PA/23539`
- `25/563651/PA/23713`

**Kelompok 3** — Tugas 3 · seed data **296** · ketua: `25/555624/PA/23296`

- `25/555624/PA/23296`
- `25/563619/PA/23711`
- `25/555895/PA/23320`
- `25/560362/PA/23613`

**Kelompok 4** — Tugas 4 · seed data **562** · ketua: `25/559779/PA/23562`

- `25/559779/PA/23562`
- `25/556397/PA/23363`
- `25/559710/PA/23557`
- `25/564059/PA/23738`

**Kelompok 5** — Tugas 5 · seed data **457** · ketua: `25/558098/PA/23457`

- `25/558098/PA/23457`
- `25/566089/PA/23887`
- `25/561581/PA/23675`
- `25/557065/PA/23397`

**Kelompok 6** — Tugas 6 · seed data **980** · ketua: `25/568050/PA/23980`

- `25/568050/PA/23980`
- `25/564390/PA/23765`
- `25/559366/PA/23525`
- `25/566317/PA/23900`

**Kelompok 7** — Tugas 7 · seed data **892** · ketua: `25/566130/PA/23892`

- `25/566130/PA/23892`
- `25/568111/PA/23982`
- `25/563609/PA/23708`
- `25/561893/PA/23692`

**Kelompok 8** — Tugas 8 · seed data **547** · ketua: `25/559642/PA/23547`

- `25/559642/PA/23547`
- `25/562097/PA/23700`
- `25/555412/PA/23282`
- `25/561532/PA/23673`

**Kelompok 9** — Tugas 9 · seed data **826** · ketua: `25/565092/PA/23826`

- `25/565092/PA/23826`
- `25/557447/PA/23417`
- `25/556798/PA/23382`
- `25/555356/PA/23278`

**Kelompok 10** — Tugas 10 · seed data **839** · ketua: `25/565277/PA/23839`

- `25/565277/PA/23839`
- `25/559665/PA/23552`
- `25/556910/PA/23386`
- `25/564062/PA/23739`

**Kelompok 11** — Tugas 1 · seed data **946** · ketua: `25/567332/PA/23946`

- `25/567332/PA/23946`
- `25/558151/PA/23465`
- `25/565478/PA/23851`

**Kelompok 12** — Tugas 2 · seed data **302** · ketua: `25/555671/PA/23302`

- `25/555671/PA/23302`
- `25/566623/PA/23918`
- `25/565504/PA/23852`

**Kelompok 13** — Tugas 3 · seed data **289** · ketua: `25/555559/PA/23289`

- `25/555559/PA/23289`
- `25/568068/PA/23981`
- `25/561068/PA/23654`

**Kelompok 14** — Tugas 4 · seed data **409** · ketua: `25/557225/PA/23409`

- `25/557225/PA/23409`
- `25/566019/PA/23885`
- `25/561061/PA/23652`

**Kelompok 15** — Tugas 5 · seed data **587** · ketua: `25/560090/PA/23587`

- `25/560090/PA/23587`
- `25/564227/PA/23750`
- `25/559569/PA/23542`

**Kelompok 16** — Tugas 6 · seed data **714** · ketua: `25/563656/PA/23714`

- `25/563656/PA/23714`
- `25/557578/PA/23427`
- `25/564718/PA/23800`

**Kelompok 17** — Tugas 7 · seed data **949** · ketua: `25/567376/PA/23949`

- `25/567376/PA/23949`
- `25/555318/PA/23273`
- `25/556091/PA/23339`

**Kelompok 18** — Tugas 8 · seed data **951** · ketua: `25/567405/PA/23951`

- `25/567405/PA/23951`
- `25/564535/PA/23778`
- `25/567978/PA/23975`

**Kelompok 19** — Tugas 9 · seed data **598** · ketua: `25/560189/PA/23598`

- `25/560189/PA/23598`
- `25/567608/PA/23956`
- `25/561209/PA/23657`

**Kelompok 20** — Tugas 10 · seed data **784** · ketua: `25/564592/PA/23784`

- `25/564592/PA/23784`
- `25/559657/PA/23550`
- `25/557392/PA/23415`
