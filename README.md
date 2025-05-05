# Klasifikasi-SIBI-KNN-LKS-Jatim-2025

Repositori ini berisi dua implementasi model K-Nearest Neighbors (KNN) untuk mengenali isyarat tangan statis alfabet Bahasa Isyarat Indonesia (SIBI), dikembangkan untuk **Lomba Kompetensi Siswa (LKS) Jawa Timur 2025** kategori IT Software Solutions for Business. Proyek ini dibuat oleh seorang siswa peserta lomba di bawah bimbingan mentornya, sebagai bagian dari tantangan pemrograman kompetitif. Dataset berisi koordinat keypoint tangan 2D untuk huruf SIBI A-I dan K-Y (tanpa J dan Z, yang memerlukan gerakan).

## Ikhtisar Proyek

Tujuan proyek ini adalah mengklasifikasikan isyarat tangan SIBI menggunakan algoritma KNN berbasis jarak. Repositori ini menyediakan dua kode:
1. **Kode Siswa**: Implementasi KNN modular dengan metrik jarak dan bobot fleksibel, disubmit oleh siswa untuk LKS. Kode ini meraih **juara 2** pada LKS Jatim 2025.
2. **Kode Mentor**: Implementasi KNN komprehensif dengan fitur engineering relevan dan evaluasi mendalam, dibuat oleh mentor untuk tujuan pembanding dan pembelajaran.

Kedua kode mencakup preprocessing data, feature engineering, pelatihan model, dan evaluasi, tetapi berbeda dalam pendekatan preprocessing dan pemilihan fitur. Kode mentor mencapai akurasi **90,31%**, sementara kode siswa mencapai **19,86%**, terutama karena perbedaan dalam penanganan label tidak valid dan fitur yang digunakan.

## Struktur Repositori

```
Klasifikasi-SIBI-KNN-LKS-Jatim-2025/
├── kode_mentor.ipynb               # Kode KNN mentor dengan preprocessing dan evaluasi
├── kode_siswa.ipynb                # Kode KNN siswa untuk LKS Jatim 2025
├── data_train.csv                  # Dataset pelatihan (placeholder, tidak disertakan)
├── data_test.csv                   # Dataset pengujian (placeholder, tidak disertakan)
├── Soal_LKS_AI_JATIM_2025_SIBI.pdf # Soal resmi LKS Jatim 2025 untuk SIBI
```

## Dataset

Dataset berisi koordinat keypoint tangan 2D (misalnya, `0x`, `0y`, ..., `20x`, `20y`) dari gambar isyarat SIBI. Variabel target adalah huruf SIBI (`char`), dienkode sebagai integer. Dataset terbagi menjadi:
- **Data pelatihan** (`Datafull train.csv`): Untuk melatih model KNN.
- **Data pengujian** (`Datafull test.csv`): Untuk mengevaluasi performa model.

**Catatan**: Karena aturan privasi dan kompetisi, dataset tidak disertakan. Anda dapat menggunakan dataset SIBI dengan format serupa di folder `data_train.csv` dan `data_test.csv`.

## Detail Kode

### 1. Kode Siswa (`kode_siswa.ipynb`)
- **Fitur Utama**:
  - Kelas KNN kustom (`KNN_1`) dengan metrik jarak Euclidean/Manhattan dan bobot uniform/jarak/Gaussian.
  - Preprocessing: Penanganan missing values (mengisi `char` dengan 'Z', yang merupakan kesalahan logika untuk SIBI), koreksi skewness, dan fitur rata-rata koordinat (misalnya, `0xy`).
  - Resampling pada data uji untuk menyeimbangkan kelas, yang mengubah distribusi asli.
  - Evaluasi dengan akurasi dan metrik per kelas (precision, recall, F1-score).
- **Hasil**: Akurasi **19,86%** pada data Test, Akurasi **90%** pada data Train, dipengaruhi oleh pengisian 'Z' yang tidak valid, fitur kurang relevan, dan resampling data uji.
- **Prestasi**: Meraih **juara 2** pada LKS Jatim 2025 kategori IT Software Solutions for Business.

### 2. Kode Mentor (`kode_mentor.ipynb`)
- **Fitur Utama**:
  - Implementasi KNN manual dengan jarak Euclidean dan voting seragam.
  - Preprocessing robust: Validasi label ketat (menghapus label tidak valid seperti 'Z'), clipping outlier, normalisasi min-max, dan fitur jarak Euclidean (misalnya, `dist_0_5`).
  - Evaluasi komprehensif: Akurasi, metrik per kelas, confusion matrix, dan analisis statistik.
- **Hasil**: Akurasi **90,31%** pada data Test, didukung oleh preprocessing logis dan fitur relevan.
- **Tujuan**: Sebagai pembanding dan materi pembelajaran untuk siswa.

## Hasil dan Analisis

- **Kode Siswa**:
  - Akurasi: **19,86%**
  - Tantangan:
    - Kesalahan logika mengisi missing values `char` dengan 'Z', yang tidak valid untuk SIBI.
    - Resampling data uji mengubah distribusi kelas.
    - Fitur rata-rata koordinat kurang relevan untuk klasifikasi isyarat.
  - Visualisasi: Distribusi kelas dan metrik per kelas.
  - Prestasi: **Juara 2** LKS Jatim 2025, menunjukkan potensi besar meskipun ada kekurangan teknis.

- **Kode Mentor**:
  - Akurasi: **90,31%**
  - Keunggulan:
    - Validasi label ketat dan penanganan missing values logis.
    - Fitur jarak Euclidean relevan untuk geometri tangan.
    - Evaluasi mendalam dengan confusion matrix dan metrik per kelas.
  - Visualisasi: Confusion matrix, distribusi prediksi, dan metrik per kelas.

Perbedaan akurasi disebabkan oleh penanganan label tidak valid, pemilihan fitur, dan resampling yang tidak tepat pada kode siswa, seperti dianalisis dalam kompetisi.

## Pelajaran yang Diperoleh

Proyek ini menyoroti konsep penting dalam machine learning untuk tujuan pendidikan:
- **Preprocessing Penting**: Validasi label dan penanganan missing values krusial untuk performa model.
- **Feature Engineering**: Fitur relevan (misalnya, jarak vs rata-rata) meningkatkan akurasi klasifikasi.
- **Integritas Data Uji**: Resampling data uji harus dihindari untuk menjaga distribusi asli.
- **Evaluasi Mendalam**: Metrik per kelas dan confusion matrix membantu memahami perilaku model.

## Kredit

- **Siswa**: Peserta LKS Jatim 2025, meraih **juara 2** kategori IT Software Solutions for Business, untuk pengembangan `kode_siswa.ipynb`.
- **Mentor**: **Michael Angello** & **Bernadus Anggo Seno Aji, S.Kom., M.Kom.**, untuk bimbingan, pengembangan `kode_mentor.ipynb`, dan pengawasan proyek.
- **Kompetisi**: LKS Jawa Timur 2025, kategori IT Software Solutions for Business.

*Repositori ini dibuat untuk tujuan pendidikan dan memamerkan karya selama LKS Jawa Timur 2025. Kontribusi dan saran diterima dengan senang hati!*
