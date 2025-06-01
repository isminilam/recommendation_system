# Laporan Proyek Machine Learning - Ismi Nilam Anggraini

## Project Overview

Sistem rekomendasi menjadi komponen paling penting pada platform e-commerce. Sistem ini membantu pengguna menemukan produk yang sesuai dengan preferensinya, meningkatkan kepuasan pelanggan, dan mendorong peningkatan penjualan. Di Indonesia, penerapan sistem rekomendasi telah meluas di berbagai sektor, seperti e-commerce, platform streaming media, dan sosial media. 

Berdasarkan penelitian yang dilakukan oleh Riswan et al. (2024) menunjukkan bahwa pengembangan  sistem rekomendasi berbasis  kecerdasan buatan (AI) memiliki  peranan penting  dalam  meningkatkan  pengalaman  pengguna  dan  konversi  penjualan  di  platform  e-commerce, sistem rekomendasi mampu memahami preferensi dan  perilaku pengguna  dengan lebih akurat, menyajikan rekomendasi produk yang lebih personal dan relevan.

Salah satu pendekatan yang umum digunakan dalam sistem rekomendasi adalah Content-Based Filtering (CBF). Metode ini menganalisis atribut produk, seperti nama, kategori, warna, ukuran, dan merek untuk menemukan kesamaan antar item dan memberikan rekomendasi yang relevan kepada pengguna. CBF memiliki keunggulan dalam memberikan rekomendasi yang independen dari data interaksi pengguna lain, sehingga cocok untuk situasi dengan data pengguna yang terbatas.

Referensi:
- Riswan, D., Putra, H. E. R., & Saputra, R. N. (2024). Pengembangan sistem rekomendasi berbasis kecerdasan buatan untuk meningkatkan pengalaman pengguna di platform e-commerce. JUKTISI, 2(3). https://doi.org/10.62712/juktisi.v2i3.145

- Laksamana. (2024, Mei 30). Penerapan sistem rekomendasi memaksimalkan pengalaman pengguna di era digital. Kompasiana. https://www.kompasiana.com/laksamana05421/665834fdc925c4036b5b9f02/penerapan-sistem-rekomendasi-memaksimalkan-pengalaman-pengguna-di-era-digital?page=all#section1

## Business Understanding

### Problem Statements

- Bagaimana distribusi user dengan interaksi terbanyak?
- Bagaimana distribusi produk berdasarkan rating tertinggi dan terendah?
- Bagaimana membangun sistem rekomendasi produk fashion berdasarkan Product ID yang mewakiliki atribut seperti kategori, warna, merek, dan ukuran?


### Goals

- Menampilkan visualisasi distribusi interaksi pengguna untuk mengidentifikasi user dengan aktivitas terbanyak.
- Menampilkan distribusi rating produk untuk memahami kualitas dan persepsi produk secara umum.
- Mengembangkan sistem rekomendasi produk berbasis atribut produk untuk meningkatkan pengalaman pengguna dalam memilih produk fashion.


**Solution Statements**:

- Visualisasi Distribusi Interaksi Pengguna

  Menganalisis dan menampilkan distribusi interaksi user menggunakan grafik seperti histogram atau bar chart untuk mengidentifikasi pengguna dengan aktivitas terbanyak.
  
- Visualisasi Distribusi Rating Produk

  Menggambarkan persebaran rating produk dengan histogram atau boxplot untuk mengenali produk dengan rating tertinggi dan terendah.

- Sistem Rekomendasi Berbasis Content-Based Filtering (CBF)

  Membangun sistem rekomendasi yang menghitung kemiripan produk berdasarkan atribut (kategori, warna, merek, ukuran) menggunakan teknik seperti Cosine Similarity dan Euclidean Distance.

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
   - `User UD`: Distribusi tidak seragam, menunjukkan adanya beberapa pengguna aktif yang mendominasi interaksi.
   - `Product ID`: Distribusi merata.
   - `Price`: Distribusi menunjukkan variasi dengan puncak di harga tertentu, sekitar sekitar 20, 50, dan 80-100.
   - `Rating`: Distribusi yang cukup merata dengan puncak sekitar 2.5-3.5, menunjukkan bahwa pengguna cenderung memberikan penilaian netral.  

