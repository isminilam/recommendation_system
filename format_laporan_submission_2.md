# Laporan Proyek Machine Learning - Nama Anda

## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
- Format Referensi dapat mengacu pada penulisan sitasi [IEEE](https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf), [APA](https://www.mendeley.com/guides/apa-citation-guide/) atau secara umum seperti [di sini](https://penerbitdeepublish.com/menulis-buku-membuat-sitasi-dengan-mudah/)
- Sumber yang bisa digunakan [Scholar](https://scholar.google.com/)

## Business Understanding

### Problem Statements

- Bagaimana distribusi user dengan interaksi terbanyak?
- Bagaimana distribusi produk berdasarkan rating tertinggi dan terendah?
- Bagaimana membangun sistem rekomendasi produk fashion berdasarkan kemiripan atribut seperti kategori, warna, merek, dan ukuran?


### Goals

- Menampilkan visualisasi distribusi interaksi pengguna untuk mengidentifikasi user dengan aktivitas terbanyak.
- Menampilkan distribusi rating produk untuk memahami kualitas dan persepsi produk secara umum.
- Mengembangkan sistem rekomendasi produk berbasis atribut produk untuk meningkatkan pengalaman pengguna dalam memilih produk fashion.


**Solution Approach**:

- Visualisasi Distribusi Interaksi Pengguna

  Menganalisis dan menampilkan distribusi interaksi user menggunakan grafik seperti histogram atau bar chart untuk mengidentifikasi pengguna dengan aktivitas terbanyak.
  
- Visualisasi Distribusi Rating Produk

  Menggambarkan persebaran rating produk dengan histogram atau boxplot untuk mengenali produk dengan rating tertinggi dan terendah.

- Sistem Rekomendasi Berbasis Content-Based Filtering (CBF)

  Membangun sistem rekomendasi yang menghitung kemiripan produk berdasarkan atribut (kategori, warna, merek, ukuran) menggunakan metrik seperti cosine similarity.

## Data Understanding
Dataset yang digunakan dalam proyek ini diambil dari situs [Kaggle - Fashion Product](https://www.kaggle.com/datasets/bhanupratapbiswas/fashion-products). Dataset ini berisi informasi produk fashion yang dijual secara online, serta mencakup fitur-fitur yang relevan untuk membuat sistem rekomendasi produk.

Variabel-variabel pada Fashion Product dataset adalah sebagai berikut:
| Nama Variabel | Deskripsi                                                                                                       | Tipe Data            |
| ------------- | --------------------------------------------------------------------------------------------------------------- | -------------------- |
| User ID       | Nomor unik yang mengidentifikasi pengguna.                                                                      | int64 (Numerik)      |
| Product ID    | Nomor unik yang mengidentifikasi setiap produk fashion.                                                         | int64 (Numerik)      |
| Product Name  | Nama dari produk fashion.                                                                                       | object (Kategorikal) |
| Brand         | Merek produk fashion.                                                                                           | object (Kategorikal) |
| Category      | Kategori produk.                                                                                                | object (Kategorikal) |
| Price         | Harga produk.                                                                                                   | int64 (Numerik)      |
| Rating        | Nilai rating produk yang diberikan oleh pengguna, dengan skala 1 sampai 5.                                      | float64 (Numerik)    |
| Color         | Warna utama produk.                                                                                             | object (Kategorikal) |
| Size          | Ukuran produk.                                                                                                  | object (Kategorikal) |

Informasi awal dataset:

- Terdiri dari 9 kolom dengan 1000 baris.
- Tidak memiliki missing value.
- Tidak memiliki duplikasi data.
- Tidak memiliki outlier.
- User ID hanya sampai 100.

Exploratory Data Analysis (EDA)

1. Distribusi Antar Fitur Numerik

   ![image](https://github.com/user-attachments/assets/4738db6d-5cab-4610-8878-f3a115cd58d7)
   Insight:

3. Distribusi Antar Fitur Kategorikal

   ![image](https://github.com/user-attachments/assets/33d7240b-6f9b-46e0-84ef-f1f498c2f583)
   Insight:

4. Distribusi User ID dengan Interaksi Terbanyak

   ![image](https://github.com/user-attachments/assets/102d1b35-1d7a-4616-8ed2-a343c6a4a2b4)
   Insight:

5. Distribusi Produk dengan Rating Tertinggi

   ![image](https://github.com/user-attachments/assets/bcf1522e-1fb2-405f-b0dc-2131239e4a2e)
   Insight:

6. Distribusi Produk dengan Rating Terendah

   ![image](https://github.com/user-attachments/assets/ecdf137a-17c1-42ad-9d9a-656691b4100b)
   Insight:
   
8. Visualisasi Korelasi Antar Fitur Numerik
   
   ![image](https://github.com/user-attachments/assets/5a03c5a6-172b-4e3e-b264-07a81383d441)
   Insight:

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
