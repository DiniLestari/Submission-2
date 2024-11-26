 # Laporan Proyek Machine Learning: Sistem Rekomendasi Buku
---
### Domain Project

> **Domain proyek yang dipilih dalam proyek machine learning ini adalah mengenai industri buku dan literasi dengan judul proyek "Sistem Rekomendasi Buku"**.

# Latar belakang

Pertumbuhan pasar industri buku dan literasi tengah mengalami pertumbuhan yang cukup tinggi. Ukuran pasar buku global diperkirakan mencapai USD 150,99 miliar pada tahun 2024 dan diproyeksikan tumbuh dengan CAGR  **Compound Annual Growth Rate** [1](https://www.grandviewresearch.com/industry-analysis/books-market) sebesar 4,2% dari tahun 2025 hingga 2030. Peningkatan pengeluaran konsumen untuk buku, yang didorong oleh kenaikan pendapatan dan minat yang berkembang terhadap kegiatan membaca, serta inovasi dalam format yang meningkatkan pengalaman membaca, menjadi faktor utama yang mendorong pertumbuhan pasar ini.


  ![books-market-size](https://github.com/user-attachments/assets/db7c5fa9-3fe3-4144-bb41-5b97ace3a1b5)


Namun, pembaca terkadang menghadapa pembaca menghadapi tantangan dalam menemukan rekomendasi buku yang personal. Toko buku dan perpustakaan tradisional hanya menyediakan panduan terbatas berdasarkan genre atau saran staf, namun metode ini sering kali tidak sesuai dengan selera unik masing-masing individu. Selain itu, meskipun situs ulasan buku sudah ada, banyak di antaranya terpisah dari elemen sosial yang dapat membantu pembaca menemukan buku melalui rekomendasi teman. [2](https://onlinelibrary.wiley.com/doi/10.1155/2023/1514801)

Belum lagi pertumbuhan pesat informasi digital telah menimbulkan tantangan yang signifikan, yaitu terjadinya kelebihan informasi (_information overload_), yang menghambat akses pengguna mengenai pengambilan keputusan. Seringkali ketika kelebihan informasi terjadi, kualitas keputusan yang diambil mengalami penurunan yang signifikan [3](https://www.tandfonline.com/doi/abs/10.1080/14759390300200146). Dalam hal ini, kegiatan memilih buku yang cocok untuk dibaca adalah sesuatu yang cukup memakan energi. 


   <img width="944" alt="Goodread" src="https://github.com/user-attachments/assets/06980be2-1b7f-46ce-a665-610334986b43">


Dengan semakin berkembangnya jumlah buku digital yang tersedia, pembaca sering kali terjebak dalam memilih berdasarkan popularitas atau ulasan tanpa sempat mengeksplorasi lebih dalam mengenai relevansi atau kualitas buku tersebut dalam konteks kebutuhan atau preferensi pribadi mereka​. [4](https://www.theparisreview.org/blog/2019/02/08/reading-in-the-age-of-constant-distraction/)
 
Untuk mengatasi masalah ini, penting bagi pembaca untuk memiliki tujuan yang jelas saat memilih buku—apakah itu untuk hiburan, edukasi, atau untuk memperluas perspektif mereka—serta menggunakan pendekatan membaca yang lebih aktif dan terstruktur, seperti dengan menilai sinopsis, ulasan, dan rekomendasi yang relevan. Teknik ini dapat membantu mengurangi rasa kewalahan dan meningkatkan kualitas pengalaman membaca. [5](https://theinvisiblementor.com/the-art-of-reading-francis-bacons-wisdom-on-consuming-books/)

Hal ini dapat diselesaikan dengan sistem rekomendasi. [6](https://www.%20Interact.%20org/literature/article/information-overload-whyit-matters-and-how-to-combat-it.) Sistem rekomendasi telah dikembangkan untuk mengatasi kelebihan informasi, membantu pengambilan keputusan pengguna, dan mencapai berbagai bentuk personalisasi jelas bahwa model tradisional dalam pengambilan informasi sering kali gagal untuk menghubungkan pengguna dengan materi yang relevan secara optimal.

Untuk mengimplementasikan hal ini, telah dilakukan pembangunan sistem rekomendasi dengan **Collaborative Filtering** [7](https://ieeexplore.ieee.org/document/7176109) Kemiripan didapatkan dengan menggunakan metode cosine similarity [[8](https://dl.acm.org/doi/10.1145/3639233.3639335)]. 

Proyek yang dirancang kali ini merupakan proyek membuat sistem rekomendasi judul buku berdasarkan penggabungan tiga data set mengenai data Books, Users, dan Ratings yang dapat merekomendasikan buku berdasarkan judul buku yang telah dibaca sebelumnya dengan **Collaborative Filtering**. 
___
# Business Understanding
---
#### Problem Statements
berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:

- Bagaimana cara melakukan pra-pemrosesan pada ketiga dataset (Books, Users, dan Ratings) yang akan digunakan agar dapat membuat model yang baik menggunakan teknik Collaborative Filtering?
- Bagaimana memberikan rekomendasi judul buku berdasarkan kemiripan dengan judul buku yang telah dibaca sebelumnya?
 
#### Goals
- Melakukan pra-pemrosesan dengan baik agar dapat digunakan dalam pembuatan model.
- Membuat pelanggan lebih mudah menemukan judul buku yang mirip dengan buku yang telah dibaca sebelumnya dengan bantuan sistem rekomendasi.

#### Solution Statements
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya :
* Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, diantaranya :
    * Mengecek masalah data yang kosong dengan melakukan pengecekan terlebih dahulu.
    * Membaca Data dengan Menentukan Tipe Data Kolom
    * Menghitung besar/panjang data pada dataset terlebih dahulu kemudian mencoba untuk menguraikan jenis-jenis fitur
    * Membersihkan dataset dengan mengisi nilai yang hilang pada beberapa kolom, menghapus entri duplikat, serta menghapus pengguna dengan data yang tidak lengkap.
   
* Metode yang digunakan pada projek ini adalah Collaborative Filtering.
  Untuk mengatasi beberapa keterbatasan pemfilteran berbasis konten, penyaringan kolaboratif menggunakan kesamaan antara pengguna dan item secara bersamaan untuk memberikan rekomendasi. Dengan menganalisis data penilaian, sistem ini membuat tabel pivot yang memetakan buku ke pengguna dan menghitung kesamaan antara buku berdasarkan penilaian pengguna. Sistem ini kemudian merekomendasikan buku yang paling mirip dengan buku input yang diberikan, memberikan pengguna daftar saran yang dipersonalisasi. [9](https://developers.google.com/machine-learning/recommendation/collaborative/basics?hl=id)

 Namun, metode Collaborative Filtering memiliki kelbihan dan kekurangan yaitu: 
 
- Kelebihan:
   - *Kesederhanaan dan Efektivitas*: Collaborative filtering menggunakan cosine similarity adalah metode yang sederhana namun efektif untuk menghitung kesamaan antar item berdasarkan interaksi pengguna. Metode ini tidak memerlukan pemahaman mendalam tentang konten buku, hanya berdasarkan perilaku dan penilaian pengguna, yang membuatnya mudah untuk diimplementasikan.
  - *Personalisasi*: Metode ini mempersonalisasi rekomendasi buku berdasarkan penilaian dan preferensi masing-masing pengguna, menjadikannya lebih relevan bagi pengguna individu.
  - *Skalabilitas*: Sistem ini dapat diskalakan untuk menangani dataset besar dengan banyak buku dan pengguna, karena pendekatan tabel pivot cukup efisien dalam pemrosesan data berskala besar.
 
- **Kekurangan**:

  - *Masalah Cold Start*: Pendekatan ini mengalami kesulitan ketika data untuk pengguna baru atau buku baru terbatas. Buku baru atau pengguna yang belum memberikan penilaian tidak akan tercakup dengan baik dalam proses rekomendasi, yang dapat menghasilkan saran yang kurang optimal.
  - *Keterbatasan Data* (_Sparsity_): Dalam kasus di mana pengguna hanya memberikan penilaian untuk sebagian kecil buku, tabel pivot akan memiliki banyak nilai yang hilang, yang bisa memengaruhi kualitas rekomendasi.
  - *Terlalu Fokus pada Popularitas*: Metode ini cenderung merekomendasikan buku yang lebih populer dengan banyak penilaian, yang berisiko mengabaikan buku yang lebih kecil atau kurang dikenal yang mungkin relevan bagi beberapa pengguna.

# Data Understanding
---

<img width="750" alt="kaggledat" src="https://github.com/user-attachments/assets/f7a8ea40-5dc8-4b0a-a3ba-301cc73441ab">


Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut menyajikan data-data daftar film dari yg terlama hingga ke yg terbaru serta memberikan korelasi dengan data rating yg disediakan pada dataset (tidak terlalu banyak digunakan pada studi kasus projek ini).
Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset : Recommendation System - Collaborative filtering](https://www.kaggle.com/code/shikhararyan/recommendation-system-collaborative-filtering/input)
Lisensi | Unknown
Kategori | Book-crossing datasets
Content | Books.csv, Users.csv, dan Ratings.csv
Jenis dan Ukuran Berkas | csv (73.29 MB), csv (22.63 MB), csv (11.62)

_Book-Crossing dataset_ terdiri dari tiga berkas berikut:

**Users.csv**: Berisi data pengguna dengan ID pengguna (User-ID) yang telah dianonimkan dan dipetakan ke angka-angka. Data demografis seperti Lokasi dan Usia disediakan jika tersedia. Jika tidak ada, kolom-kolom ini akan berisi nilai NULL.

**Books.csv**: Buku diidentifikasi dengan ISBN masing-masing. ISBN yang tidak valid telah dihapus dari dataset. Selain itu, informasi berbasis konten diberikan (Judul Buku, Penulis Buku, Tahun Terbit, Penerbit), yang diperoleh dari layanan Amazon Web Services. Jika sebuah buku memiliki beberapa penulis, hanya penulis pertama yang tercantum. URL yang mengarah ke gambar sampul buku juga disediakan dalam tiga ukuran berbeda (Image-URL-S, Image-URL-M, Image-URL-L), yaitu kecil, sedang, dan besar. URL ini mengarah ke situs web Amazon.

**Ratings.csv**: Berisi informasi penilaian buku. Penilaian (Book-Rating) dapat berupa penilaian eksplisit yang diberikan pada skala 1-10 (nilai yang lebih tinggi menunjukkan apresiasi yang lebih tinggi), atau penilaian implisit yang diberikan dengan angka 0.

Langkah-langkah yang diambil dalam untuk mendapat insight dari tahap data understanding adalah :

1. Basic Exploration
   Mengambil informasi dasar dari dataset.
   
       print("Books dataset:")
       print(books.info())
       print("\nUsers dataset:")
       print(users.info())
       print("\nRatings dataset:")
       print(ratings.info())

   Hasil dari basic exploration didapatkan :
   - Dataset Books.csv
     
       <img width="244" alt="Book data understanding" src="https://github.com/user-attachments/assets/eda4adfd-d144-42b2-bd41-1094e843d392">

   - Dataset Users.csv
     
       <img width="207" alt="user data understanding" src="https://github.com/user-attachments/assets/218561b7-736e-432e-a89b-c688c8dbcdbe">

   - Dataset Ratings.csv
     
       <img width="218" alt="Ratings data understanding" src="https://github.com/user-attachments/assets/0aafbca1-90c9-49fe-8032-e0435bc7cfc9">

2. Mencari data value yang hilang
   
   Mengetahui nilai-nilai kosong dalam dataset sangat penting karena dapat memengaruhi kualitas analisis data dan hasil yang dihasilkan oleh model machine learning. Digunakan kode seperti: 

              print("\nMissing values:")
              print("\nBooks:\n", books.isnull().sum())
              print("\nUsers:\n", users.isnull().sum())
              print("\nRatings:\n", ratings.isnull().sum())

   Hasil dari percarian ini adalah :
   - Dataset Books

     | Column Name          | Missing Values |
     |----------------------|----------------|
     | ISBN                | 0              |
     | Book-Title          | 0              |
     | Book-Author         | 2              |
     | Year-Of-Publication | 0              |
     | Publisher           | 2              |
     | Image-URL-S         | 0              |
     | Image-URL-M         | 0              |
     | Image-URL-L         | 3              |

   - Dataset Users
     | Column Name | Missing Values |
     |-------------|----------------|
     | User-ID     | 0              |
     | Location    | 0              |
     | Age         | 110,762        |

   - Dataset Ratings
     | Column Name  | Missing Values |
     |--------------|----------------|
     | User-ID      | 0              |
     | ISBN         | 0              |
     | Book-Rating  | 0              |

 3. summary statistic
     Tahapan ini mengambil beberapa parameter , seperti : 
     
    - **Ringkasan Statistic** memberikan gambaran umum tentang sebaran rating yang diberikan oleh pengguna.Didapatkan hasil seperti :

       | Statistic | User-ID       | Book-Rating    |
       |-----------|---------------|----------------|
       | **Count** | 1.149780e+06 | 1.149780e+06   |
       | **Mean**  | 1.403864e+05 | 2.866950e+00   |
       | **Std**   | 8.056228e+04 | 3.854184e+00   |
       | **Min**   | 2.000000e+00 | 0.000000e+00   |
       | **25%**   | 7.034500e+04 | 0.000000e+00   |
       | **50%**   | 1.410100e+05 | 0.000000e+00   |
       | **75%**   | 2.110280e+05 | 7.000000e+00   |
       | **Max**   | 2.788540e+05 | 1.000000e+01   |

       Dataset ini mencakup total 1.149.780 pengguna dan 1.149.780 penilaian buku. Rata-rata ID pengguna adalah 140.386,4, dengan penyebaran nilai (standar deviasi) sekitar 80.562,28. Nilai ID pengguna berkisar dari 2 hingga 278.854, dengan distribusi: 25% pengguna memiliki ID di bawah 70.345, median ID adalah 141.010, dan 75% pengguna memiliki ID di bawah 211.028.

       Untuk penilaian buku, rata-rata adalah 2,87, dengan standar deviasi 3,85, menunjukkan variasi yang signifikan dalam data penilaian. Penilaian berkisar dari 0 (implisit) hingga 10 (eksplisit maksimum). Sebanyak 25% buku memiliki penilaian 0, median (50%) juga berada pada 0, menandakan banyak buku yang tidak dinilai eksplisit, sementara 75% buku memiliki penilaian hingga 7.

       Artinya mayoritas pengguna memberikan penilaian rendah atau tidak memberikan penilaian eksplisit (terlihat dari banyaknya nilai 0 pada Book-Rating). Variasi penilaian buku cukup besar, dengan beberapa buku memiliki penilaian maksimum 10. Distribusi ID pengguna cukup merata dalam dataset.

    - **Distribusi Rating Buku**  menampilkan bagaimana rating tersebar, apakah cenderung terkonsentrasi pada nilai tertentu atau tersebar merata.
   
      ![distribusi books ratings](https://github.com/user-attachments/assets/35bf69fa-c1ec-4082-9a86-24e5dbe2805d)


    - **Jumlah Rating per Pengguna** mengidentifikasi pengguna yang paling aktif dalam memberikan rating.

    | Rank | User-ID | Ratings Count |
    |------|---------|---------------|
    | 1    | 11676   | 13602         |  
    | 2    | 198711  | 7550          |
    | 3    | 153662  | 6109          |
    | 4    | 98391   | 5891          |
    | 5    | 35859   | 5850          |


    - **Buku Paling Populer** menunjukkan buku yang paling banyak mendapatkan rating dari pengguna.

    | Rank | ISBN        | Ratings Count |
    |------|-------------|---------------|
    | 1    | 0971880107 | 2502          |
    | 2    | 0316666343 | 1295          |
    | 3    | 0385504209 | 883           |
    | 4    | 0060928336 | 732           |
    | 5    | 0312195516 | 723           |


4. Relationships and Trends
   
- **Menggabungkan Rating dengan Buku** memungkinkan kita untuk mendapatkan informasi yang lebih lengkap dengan menghubungkan data rating dengan data buku.
  
- **Buku yang Paling Banyak Diberi Rating** memberikan wawasan tentang buku mana yang paling banyak mendapat perhatian dari pengguna.

  | Rank | Book Title                                       | Ratings Count |
  |------|--------------------------------------------------|---------------|
  | 1    | Wild Animus                                     | 2502          |
  | 2    | The Lovely Bones: A Novel                       | 1295          |
  | 3    | The Da Vinci Code                               | 898           |
  | 4    | A Painted House                                 | 838           |
  | 5    | The Nanny Diaries: A Novel                      | 828           |
  | 6    | Bridget Jones's Diary                           | 815           |
  | 7    | The Secret Life of Bees                         | 774           |
  | 8    | Divine Secrets of the Ya-Ya Sisterhood: A Novel | 740           |
  | 9    | The Red Tent (Bestselling Backlist)             | 723           |
  | 10   | Angels &amp; Demons                             | 670           |

  
- **Visualisasi Buku dengan Rating Terbanyak** mempermudah pemahaman tentang buku populer dengan menggunakan grafik batang.

  ![grafik most ratings](https://github.com/user-attachments/assets/9f1ef800-2f47-465a-8211-905506ff8bad)

  
- **Distribusi Usia Pengguna** membantu kita memahami demografi pengguna dalam hal usia, yang bisa berguna untuk analisis lebih lanjut, seperti apakah ada kategori usia tertentu yang lebih banyak memberikan rating.

![Usia](https://github.com/user-attachments/assets/0c2534c1-7bcc-4c64-b145-4acb194a0184)

- **Wawasan dari Metadata**
  - **Top Penulis** dengan Buku Terbanyak memberikan informasi tentang penulis yang memiliki kontribusi terbesar dalam jumlah buku yang ada dalam dataset.

  | Rank | Author                | Number of Books |
  |------|-----------------------|-----------------|
  | 1    | Agatha Christie       | 632             |
  | 2    | William Shakespeare   | 567             |
  | 3    | Stephen King          | 524             |
  | 4    | Ann M. Martin         | 423             |
  | 5    | Carolyn Keene         | 373             |
  | 6    | Francine Pascal       | 372             |
  | 7    | Isaac Asimov          | 330             |
  | 8    | Nora Roberts          | 315             |
  | 9    | Barbara Cartland      | 307             |
  | 10   | Charles Dickens       | 302             |
    
  - **Visualisasi Penulis Teratas dengan Buku Terbanyak** memungkinkan kita untuk melihat secara grafis siapa saja penulis yang paling produktif, sehingga memudahkan analisis lebih lanjut tentang popularitas dan kontribusi penulis tersebut terhadap koleksi buku.
   
![10 author with most books](https://github.com/user-attachments/assets/5f715e4b-d3cc-4c75-b5d7-32eee932eda0)

# Data Preparation
---
Berikut adalah tahapan-tahapan dalam melakukan Persiapan data:
1. Memberikan tipe data, membersihkan kolom, juga konversi tahun ke Integer

      - Pada baris ini, data dari file CSV Books.csv dibaca menggunakan fungsi pd.read_csv(). Saat membaca file CSV, tipe data setiap kolom ditentukan menggunakan parameter dtype untuk menghindari peringatan atau error. Kolom seperti `ISBN`, `Book-Title`, `Book-Author`, `Publisher`, dan `URL gambar` (_Image-URL-S, Image-URL-M, Image-URL-L_) diatur sebagai string (_str_). Kolom Year-Of-Publication diatur sebagai tipe object karena mungkin memiliki tipe data campuran (angka dan teks).
      - Argumen dtype digunakan untuk menentukan tipe data yang sesuai untuk - setiap kolom dalam dataset. Misalnya, kolom ISBN, Book-Title, B- ook-Author, dan lainnya ditetapkan dengan tipe data string (str).
      - Untuk kolom Year-Of-Publication, tipe data diatur menjadi object untuk menangani kemungkinan adanya nilai campuran (seperti tahun yang mungkin berupa teks atau angka)(menghandle warning dari python)
  
            #Handling warnings
            books = pd.read_csv('Books.csv', dtype={
            'ISBN': str,
            'Book-Title': str,
            'Book-Author': str,
            'Year-Of-Publication': 'object',  # Mixed types handled
            'Publisher': str,
            'Image-URL-S': str,
            'Image-URL-M': str,
            'Image-URL-L': str
            })

            # Clean Year-Of-Publication column
            books['Year-Of-Publication'] = books['Year-Of-Publication'].apply(
            lambda x: x if str(x).isdigit() else 'Unknown'
            )

            # Convert numeric years to integers if needed
            books['Year-Of-Publication'] = books['Year-Of-Publication'].replace('Unknown', 0).astype(int)

     Hasil dari perhitungan adalah :
   
    | Dataset            | Original Shape      | Prepared Shape      |
    |--------------------|---------------------|---------------------|
    | Books              | (271,360, 8)       | (271,360, 8)       |
    | Users              | (278,858, 3)       | (168,096, 3)       |
    | Ratings            | (1,149,780, 3)     | (1,149,780, 3)     |
 

2. Pembersihan Data

      a. Cek Nilai Kosong

                 books.isnull().sum(), ratings.isnull().sum(), users.isnull().sum()

      - **Fungsi**  : Mengecek jumlah nilai kosong (missing values) di setiap kolom dari tiga dataset utama: books, ratings, dan users.
      - **Manfaat** : Dengan mengetahui nilai kosong, kita dapat merencanakan bagaimana menangani data yang hilang agar dataset tetap relevan dan bersih.
        
      b. Mengisi Missing Value di kolong `Book-Author` dan `Publisher`. Kode ini bertujuan untuk membersihkan dataset dengan mengisi nilai yang hilang pada beberapa kolom, menghapus entri duplikat, serta menghapus pengguna dengan data yang tidak lengkap (seperti usia yang hilang). Pada akhirnya, ukuran dataset yang telah diproses dibandingkan dengan dataset asli untuk memastikan langkah pembersihan dilakukan dengan benar tanpa kehilangan data yang terlalu banyak.

      c. Menggabungkan data
      Penggabungkan (merge) dua dataset: ratings (berisi informasi tentang penilaian buku oleh pengguna).
books (berisi detail buku seperti judul, penulis, dan penerbit).Penggabungan dilakukan berdasarkan kolom ISBN, yang bertindak sebagai identifier unik untuk setiap buku.

      Hanya data yang memiliki nilai yang cocok di kedua tabel pada kolom ISBN yang akan disertakan dalam dataset gabungan. Hal ini menghasilkan dataset baru bernama `ratings_with_name`: yang berisi data penilaian dari ratings (seperti `User-ID` dan `Book-Rating`).
Ditambah dengan informasi tambahan dari books (seperti `Book-Title`, `Book-Author`, `Publisher`, dan `gambar buku`).
      
            # Merging ratings with book information
            ratings_with_name = ratings.merge(books, on='ISBN')
     
# Modeling
---
Setelah dilakukan pra-pemrosesan pada dataset, langkah selanjutnya adalah *modeling* terhadap data. Pada tahap ini Model machine learning yang digunakan pada sistem rekomendasi ini adalah model _Collaborative filtering_ dengan _simlarity measure_ yang digunakan adalah _Cosine Similarity_.. 

_Collaborative Filtering_ (CF) adalah salah satu teknik dalam sistem rekomendasi yang menggunakan data perilaku pengguna untuk memberikan rekomendasi. Prinsip utamanya adalah memanfaatkan pola interaksi pengguna dengan item (misalnya buku, film, atau produk) untuk menyarankan item baru berdasarkan preferensi serupa. Pendekatan yang digunakan yaitu _Item-Based Collaborative Filtering_ yang fokus pada kesamaan antar item berdasarkan pola penilaian pengguna.

**Keuntungan** :
     _Personalisasi_: Rekomendasi disesuaikan dengan preferensi pengguna.
     _Efisiensi_: Dapat digunakan tanpa informasi spesifik tentang item (hanya membutuhkan data penilaian).
     
**Kekurangan** :
    _Cold-Start Problem_: Kesulitan dalam memberikan rekomendasi untuk pengguna atau item baru tanpa data interaksi.
    _Sparsity_: Jika data interaksi sangat jarang, kualitas rekomendasi bisa menurun.

Sedangkan _cosine similarity_ adalah salah satu teknik mengukur kesamaan yang bekerja dengan mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama dengan menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai _cosine similarity_.
cara kerja dari fungsi *cosine similiraty* yaitu dengan melakukan perhitungan yang sering digunakan untuk menghitung kemiripan diantara item-item [[10]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748). Secara umum, fungsi similarity adalah fungsi yang menerima dua buah obyek berupa bilangan riil (0 dan 1) dan mengembalikan nilai kemiripan (similarity) antara kedua obyek tersebut berupa bilangan riil. Cosine similarity merupakan salah satu metode pengukuran kemiripan yang populer. Metode ini digunakan untuk menghitung nilai kosinus sudut antara dua vektor dan biasanya digunakan untuk mengukur kemiripan antara dua teks/dokumen. Fungsi cosine similarity antara item A dan item B ditunjukkan sebagai berikut [[10]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748). 
![68747470733a2f2f692e6962622e636f2f744a58465a58422f696d6167652e706e67](https://github.com/user-attachments/assets/7f8ccd15-83c0-45de-8322-7e0ec8086e96)

Keterangan:
```
𝑠𝑖𝑚(𝐴, 𝐵) = nilai similaritas dari item A dan item B
𝑛(𝐴) = banyaknya fitur konten item A 
𝑛(𝐵) = banyaknya fitur konten item B 
𝑛(𝐴 ∩ 𝐵)  = banyaknya fitur konten yang terdapat pada item A dan juga terdapat pada item B
```
Jika kedua objek memiliki nilai similaritas 1, maka kedua objek dikatakan identik dan sebaliknya. Semakin besar hasil dari fungsi similarity, maka kedua objek yang dievaluasi dianggap semakin mirip dan sebaliknya. 

Tujuan akhir dari perhitungan ini adalah memfilter data ratings berdasarkan dua kriteria utama ; yaitu `pengguna yang aktif` memberikan banyak rating (lebih dari 150 buku) dan `buku yang populer` (telah dirating oleh setidaknya 50 pengguna).

Tahapan yang dilakukan adalah :
1. Menghitung jumlah rating per pengguna

         user_rating_counts = ratings_with_name.groupby('User-ID').size()

   
2. Memilih pengguna aktif

        imp_users = user_rating_counts[user_rating_counts > 150].index

3. Menghitung jumlah rating per buku

        book_rating_counts = ratings_with_name.groupby('Book-Title').size()
   
4. Memilih buku populer

       famous_books = book_rating_counts[book_rating_counts >= 50].index

5. Memfilter data rating

       filtered_ratings = ratings_with_name[
       (ratings_with_name['User-ID'].isin(imp_users)) & 
       (ratings_with_name['Book-Title'].isin(famous_books))]
   
7. Membuat pivot table

       # Create a pivot table with Users on rows, Books on columns, and ratings as values
       pivot_table = filtered_ratings.pivot_table(index='Book-Title', columns='User-ID', values='Book-Rating', aggfunc='mean')
       pivot_table.fillna(0, inplace=True)

8. Membuat model kesamaan (_SImiliarity_)

        # Compute cosine similarity for the books
        similarity_scores = cosine_similarity(pivot_table)
   
9. Fungsi Rekomendasi
   Fungsi dirancang untuk merekomendasikan buku kepada pengguna berdasarkan content-based filtering, dengan memanfaatkan skor kesamaan antar buku. Pendekatan ini sangat berguna untuk sistem rekomendasi buku yang dipersonalisasi. 

Parameter penting yang dipakai dalam fungsi ini adalah : 

   - `pivot_table`: Kemungkinan merupakan tabel pivot yang menunjukkan hubungan antara pengguna dan buku berdasarkan rating mereka. Dalam tabel ini, baris mewakili buku, sementara kolom mewakili pengguna.

   - `similarity_scores`: Matriks yang sudah dihitung sebelumnya (misalnya, menggunakan cosine similarity) yang menyimpan nilai kesamaan antar buku.

10. Penggunaan Model

    Fungsi akan mencari buku "Lord of the Flies" dalam dataset. Mengambil skor kesamaan dari matriks kesamaan (similarity_scores) untuk buku tersebut. Menyortir daftar buku berdasarkan skor kesamaan tertinggi. Mengembalikan daftar 10 buku yang paling mirip dengan "Lord of the Flies", termasuk informasi detail seperti judul, penulis, URL gambar, dan skor kesamaan.
    
         recommended_books = recommend('Lord of the Flies', top_n=10)


Berikut _top_-10 _recommemdation_ berdasarkan genre dari judul buku "*Lord of the Flies*"

| Title                                  | Author               | Similarity |
|----------------------------------------|----------------------|------------|
| Death of A Salesman                   | Arthur Miller         | 0.23       |
| 1984                                   | George Orwell        | 0.22       |
| Midnight in the Garden of Good and Evil| John Berendt         | 0.22       |
| Stand                                  | Stephen King         | 0.20       |
| Fight Club                             | Chuck Palahniuk      | 0.19       |
| The Color Purple                       | Alice Walker         | 0.19       |
| Roll of Thunder, Hear My Cry           | Mildred D. Taylor    | 0.18       |
| The Catcher in the Rye                 | J.D. Salinger        | 0.18       |
| To Kill a Mockingbird                  | Harper Lee           | 0.18       |
| Animal Farm                            | George Orwell        | 0.18       |


Dengan hasil yang diberikan di atas berdasarkan judul buku "Lord of the Flies" .

# Evaluation
---
Pada proyek ini, Metric yang digunakan pada sistem rekomendasi judul film berdasarkan genre adalah accuracy precision, recall dan f1-score. Precision adalah metrik yang membandingkan rasio prediksi benar atau positif dengan keseluruhan hasil yang diprediksi positif dengan rumus.

$$\ Precission=TP/(TP+FP)$$
~~~
keterangan:
TP = True Positif (prediksi positif dan hal tersebut benar)
FP = False Positif (prediksi positif dan hal tersebut salah)
~~~

Perhitungan Recall yaitu ; 

$$\ Recall = TP/(TP+FN)$$
~~~
keterangan:
Precision = 
Recall = False Negative (prediksi negative dan hal tersebut salah)
~~~

Perhitungan F1-Score

$$\ F1 = 2* Precision * Recall/(Precision + Recall)$$
~~~
keterangan:
TP = True Positif (prediksi positif dan hal tersebut benar)
FN = False Negative (prediksi negative dan hal tersebut salah)
~~~

Penjelasa: 
`True Positives` (TP): Buku yang benar-benar direkomendasikan dan memang relevan (ada dalam daftar rating yang sebenarnya).
TP dihitung dengan menghitung jumlah buku yang ada di kedua set (aktual dan yang diprediksi).

`False Positives` (FP): Buku yang direkomendasikan, namun tidak relevan (ada di set prediksi, tetapi tidak ada di set aktual). FP dihitung dengan mencari buku-buku yang ada di set prediksi tetapi tidak ada di set aktual.

`False Negatives` (FN): Buku yang relevan, namun tidak direkomendasikan (ada di set aktual, tetapi tidak ada di set prediksi). FN dihitung dengan mencari buku-buku yang ada di set aktual tetapi tidak ada di set prediksi.


Dari output tersebut dihitung accuracy precision nya adalah
```
Precision: 0.50, Recall: 0.67, F1-Score: 0.57
True Positives: 3, False Positives: 3, False Negatives: 2

```
**Precision (0.50)**:

*Precision* mengukur seberapa tepat rekomendasi yang diberikan. Dalam konteks ini, precision 0.50 berarti bahwa setengah dari buku yang direkomendasikan benar-benar relevan dengan preferensi pengguna. Dengan kata lain, dari 6 buku yang direkomendasikan (3 TP + 3 FP), hanya 3 buku yang relevan.

**Recall (0.67)**:

*Recall* mengukur seberapa banyak buku yang seharusnya direkomendasikan (relevan) berhasil ditemukan dan direkomendasikan. Recall 0.67 berarti bahwa 67% dari buku relevan yang seharusnya direkomendasikan telah berhasil ditemukan dan disarankan oleh sistem. Dari 5 buku relevan yang ada (3 TP + 2 FN), 3 di antaranya berhasil direkomendasikan.

**F1-Score (0.57)**:

*F1-Score* adalah rata-rata harmonik antara precision dan recall. F1-Score 0.57 menunjukkan bahwa sistem memiliki keseimbangan yang cukup antara precision dan recall. Skor ini menunjukkan kinerja yang moderat, dengan ruang untuk perbaikan di kedua metrik tersebut.
True Positives (TP = 3):

**Dampak Terhadap Business Understanding**

1. Precision (0.50)
Precision yang lebih rendah (0.50) menunjukkan bahwa setengah dari rekomendasi yang diberikan kepada pengguna tidak relevan, karena ada banyak False Positives (rekomendasi yang tidak sesuai dengan preferensi pengguna). Hal ini bisa menurunkan kepuasan pelanggan karena mereka mendapatkan banyak rekomendasi yang tidak mereka inginkan atau butuhkan.

2. Recall (0.67)
Recall yang lebih tinggi (0.67) menunjukkan bahwa model mampu menangkap sebagian besar item yang relevan dari seluruh actual ratings. Ini berarti meskipun ada beberapa rekomendasi yang salah, sistem masih berhasil mencakup banyak item yang benar-benar relevan bagi pengguna.

3. F1-Score (0.57)
F1-Score yang moderat (0.57) menunjukkan adanya kompromi antara precision dan recall. Meskipun model memberikan beberapa rekomendasi yang relevan, ada juga kekurangan dalam hal menghindari false positives dan false negatives.

 

**Dampak pada Business**:

**Pengalaman Pengguna**: Hasil ini menunjukkan bahwa pengalaman pengguna masih bisa ditingkatkan. Precision yang lebih rendah dapat menyebabkan frustrasi jika pengguna menerima terlalu banyak rekomendasi yang tidak sesuai. Oleh karena itu, bisnis perlu memperbaiki model untuk meningkatkan relevansi rekomendasi.

**Keputusan Pengelolaan Produk**: Bisnis dapat memutuskan untuk mengoptimalkan algoritma rekomendasi untuk memperbaiki algoritma filtering atau menggunakan data yang lebih banyak dan lebih baik untuk meningkatkan akurasi rekomendasi.

**Keuntungan Finansial**: Dengan meningkatkan precision dan recall, perusahaan dapat meningkatkan peluang untuk penjualan dan monetisasi produk yang lebih relevan, serta meningkatkan loyalitas pelanggan.

Secara keseluruhan, evaluasi metrik ini memberi wawasan yang jelas tentang kekuatan dan kelemahan model rekomendasi. Dengan memperbaiki precision dan recall, perusahaan dapat menciptakan pengalaman yang lebih baik untuk pengguna dan mendorong hasil bisnis yang lebih optimal.   



## Referensi
---
- [1] Grand View Research. (n.d.). Books market size, share & trends analysis report. Retrieved from https://www.grandviewresearch.com/industry-analysis/books-market

- [2] Wiley Online Library. (2023). A novel book recommendation system using advanced techniques. International Journal of Intelligent Systems. Retrieved from https://onlinelibrary.wiley.com/doi/10.1155/2023/1514801

- [3] McFarlane, A. (2003). The impact of technology on reading habits. Journal of Educational Computing Research, 29(3). Retrieved from https://www.tandfonline.com/doi/abs/10.1080/14759390300200146

- [4] The Paris Review. (2019). Reading in the age of constant distraction. Retrieved from https://www.theparisreview.org/blog/2019/02/08/reading-in-the-age-of-constant-distraction/

- [5] Invisible Mentor. (n.d.). The art of reading: Francis Bacon's wisdom on consuming books. Retrieved from https://theinvisiblementor.com/the-art-of-reading-francis-bacons-wisdom-on-consuming-books/

- [6] Interact. (n.d.). Information overload: Why it matters and how to combat it. Retrieved from https://www.Interact.org/literature/article/information-overload-whyit-matters-and-how-to-combat-it

- [7] IEEE Xplore. (2015). A study on advanced recommender systems. Retrieved from https://ieeexplore.ieee.org/document/7176109

- [8] ACM Digital Library. (2023). The future of collaborative filtering in recommendation systems. Retrieved from https://dl.acm.org/doi/10.1145/3639233.3639335

- [9] Google Developers. (n.d.). Collaborative filtering basics. Retrieved from https://developers.google.com/machine-learning/recommendation/collaborative/basics?hl=id

- [10] (https://jurnal.uns.ac.id/itsmart/article/download/35008/27748). 
![68747470733a2f2f692e6962622e636f2f744a58465a58422f696d6167652e706e67](https://github.com/user-attachments/assets/7f8ccd15-83c0-45de-8322-7e0ec8086e96)
---Ini adalah bagian akhir laporan---