3. Distribusi Antar Fitur Kategorikal

   ![image](https://github.com/user-attachments/assets/33d7240b-6f9b-46e0-84ef-f1f498c2f583)
   
   Insight:
   - `Product Name`: Distribusi tidak seragam, Jeans dan Shoes memiliki jumlah terbanyak yang menunjukkan ketertarikan pengguna pada kedua barang tersebut.
   - `Brand`: Distribusi yang cukup merata dengan Nike sebagai jumlah terbanyak, yang menunjukkan preferensi pengguna pada merk olahraga tersebut.
   - `Category`: Distribusi yang cukup merata, menunjukkan permintaan yang cukup merata di semua kategori.
   - `Color`: White dan yellow menjadi jumlah terbanyak, menunjukkan bahwa preferensi pengguna pada warna cerah.
   - `Size`: Distribusi yang merata pada setiap ukuran produk.

4. Distribusi User ID dengan Interaksi Terbanyak

   ![image](https://github.com/user-attachments/assets/102d1b35-1d7a-4616-8ed2-a343c6a4a2b4)
   
   Insight: User ID 37 memiliki jumlah interaksi tertinggi yang menunjukkan user tersebut paling aktif dibandingkan dengan user lainnya. Diikuti dengan user 65 dan 34, yang memiliki interaksi yang cukup tinggi. Hal ini dapat mengidentifikasi pengguna loyal atau aktif yang dapat dijadikan target untuk analisis preferensi, maupun promosi eksklusif. 

5. Distribusi Produk dengan Rating Tertinggi

   ![image](https://github.com/user-attachments/assets/bcf1522e-1fb2-405f-b0dc-2131239e4a2e)
   
   Insight: Produk dengan ID 199, 418, dan 502 mendapat rating hampir sempurna yaitu 4.99, menunjukkan kepuasan pengguna yang sangat tinggi.

6. Distribusi Produk dengan Rating Terendah

   ![image](https://github.com/user-attachments/assets/ecdf137a-17c1-42ad-9d9a-656691b4100b)
   
   Insight: Produk dengan ID 36 dan 136 mendapat rating sangat rendah, mengindikasikan ketidakpuasan pengguna yang tinggi pada produk tersebut.
   
7. Visualisasi Korelasi Antar Fitur Numerik

   ![image](https://github.com/user-attachments/assets/5a03c5a6-172b-4e3e-b264-07a81383d441)
   
   Insight: Semua nilai korelasi berada di kisaran -0.02 hingga 0.04, menunjukkan tidak ada fitur numerik yang memiliki korelasi yang kuat.

## Data Preparation
Pada tahap ini, dilakukan serangkaian proses untuk menyiapkan data agar siap digunakan dalam analisis dan pemodelan. Proses ini penting untuk memastikan data yang digunakan bersih, konsisten, dan sesuai kebutuhan analisis.

1. Menangani Anomali Data

   Memindahkan Dress dalam kategori "Men's Fashion" menjadi "Women's Fashion". Kategori yang tidak sesuai dapat memengaruhi hasil rekomendasi.

   ```
   # Memindahkan Dress dari Men's Fashion ke Women's Fashion
   df.loc[(df['Product Name'] == 'Dress') & (df['Category'] == "Men's Fashion"), 'Category'] = "Women's Fashion"
   print("Jumlah Dress di Men's Fashion setelah pembersihan:",
     len(df[(df['Product Name'] == 'Dress') & (df['Category'] == "Men's Fashion")]))
   ```

      ![image](https://github.com/user-attachments/assets/1901edce-2e98-4f8f-9c4c-4e4dd37b2a91)

2. Normalisasi Format Teks

   Mengubah nilai pada kolom Category, Brand, Color, Size, dan Product Name menjadi huruf kecil (lowercase) untuk menghindari perbedaan nilai yang sama, tetapi dalam format yang berbeda. 

   ```
   # Mengubah nilai pada kolom menjadi Category, Brand, Color, Size, dan Product Name huruf kecil
   df['Category'] = df['Category'].str.lower()
   df['Brand'] = df['Brand'].str.lower()
   df['Color'] = df['Color'].str.lower()
   df['Size'] = df['Size'].str.lower()
   df['Product Name'] = df['Product Name'].str.lower()
   ```
   
3. Seleksi Atribut

   Memilih kolom yang relevan untuk digunakan dalam pemodelan Content-Based Filtering, yaitu Product Name, Category, Brand, Color, dan Size untuk menyaring informasi yang dibutuhkan dalam model.

   ```
   # Menyeleksi atribut dengan memilih kolom yang relevan untuk CBF
   features = ['Product Name', 'Category', 'Brand', 'Color', 'Size']
   cbf_data = df[features].copy()
   ```

4. Transformasi Data menggunakan One-Hot Encoding

   Menggunakan One-Hot Encoding pada fitur kategorikal untuk mengubah nilai kategorikal menjadi format numerik biner. Transformasi ini memungkinkan sistem merepresentasikan fitur dalam bentuk vektor yang bisa dihitung kesamaannya (similarity).

   ```
   # Transformasi Data dengan One-Hot Encoding
   categorical_features = ['Product Name', 'Category', 'Brand', 'Color', 'Size']
   encoder = OneHotEncoder(handle_unknown='ignore')
   encoded_features = encoder.fit_transform(cbf_data[categorical_features])
   encoded_columns = encoder.get_feature_names_out(categorical_features)
   encoded_df = pd.DataFrame(encoded_features.toarray(), columns=encoded_columns, index=cbf_data.index)
   ```


## Modeling
Tahapan ini membahas sistem rekomendasi yang dibangun menggunakan pendekatan Content-Based Filtering dengan teknik Cosine Similarity dan Euclidean Distance. Tujuannya adalah untuk merekomendasikan produk fashion yang mirip berdasarkan atribut, seperti nama produk, kategori, merek, warna, dan ukuran.

- Consine Similarity

  Menghitung cosine similarity untuk mengukur kesamaan antar vektor fitur produk. Matriks akan menyimpan nilai kemiripan antar setiap produk, dengan nilai 0 - 1.0, yang artinya 1.0 berarti identik, dan semakin mendekati 0 berarti semakin tidak mirip. baris dan kolom DataFrame tersebut diberi label sesuai dengan Product ID, sehingga dapat mengidentifikasi kemiripan antara produk tertentu berdasarkan ID-nya.

  Cosine Similarity dirumuskan sebagai berikut.
  
  ![image](https://github.com/user-attachments/assets/f2818c85-4282-4c10-b4bb-cc95a7727709)


- Euclidean Distance

  Euclidean Distance mengukur jarak “garis lurus” antara dua titik dalam ruang multidimensi. Dalam konteks rekomendasi, Euclidean cocok untuk fitur numerik (misalnya harga atau rating), tapi juga bisa diterapkan pada data biner (hasil One-Hot Encoding), meskipun bisa kurang sensitif terhadap sparsity dibanding cosine atau Jaccard.

  Euclidean distance dirumuskan sebagai berikut.

  ![image](https://github.com/user-attachments/assets/9968a808-6d21-4824-a719-ff218566e8b9)

 | **Teknik**             | **Kelebihan**                                                                                                                                                                   | **Kekurangan**                                                                                                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Cosine Similarity**  | - Cocok untuk data berdimensi tinggi dan *sparse*.<br> - Tidak sensitif terhadap skala data.<br> - Efektif untuk data kategorikal atau teks yang telah diubah ke bentuk vektor. | - Tidak mempertimbangkan besar nilai absolut.<br> - Kurang cocok untuk data numerik kontinu.                                                    |
| **Euclidean Distance** | - Intuitif dan mudah dipahami.<br> - Cocok untuk data numerik kontinu seperti harga atau berat.                                                                                 | - Sensitif terhadap skala data (perlu normalisasi).<br> - Kurang efektif untuk data *sparse*.<br> - Kurang akurat untuk data berdimensi tinggi. |

Hasil Rekomendasi Top-5 dengan Product ID 65

![image](https://github.com/user-attachments/assets/68c8e9b1-a99c-417c-b4bb-5689bf8567fb)

![image](https://github.com/user-attachments/assets/186cf323-db2a-4d5a-8361-d4c642ff171e)


## Evaluation
Tahapan ini dilakukan evaluasi sistem rekomendasi untuk menilai seberapa relevan dan efektif model yang dibuat menggunakan pendekatan Content-Based Filtering dalam memberikan rekomendasi produk fashion yang serupa berdasarkan atribut konten kepada pengguna.

Metrik Evaluasi yang Digunakan: 

- Precision@5: Mengukur rasio produk yang direkomendasikan dan relevan terhadap jumlah total rekomendasi yang diberikan (Top-5). Metrik ini menilai ketepatan rekomendasi sistem.

  ![image](https://github.com/user-attachments/assets/7ec57b57-8f8b-4a79-8e40-e300034b728d)

  Keterangan:
  - Mengukur seberapa banyak dari K item yang direkomendasikan merupakan item yang benar-benar relevan.
  - Relevansi didefinisikan berdasarkan atribut seperti nama produk dan kategori yang sama dengan produk awal.


- NDCG@5 (Normalized Discounted Cumulative Gain)
Mengukur kualitas rekomendasi berdasarkan urutan (ranking) dan relevansi. NDCG menilai seberapa baik sistem menempatkan produk yang paling relevan di posisi teratas daftar rekomendasi.

  ![image](https://github.com/user-attachments/assets/97bf8b5d-e6b2-4024-9b44-0fd0d5dd753d)

  ![image](https://github.com/user-attachments/assets/2b7a6b85-cbe3-44b0-9cf5-bd1c3f9742aa)

  Keterangan:
  - 𝑟𝑒𝑙𝑖 adalah skor relevansi pada posisi ke-i dalam daftar rekomendasi (misalnya berdasarkan kesamaan warna dan ukuran).
  - DCG mengukur seberapa relevan item berdasarkan urutan peringkatnya.
  - IDCG adalah DCG terbaik yang mungkin didapat (urutan item paling relevan di atas).
  - NDCG bernilai 1 jika urutan item sangat ideal, dan semakin kecil jika urutan semakin buruk.

Hasil Evaluasi:

| **Teknik**             | **Precision\@5** | **NDCG\@5** |
| ---------------------- | ---------------- | ----------- |
| **Cosine Similarity**  | 1.000            | 0.971       |
| **Euclidean Distance** | 1.000            | 0.971       |

Bedasarkan hasil evaluasi Product ID 65, kedua pendekatan menghasilkan nilai Precision@5 dan NDCG@5 yang sama tinggi untuk data ini, menunjukkan bahwa sistem berhasil merekomendasikan produk relevan. Namun, Cosine Similarity lebih stabil dalam menilai kemiripan antar produk.

Kesimpulan:

Berdasarkan evaluasi terhadap sistem rekomendasi dengan pendekatan Content-Based Filtering menggunakan dua teknik pengukuran kesamaan yaitu Cosine Similarity dan Euclidean Distance, diperoleh hasil evaluasi yang identik, yaitu Precision@5 sebesar 1.000 dan NDCG@5 sebesar 0.971 untuk produk yang diuji (Product ID 65). Hal ini menunjukkan bahwa kedua teknik tersebut dapat memberikan rekomendasi yang relevan sesuai dengan preferensi pengguna. Namun, Cosine Similarity cenderung lebih unggul karena lebih stabil dalam menilai kemiripan antar produk dibandingkan Euclidean Distance.  
