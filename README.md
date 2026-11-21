# Replacement-Analysis-Simulator-Pert-10-dan-Pert-11
Replacement Analysis when the Required Service Is Long and Replacement Analysis with Tax Considerations
from pathlib import Path

content = r'''# Replacement Analysis (Analisis Penggantian Aset)
## Materi Ekonomi Teknik — Mg 10 dan Mg 11

Materi ini disusun untuk mahasiswa D4 Teknologi Rekayasa Manufaktur pada mata kuliah **Ekonomi Teknik**. Pembahasan mencakup analisis penggantian aset pada periode layanan panjang serta analisis penggantian aset dengan mempertimbangkan pajak.

---

## Daftar Isi

1. [Capaian Pembelajaran](#1-capaian-pembelajaran)
2. [Mg 10 — Replacement Analysis when the Required Service Is Long](#2-mg-10--replacement-analysis-when-the-required-service-is-long)
   - [Komponen Data](#21-komponen-data-yang-diperlukan)
   - [Contoh Struktur Data Defender dan Challenger](#22-contoh-struktur-data-defender-dan-challenger)
   - [Faktor Bunga](#23-faktor-bunga)
   - [Kompetensi Perhitungan](#24-kompetensi-perhitungan)
   - [Metode Keputusan](#25-metode-keputusan)
3. [Mg 11 — Replacement Analysis with Tax Considerations](#3-mg-11--replacement-analysis-with-tax-considerations)
   - [Komponen Data Setelah Pajak](#31-komponen-data-yang-diperlukan)
   - [Jadwal Penyusutan](#32-jadwal-penyusutan-depreciation-schedule)
   - [Pajak atas Pelepasan Aset](#33-perhitungan-pajak-pelepasan-aset)
   - [After-Tax Cash Flow](#34-after-tax-cash-flow)
4. [Perbedaan Mg 10 dan Mg 11](#4-perbedaan-mg-10-dan-mg-11)
5. [Urutan Pembelajaran](#5-urutan-pembelajaran)
6. [Catatan Penerapan di Indonesia](#6-catatan-penerapan-di-indonesia)

---

## 1. Capaian Pembelajaran

Setelah mempelajari kedua topik, mahasiswa diharapkan mampu:

- Mengidentifikasi aset lama (*defender*) dan aset pengganti (*challenger*).
- Menyusun arus kas berdasarkan harga perolehan, biaya operasi dan pemeliharaan, biaya perbaikan, serta nilai pasar atau nilai sisa.
- Menghitung *Present Worth* (PW) dan *Equivalent Annual Cost* (EAC/AEC).
- Menentukan *economic service life* setiap alternatif.
- Menentukan waktu penggantian aset menggunakan *marginal analysis*.
- Menghitung penyusutan, nilai buku, keuntungan atau kerugian pelepasan aset, serta dampak pajaknya.
- Menyusun dan mengevaluasi *after-tax cash flow*.

## 2. Mg 10 — Replacement Analysis when the Required Service Is Long

### Analisis Penggantian Saat Layanan yang Diperlukan Membutuhkan Waktu Lama

Analisis ini menentukan kapan aset lama (*defender*) perlu dipertahankan atau diganti dengan aset baru (*challenger*). Keputusan mempertimbangkan umur ekonomis, biaya operasi, nilai pasar, tingkat bunga, periode perencanaan, dan perkembangan teknologi.

Materi sumber mengelompokkan pertimbangan utama ke dalam *planning horizon*, *technology*, dan *relevant cash flow information*.

### 2.1. Komponen Data yang Diperlukan

| No. | Komponen | Data/kriteria yang harus tersedia | Fungsi dalam analisis |
|---:|---|---|---|
| 1 | Aset lama (*Defender*) | Harga perolehan, umur aset, kondisi teknis, nilai pasar saat ini | Menentukan kelayakan mempertahankan aset |
| 2 | Aset pengganti (*Challenger*) | Harga pembelian, biaya instalasi, biaya transportasi, kapasitas, dan efisiensi | Menentukan alternatif penggantian |
| 3 | Biaya operasional (O&M) | Biaya energi, tenaga kerja, pelumas, bahan habis pakai, dan biaya operasional tahunan | Menghitung biaya penggunaan aset |
| 4 | Biaya pemeliharaan dan perbaikan | *Preventive maintenance*, *corrective maintenance*, dan *overhaul* | Mengidentifikasi kenaikan biaya seiring umur aset |
| 5 | Nilai sisa (*Salvage Value*) | Estimasi harga jual atau nilai pelepasan aset pada akhir setiap tahun | Menghitung nilai pemulihan investasi |
| 6 | Nilai pasar (*Market Value*) | Harga jual aset jika dilepas sekarang maupun pada tahun mendatang | Menghitung biaya peluang mempertahankan aset |
| 7 | Tingkat bunga (MARR) | *Minimum Attractive Rate of Return*, misalnya 12% atau 15% | Mendiskontokan arus kas |
| 8 | Umur ekonomis (*Economic Service Life*) | Estimasi umur penggunaan masing-masing alternatif | Menentukan periode penggunaan yang paling ekonomis |
| 9 | Periode perencanaan (*Planning Horizon*) | Periode layanan terbatas atau tidak terbatas | Menentukan metode evaluasi |
| 10 | Perkembangan teknologi | Efisiensi, produktivitas, keandalan, dan potensi keusangan teknologi | Mempertimbangkan waktu terbaik untuk mengganti aset |

*Sumber: materi Replacement Decisions, Section 14.3.*

### 2.2. Contoh Struktur Data Defender dan Challenger

Mahasiswa sebaiknya mengolah data dasar terlebih dahulu sebelum diberikan nilai AEC. Angka pada tabel berikut merupakan **ilustrasi rancangan soal**, bukan data dari buku.

#### Tabel 1. Data Aset Lama (Defender)

| Tahun | Biaya overhaul | Biaya O&M | Nilai pasar akhir tahun |
|---:|---:|---:|---:|
| 0 | Rp5.000.000 | — | Rp20.000.000 |
| 1 | — | Rp4.000.000 | Rp16.000.000 |
| 2 | — | Rp5.000.000 | Rp12.000.000 |
| 3 | Rp2.000.000 | Rp6.000.000 | Rp9.000.000 |
| 4 | — | Rp8.000.000 | Rp6.000.000 |
| 5 | — | Rp10.000.000 | Rp3.000.000 |

#### Tabel 2. Data Aset Baru (Challenger)

| Komponen | Nilai |
|---|---:|
| Harga pembelian | Rp50.000.000 |
| Biaya instalasi | Rp3.000.000 |
| Biaya transportasi | Rp1.000.000 |
| Biaya O&M tahun pertama | Rp3.000.000 |
| Kenaikan O&M per tahun | Rp750.000 |
| Nilai sisa tahun pertama | Rp35.000.000 |
| Penurunan nilai sisa per tahun | Rp3.000.000 |
| Umur teknis estimasi | 6 tahun |
| MARR | 12% per tahun |

### 2.3. Faktor Bunga

Mahasiswa perlu memahami dan menggunakan faktor bunga majemuk. Faktor-faktor berikut menjadi bagian dari perhitungan PW dan AEC.

| Faktor | Rumus | Kegunaan |
|---|---|---|
| \(P/F\) | \(\displaystyle \frac{1}{(1+i)^n}\) | Mengubah nilai masa depan menjadi nilai sekarang |
| \(F/P\) | \((1+i)^n\) | Mengubah nilai sekarang menjadi nilai masa depan |
| \(P/A\) | \(\displaystyle \frac{(1+i)^n-1}{i(1+i)^n}\) | Menghitung nilai sekarang anuitas |
| \(A/P\) | \(\displaystyle \frac{i(1+i)^n}{(1+i)^n-1}\) | Menghitung nilai tahunan ekuivalen dari nilai sekarang |
| \(A/F\) | \(\displaystyle \frac{i}{(1+i)^n-1}\) | Menghitung setoran tahunan untuk mencapai nilai masa depan |
| \(A/G\) | \(\displaystyle \frac{1}{i}-\frac{n}{(1+i)^n-1}\) | Mengonversi kenaikan biaya tahunan secara bertahap |

Keterangan:

- \(P\) = nilai sekarang (*present worth*).
- \(F\) = nilai masa depan (*future worth*).
- \(A\) = nilai tahunan ekuivalen (*annual worth*).
- \(G\) = kenaikan aritmetika tahunan (*arithmetic gradient*).
- \(i\) = tingkat bunga per periode.
- \(n\) = jumlah periode.

Tabel faktor bunga dapat disediakan berdasarkan MARR dan umur aset, misalnya \(i = 10\%\), \(12\%\), dan \(15\%\), serta \(n = 1\) sampai dengan 10 tahun.

### 2.4. Kompetensi Perhitungan

| No. | Materi perhitungan | Output yang diharapkan |
|---:|---|---|
| 1 | *Cash flow defender* | Diagram arus kas aset lama |
| 2 | *Cash flow challenger* | Diagram arus kas aset baru |
| 3 | *Capital recovery* | Biaya pemulihan modal |
| 4 | *Equivalent Annual Cost* (EAC/AEC) | Biaya tahunan ekuivalen |
| 5 | *Economic Service Life* | Umur ekonomis masing-masing aset |
| 6 | *Defender vs. Challenger* | Perbandingan biaya kedua alternatif |
| 7 | *Marginal Analysis* | Biaya tambahan mempertahankan aset satu tahun lagi |
| 8 | *Replacement Timing* | Tahun optimal penggantian |

### 2.5. Metode Keputusan

Dua metode keputusan yang perlu dipahami:

1. **Infinite Planning Horizon** — menggunakan *Annual Equivalent Cost* (AEC) dan analisis marginal.
2. **Finite Planning Horizon** — menggunakan *Present Worth* (PW) untuk membandingkan pola penggantian selama periode perencanaan yang terbatas.

Kedua pendekatan tersebut digunakan sesuai karakteristik periode layanan yang dianalisis.

## 3. Mg 11 — Replacement Analysis with Tax Considerations

### Analisis Penggantian dengan Mempertimbangkan Aspek Pajak

Mg 11 merupakan pengembangan dari Mg 10. Perbedaannya adalah keputusan penggantian aset harus mempertimbangkan dampak pajak terhadap arus kas. Karena itu, analisis memerlukan informasi penyusutan, nilai buku, tarif pajak, keuntungan atau kerugian pelepasan aset, serta arus kas setelah pajak.

### 3.1. Komponen Data yang Diperlukan

| No. | Komponen | Data/kriteria yang harus tersedia | Fungsi dalam analisis |
|---:|---|---|---|
| 1 | Harga perolehan aset | Harga pembelian awal dan biaya yang dikapitalisasi | Menentukan dasar penyusutan |
| 2 | Metode penyusutan | Metode dan jadwal depresiasi | Menghitung beban penyusutan setiap tahun |
| 3 | Nilai buku (*Book Value*) | Harga perolehan dikurangi akumulasi penyusutan | Menentukan keuntungan atau kerugian pelepasan |
| 4 | Nilai pasar (*Market Value*) | Harga jual aktual atau estimasi harga jual | Menentukan penerimaan pelepasan aset |
| 5 | Nilai sisa (*Salvage Value*) | Nilai aset pada akhir periode penggunaan | Menghitung arus kas terminal |
| 6 | Tarif pajak (*Tax Rate*) | Tarif pajak penghasilan marginal yang relevan | Menghitung dampak pajak |
| 7 | Keuntungan/kerugian pelepasan | Selisih nilai jual dengan nilai buku | Menghitung pajak atas keuntungan atau penghematan pajak atas kerugian |
| 8 | Biaya operasional setelah pajak | O&M setelah memperhitungkan penghematan pajak | Menghitung biaya bersih |
| 9 | *Depreciation Tax Shield* | Penghematan pajak akibat penyusutan yang dapat dikurangkan | Menghitung manfaat pajak |
| 10 | *After-Tax MARR* | Tingkat pengembalian minimum setelah pajak | Menghitung nilai ekuivalen setelah pajak |
| 11 | *After-Tax Cash Flow* | Arus kas bersih setelah pajak | Membandingkan alternatif penggantian |

*Sumber: Section 14.4, Replacement Analysis with Tax Considerations.*

### 3.2. Jadwal Penyusutan (Depreciation Schedule)

Jadwal penyusutan merupakan komponen penting dalam Mg 11.

**Contoh data ilustratif:**

- Harga mesin: Rp100.000.000.
- Umur penyusutan: 5 tahun.
- Metode: garis lurus.
- Nilai residu untuk penyusutan: Rp10.000.000.

#### Tabel 3. Jadwal Penyusutan Garis Lurus

| Tahun | Nilai buku awal | Beban penyusutan | Akumulasi penyusutan | Nilai buku akhir |
|---:|---:|---:|---:|---:|
| 0 | — | — | — | Rp100.000.000 |
| 1 | Rp100.000.000 | Rp18.000.000 | Rp18.000.000 | Rp82.000.000 |
| 2 | Rp82.000.000 | Rp18.000.000 | Rp36.000.000 | Rp64.000.000 |
| 3 | Rp64.000.000 | Rp18.000.000 | Rp54.000.000 | Rp46.000.000 |
| 4 | Rp46.000.000 | Rp18.000.000 | Rp72.000.000 | Rp28.000.000 |
| 5 | Rp28.000.000 | Rp18.000.000 | Rp90.000.000 | Rp10.000.000 |

Rumus metode garis lurus:

\[
D = \frac{C-S}{N}
\]

Keterangan:

- \(D\) = beban penyusutan tahunan.
- \(C\) = harga perolehan.
- \(S\) = nilai residu untuk tujuan penyusutan.
- \(N\) = umur penyusutan.

### 3.3. Perhitungan Pajak Pelepasan Aset

Mahasiswa harus dapat membedakan nilai pasar (*market value*) dan nilai buku (*book value*).

**Contoh ilustratif:**

| Komponen | Nilai |
|---|---:|
| Harga perolehan mesin | Rp100.000.000 |
| Akumulasi penyusutan | Rp60.000.000 |
| Nilai buku | Rp40.000.000 |
| Harga jual mesin | Rp30.000.000 |
| Kerugian pelepasan | Rp10.000.000 |
| Tarif pajak ilustratif | 22% |
| Penghematan pajak (jika kerugian dapat dikurangkan) | Rp2.200.000 |
| Penerimaan bersih setelah pajak | Rp32.200.000 |

Secara umum, dengan asumsi keuntungan dan kerugian pelepasan dikenakan perlakuan pajak yang sama:

\[
BV = C-D_{\text{akumulasi}}
\]

\[
G/L = MV-BV
\]

\[
NP = MV-t(MV-BV)
\]

Keterangan:

- \(BV\) = nilai buku (*book value*).
- \(MV\) = nilai pasar atau harga jual.
- \(G/L\) = keuntungan atau kerugian pelepasan.
- \(t\) = tarif pajak.
- \(NP\) = penerimaan bersih setelah pajak.

Pada contoh tersebut, kerugian pelepasan menghasilkan penghematan pajak sehingga penerimaan bersih lebih tinggi daripada harga jual sebelum pajak, dengan asumsi manfaat pajak tersebut dapat direalisasikan.

### 3.4. After-Tax Cash Flow

Mahasiswa harus mampu mengintegrasikan komponen biaya operasi, penyusutan, dan dampak pajak ke dalam arus kas setelah pajak.

Formula umum untuk operasi aset, dengan asumsi biaya O&M dapat dikurangkan dari penghasilan kena pajak:

\[
ATCF=-O\&M(1-t)+D(t)
\]

Keterangan:

- \(O\&M\) = biaya operasi dan pemeliharaan.
- \(D\) = penyusutan.
- \(t\) = tarif pajak.

#### Tabel 4. Ilustrasi Perhitungan Biaya Setelah Pajak

| Komponen | Tahun 1 | Tahun 2 | Tahun 3 |
|---|---:|---:|---:|
| Biaya O&M | Rp10.000.000 | Rp12.000.000 | Rp15.000.000 |
| Beban penyusutan | Rp18.000.000 | Rp18.000.000 | Rp18.000.000 |
| Penghematan pajak O&M (22%) | Rp2.200.000 | Rp2.640.000 | Rp3.300.000 |
| *Depreciation tax shield* (22%) | Rp3.960.000 | Rp3.960.000 | Rp3.960.000 |
| Biaya O&M setelah pajak | Rp7.800.000 | Rp9.360.000 | Rp11.700.000 |
| Total biaya bersih setelah pajak | Rp3.840.000 | Rp5.400.000 | Rp7.740.000 |

Nilai tersebut merupakan ilustrasi untuk menunjukkan hubungan antara biaya operasional dan manfaat pajak penyusutan.

Materi sumber juga menekankan penggunaan *generalized cash flow approach* dan *tabular approach* untuk menghitung biaya tahunan ekuivalen setelah pajak.

## 4. Perbedaan Mg 10 dan Mg 11

| Aspek | Mg 10 | Mg 11 |
|---|---|---|
| Fokus | Keputusan penggantian aset | Keputusan penggantian setelah pajak |
| Defender | Ada | Ada |
| Challenger | Ada | Ada |
| Harga pembelian | Ada | Ada |
| Biaya O&M | Ada | Ada |
| Biaya overhaul | Ada | Ada |
| Nilai pasar | Ada | Ada |
| Nilai sisa | Ada | Ada |
| MARR | Sebelum pajak sesuai asumsi analisis | *After-tax MARR* |
| Penyusutan | Tidak menjadi fokus utama | Wajib |
| Nilai buku | Tidak menjadi fokus utama | Wajib |
| Tarif pajak | Tidak | Wajib |
| *Tax shield* | Tidak | Wajib |
| *Gain/Loss disposal* | Tidak | Wajib |
| *After-tax cash flow* | Tidak | Wajib |
| Metode keputusan | AEC, PW, *Marginal Analysis* | *After-tax AEC* dan PW |

## 5. Urutan Pembelajaran

Urutan pembelajaran disusun dari identifikasi data, pemodelan arus kas, perhitungan ekonomi, hingga penetapan keputusan.

### Mg 10 — Replacement Analysis

1. Konsep *Defender* vs. *Challenger*.
2. Identifikasi data aset lama dan aset baru.
3. Identifikasi biaya O&M, overhaul, dan *salvage value*.
4. Penyusunan *Cash Flow Diagram* kedua alternatif.
5. Perhitungan AEC dan *Economic Service Life*.
6. Perbandingan AEC Defender dan Challenger.
7. *Marginal Analysis* untuk menentukan waktu penggantian.
8. PW Analysis untuk *finite planning horizon*.
9. Penetapan keputusan penggantian aset.

### Mg 11 — Replacement Analysis with Tax

1. Tinjauan konsep *replacement analysis* Mg 10.
2. *Depreciation* dan *depreciation schedule*.
3. Perhitungan *book value*.
4. Perhitungan *gain/loss* dari pelepasan aset.
5. Perhitungan *net proceeds after tax*.
6. Perhitungan *depreciation tax shield*.
7. Perhitungan *after-tax operating cost*.
8. Penyusunan *after-tax cash flow diagram*.
9. Perhitungan *after-tax AEC* dan PW.
10. Keputusan penggantian berdasarkan biaya setelah pajak.

## 6. Catatan Penerapan di Indonesia

Materi sumber menggunakan sistem penyusutan MACRS (*Modified Accelerated Cost Recovery System*) dan *half-year convention*, yang merupakan sistem perpajakan Amerika Serikat. Jadwal MACRS tidak boleh langsung digunakan sebagai ketentuan perpajakan Indonesia.

Untuk studi kasus Indonesia, gunakan ketentuan penyusutan fiskal yang berlaku sesuai jenis aset dan peraturan perpajakan terkait. Tarif pajak dalam soal harus dinyatakan sebagai asumsi atau disesuaikan dengan ketentuan yang berlaku pada saat analisis dilakukan.

Mahasiswa perlu memahami perbedaan antara:

- Penyusutan komersial (akuntansi).
- Penyusutan fiskal (perpajakan).
- Dampak penyusutan terhadap arus kas setelah pajak.

> **Catatan akademik:** Rumus dan contoh numerik dalam materi ini mengikuti asumsi yang dinyatakan pada masing-masing bagian. Untuk penerapan perpajakan aktual, validasi kembali perlakuan fiskal, tarif, dan ketentuan yang berlaku. Contoh angka yang disebut sebagai ilustrasi tidak boleh diperlakukan sebagai ketentuan perpajakan.

---

## Referensi Materi

- *Replacement Decisions*, Section 14.3.
- *Replacement Analysis with Tax Considerations*, Section 14.4.

*Catatan: rincian bibliografi lengkap tidak tercantum dalam materi sumber yang digunakan untuk menyusun file ini.*
'''

path = Path("/mnt/data/Replacement_Analysis_Mg10_Mg11.md")
path.write_text(content, encoding="utf-8")
print(f"Markdown dibuat: {path}")
