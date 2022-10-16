# Laporan Proyek Machine Learning - Alfi Safira Az Zahrah

## Project Overview

![Gambar](https://cdn.idntimes.com/content-images/community/2019/07/1-varjilk3-sl4wmoc95d-dq-daeeedffd3de6d5bd9ae62e010415d01_600x400.jpeg)

Seperti yang kita tahu, buku adalah jendela dunia. Dengan membaca buku kita bisa mengetahui sesuatu yang sebelumnya belum pernah kita ketahui dan pahami. Orang yang memiliki kebiasaan membaca buku terbukti bahwa orang tersebut memiliki wawasan dan pengetahuan yang luas [[1]](https://journal.unhas.ac.id/index.php/jupiter/article/view/1672). Dengan memiliki wawasan dan pengetahuan yang luas tentu akan memudahkan kita untuk menggapai kesuksesan. Dengan berbagai manfaat yang didapat dari kebiasaan membaca, maka penting bagi kita semua untuk membangun kebiasaan membaca buku yang baik.

Saat ini, buku tidak hanya tersedia secara fisik, buku-buku digital dapat dengan sangat mudah diakses oleh siapa saja, kapan saja, dan dimana saja melalui internet, baik melalui _website_ maupun aplikasi. Membangun kebiasaan membaca buku tentu tidak terlepas dari bagaimana seseorang tertarik kepada suatu buku, misal tertarik karena judul bukunya, penulisnya, maupun genre dari sebuah buku. Oleh karena itu, sebuah _website_ maupun aplikasi penyedia buku digital tentulah membutuhkan suatu sistem yang dapat merekomendasikan kepada pengguna (_user_) buku-buku yang sesuai dengan preferensi pengguna. Tidak hanya untuk meningkatkan kepuasan pengguna terhadap _website_ atau aplikasi, sistem rekomendasi ini juga dapat bermanfaat untuk meingkatkan kebiasaan membaca pengguna. -----Mengingat tingkat literasi penduduk negara Indonesia masih tergolong rendah, bahkan menurut survei yang dilakukan oleh _Program for International Student Assessment (PISA)_ yang dirilis oleh _Organization for Economic Co-operation and Development (OECD)_ pada tahun 2019, Indonesia menempati peringkat ke 62 dari 70 negara [[2]](https://bisniskumkm.com/harbuknas-2022-literasi-indonesia-peringkat-ke-62-dari-70-negara/#:~:text=Harbuknas%202022%20%3A%20Literasi%20Indonesia%20Peringkat%20Ke%2D62%20Dari%2070%20negara,-UNESCO%20Menyebut%20indeks), atau dapat disimpulkan bahwa Indonesia masuk ke dalam 10 negara dengan tingkat literasi yang rendah.----

Oleh karena itu, pada proyek ini penulis membuat sebuah sistem rekomendasi yang akan memberikan rekomendasi judul buku menggunakan pendekatan **_Content-Based Filtering_** dan **_Collaborative Filtering_** menggunakan dataset [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) [3] dari kaggle.com.

## Business Understanding
---
### Problem Statements

Berdasarkan latar belakang yang telah diuraikan di atas, maka perumusan masalah yang akan diselesaikan pada proyek ini, diantaranya:
* Bagaimana cara membuat sistem untuk memberikan sejumlah rekomendasi buku berdasarkan nama penulis buku yang pernah dibaca oleh pengguna (_user_)? 
* Bagaimana cara membuat sistem untuk menghasilkan sejumlah rekomendasi judul buku yang sesuai dengan preferensi pengguna (_user_) berdasarkan rating yang telah diberikan sebelumnya?

### Goals

Berikut adalah tujuan dari pernyataan masalah:
- Mengetahui cara membuat sistem untuk memberikan sejumlah rekomendasi buku berdasarkan nama penulis buku yang pernah dibaca oleh pengguna (_user_)
- Mengetahui cara membuat sistem untuk menghasilkan sejumlah rekomendasi judul buku yang sesuai dengan preferensi pengguna (_user_) berdasarkan rating yang telah diberikan sebelumnya

### Solution Approach

Berikut adalah tahapan yang akan dilakukan dalam pembangunan model (_Model Development_) Sistem Rekomendasi, digambarkan pada diagram berikut :

![Tahapan Proyek](https://user-images.githubusercontent.com/90541793/196037010-e73aa596-a57e-43c0-b63b-b66d3a1f0347.PNG)

Gambar 1. Tahapan Proyek

Kemudian, untuk mencapai tujuan, pada proyek ini akan menggunakan 2 pendekatan yakni _Content Based Filtering_ dan _Collaborative Filtering_ :

**Solution Statement**

1. **_Content Based Filtering_**
   * Ide pendekatan ini adalah merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu.

   * Pengembangan model menggunakan pendekatan **_Content-Based Filtering_** ini dilakukan pada proyek ini untuk menghasilkan rekomendasi buku berdasarkan nama penulis buku yang pernah dibaca oleh pengguna (_user_).

2. **_Collaborative Filtering_**
   * Pendekatan ini bergantung pada pendapat komunitas pengguna. Selain itu, ia tidak memerlukan atribut untuk setiap itemnya seperti pada sistem _Content-Based Filtering_

   * Tujuan pengembangan model menggunakan pendekatan **_Collaborative Filtering_** pada proyek ini adalah untuk menghasilkan sejumlah rekomendasi judul buku yang sesuai dengan preferensi pengguna (_user_) berdasarkan rating yang telah diberikan sebelumnya.


## Data Understanding
---
Dataset yang digunakan pada proyek ini yakni _[Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset)_. Dataset ini dikumpulkan oleh Cai-Nicolas Ziegler dalam 4 minggu (Agustus / September 2004) dari komunitas Book-Crossing dengan izin dari Ron Hornbaker, CTO Humankind Systems. Berikut adalah informasi lebih lanjut mengenai dataset tersebut:

Tabel 1. Informasi Dataset
| Jenis | Keterangan |
| -------- | -------- |
| Sumber Dataset | Book Recommendation Dataset : [Kaggle](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) [3] |
| Owner/Collaborator | Möbius |
| Asal Dataset | [Book-Crossing](https://www.bookcrossing.com/?) |
| Lisensi | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |
| Jenis dan Ukuran Berkas | .zip (25 MB) |


Dataset ini terdiri dari 3 files, diantaranya `Books.csv`, `Ratings.csv`, dan `Users.csv`.

**1. Books**

Berikut ini deskripsi variabel-variabel yang terdapat pada file **Books.csv**:

* ISBN : Nomor Buku Standar Internasional (_International Standard Book Number_)
* Book-Title : Judul buku
* Book-Author : Penulis buku
* Year-Of-Publication : Tahun buku dipublikasikan/diterbitkan
* Publisher : Penerbit buku
* Image-URL-S : Tautan gambar sampul buku berukuran kecil (_Small_)
* Image-URL-M : Tautan gambar sampul buku berukuran sedang (_Medium_)
* Image-URL-L : Tautan gambar sampul buku berukuran besar (_Large_)

**2. Ratings**

Berikut ini deskripsi variabel-variabel yang terdapat pada file **Ratings.csv**:

* User-ID : ID pengguna
* ISBN : Nomor Buku Standar Internasional (_International Standard Book Number_)
* Book-Rating : Rating buku menurut pengguna

**3. Users**

Berikut ini deskripsi variabel-variabel yang terdapat pada file **Users.csv**:

* User-ID : ID pengguna
* Age : Usia pengguna
* Location : Lokasi tiap pengguna dengan nilai ibu kota, negara bagian, dan negara serikat

Pada proyek ini dataframe yang akan kita gunakan adalah `Books.csv` dan `Ratings.csv`.

## **Exploratory Data Analysis (EDA)**

**Univariate Data Analysis**

**1. Books**

Mengecek informasi dari dataframe books menggunakan fungsi `info()`. Berikut adalah output nya.

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 271360 entries, 0 to 271359
    Data columns (total 8 columns):

Berdasarkan output di atas, terlihat bahwa dataframe books memiliki 271360 data entri dan terdapat 8 variabel. Berikut informasi masing-masing variabelnya.

Tabel 2. Informasi Variabel Dataframe Books

| # |	Column	| Non-Null Count	| Dtype |
| -------- | -------- | -------- | -------- |
| 0	| ISBN | 39271360 | non-null | object |
| 1 |	Book-Title | 271360 non-null | object |
| 2	| Book-Author	| 271359 non-null	| object |
| 3	| Year-Of-Publication	| 271360 non-null	| object |
| 4	| Publisher |	271358 non-null	| object |
| 5 |	Image-URL-S	| 271360 non-null	| object |
| 6	| Image-URL-M	| 271360 non-null	| object |
| 7	| Image-URL-L	| 271357 non-null	| object |

Selanjutnya kita akan melihat ada berapa banyak entri yang unik dari masing-masing variabel (disini kita akan mengecek hanya beberapa variabel saja) menggunakan fungsi `len()` dan `unique()`. Berikut adalah outputnya.

    Banyak Judul Buku : 242135
    Banyak Nama Penulis : 102024
    Banyak Penerbit : 16808

Kemudian melihat distribusi data variabel `Year of Publication` menggunakan visualisasi data berupa bar.

![Distribusi Data YoP](https://user-images.githubusercontent.com/90541793/196039489-b692dd75-43b7-404d-89e4-e9701a5a6a80.PNG)

Gambar 2. Distribusi Year Of Publication

Dari output di atas dapat terlihat bahwa distribusi data Year of Publication cenderung _right-skewed_.

**2. Ratings**

Mengecek informasi dari dataframe ratings menggunakan fungsi `info()`. Berikut adalah output nya.

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1149780 entries, 0 to 1149779
    Data columns (total 3 columns):

Berdasarkan output di atas, terlihat bahwa dataframe books memiliki 1149780 data entri dan terdapat 3 variabel. Berikut informasi masing-masing variabelnya.

Tabel 3. Informasi Variabel Dataframe Ratings

| # |	Column	| Non-Null Count	| Dtype |
| -------- | -------- | -------- | -------- |
| 0	| User-ID | 1149780 | non-null | int64 |
| 1 |	ISBN | 1149780 non-null | object |
| 2	| Book-Rating	| 1149780 non-null	| int64 |

Selanjutnya kita akan melihat ada berapa banyak entri yang unik dari masing-masing variabel (User-ID dan Book-Rating) menggunakan fungsi `len()` dan `unique()`. Berikut adalah outputnya.

    Banyak User-ID : 105283
    Banyak Rating : 11

Kemudian melihat distribusi data variabel `Book-Rating` menggunakan visualisasi data berupa bar.

![Distribusi Data Rating](https://user-images.githubusercontent.com/90541793/196039958-fbc0aa11-7b6c-4b33-ab64-be20f346c1d6.PNG)

Gambar 3. Distribusi Data Book-Rating

Dari visualisasi di atas dapat terlihat bahwa variabel Book-Rating memiliki skala dari 0 hingga 10 dan rating 0 adalah yang paling banyak diberikan oleh user.

## Data Pre-Processing

---
Pada tahap ini kita akan melakukan penggabungan dataframe `Books.csv` dan `Ratings.csv` agar memudahkan dalam pembuatan model. Penggabungan menggunakan fungsi `merge()`. Berikut adalah outputnya.

    1032345 rows x 10 columns

Berdasarkan output di atas dapat diartikan bahwa setelah digabungkan, kini dataframe kita mempunyai `1032345` baris sampel data dan `10` kolom.

Melihat dari jumlah data pada dataframe yang terbilang banyak yakni 1032345 baris sampel data, maka pada proyek ini hanya akan diambil 100000 baris sampel data saja. Sehingga data yang akan kita gunakan sekarang berjumlah `100000` baris sampel data dan `10` kolom.

## Data Preparation

---
Data preparation merupakan salah satu tahapan yang penting dalam proses pengembangan model machine learning. Pada tahapan ini akan dilakukan proses transformasi pada data sehingga menjadi bentuk yang cocok untuk proses pemodelan.

### **Content Based Filtering**

Berikut tahapan Data Preparation yang dilakukan pada pendekatan ini :

**1. Mengecek dan Menangani Missing Value**

Setelah proses penggabungan menggunakan fungsi `merge`, mari kita cek lagi datanya, apakah ada _missing value_ atau tidak. Pendeteksian _missing value_ dilakukan menggunakan fungsi `isnull()`. Berikut hasil deteksi _missing value_ yang diperoleh:

Tabel 4. Hasil Cek Missing Value
| Variabel |	Jumlah Missing Value	| 
| -------- | -------- | 
| ISBN | 0 |
| book_title | 0 |
| book_author	| 0	|
| year_of_publication	| 0	|
| Publisher |	0	|
| Image_URL_S	| 0	|
| Image_URL_M	| 0	|
| Image_URL_L	| 0	|
| user_id | 4	|
| book_rating	| 4	|

Dari output di atas terlihat bahwa pada variabel "user_id" dan "book_rating" terdapat 4 _missing value_. Untuk mengatasi _missing value_ kita akan menghapusnya menggunakan fungsi `dropna()` dan menampilkan hasilnya. Berikut outputnya.

    99996 rows x 10 columns

Setelah _missing value_ dihilangkan, kini dataframe kita memiliki `99996` baris sampel data dan `10` kolom.

**2. Mengecek dan Menghapus Data Duplikat**

Dalam sistem rekomendasi yang kita kembangkan, penting untuk memastikan data satu judul buku, satu author (penulis). Tujuannya supaya tidak terjadi dobel atau rangkap.

Pertama kita akan membuat variabel `preparation` untuk menampung dataframe hasil tahap sebelumnya yaitu `ds_clean`. Kemudian kita akan mengurutkan sampel data berdasarkan `book_title`. Berikut cuplikan outputnya.

![Cuplikan Data yg diurutkan Berdasarkan Book_Title](https://user-images.githubusercontent.com/90541793/196041188-55321921-7fbc-4388-a577-68445b5394c0.PNG)

Dari ouput di atas terlihat banyak data judul buku yang memiliki duplikat, sehingga perlu kita hilangkan duplikatnya menggunakan fungsi `drop_duplicates`, kemudian kita tampilkan hasilnya. 

Berikut potongan kode nya :

    # Membuang data duplikat pada variabel preparation
    preparation = preparation.drop_duplicates('book_title')
    preparation

Berikut output nya :

    2228 rows x 10 columns

Setelah dilakukan data cleaning terhadap data yang duplikat kini pada dataframe terdapat `2228` baris sampel data dan `10` kolom.

**3. Mengubah Dataframe menjadi Sebuah List**

Selanjutnya kita perlu mengubah data series menjadi list menggunakan fungsi `tolist()`. 

Berikut cuplikan kodenya :

    book_ISBN = preparation['ISBN'].tolist()
    title = preparation['book_title'].tolist()
    author = preparation['book_author'].tolist()


Tahap berikutnya, kita akan membuat dictionary untuk menentukan pasangan key-value pada data book_ISBN, title, author, book_year_of_publication, dan book_publisher yang telah kita siapkan sebelumnya.

Berikut cuplikan kodenya :

    ds_new = pd.DataFrame({
        'book_ISBN': book_ISBN,
        'title': title,
        'author': author,
        'book_year_of_publication': book_year_of_publication,
        'book_publisher': book_publisher
    })
    ds_new

### **Collaborative Filtering**

Berikut tahapan Data Preparation yang dilakukan pada pendekatan ini :

**1. Melakukan encoding pada fitur `user_id` dan `ISBN` ke dalam indeks integer**

Berikut cuplikan kode untuk encoding fitur `user_id`.

    # Mengubah user_id menjadi list tanpa nilai yang sama
    user_ids = df['user_id'].unique().tolist()
 
    # Melakukan encoding user_id
    user_to_user_encoded = {x: i for i, x in enumerate(user_ids)}

    # Melakukan proses encoding angka ke user_id
    user_encoded_to_user = {i: x for i, x in enumerate(user_ids)}

Begitu juga proses untuk encoding fitur `ISBN`.

**2. Melakukan pemetaan (_mapping_) pada fitur `user_id` dan `ISBN` ke dataframe yang berkaitan**

Berikut cuplikan kode untuk mapping `user_id` ke dataframe user.

    # Mapping user_id ke dataframe user
    df['Users'] = df['user_id'].map(user_to_user_encoded)

Begitu juga proses untuk mapping fitur `ISBN`.

**3. Mengecek jumlah user, jumlah ISBN, dan mengubah nilai rating menjadi float**

* Mengecek data menggunakan fungsi `len()`.
* Mengubah nilai data menggunakan fungsi `astype()`.

Berikut cuplikan outputnya
    
    Jumlah User: 105283, Jumlah ISBN: 340556, Min Rating: 0.0, Max Rating: 10.0

**4. Membagi Data untuk Training dan Validasi**

Proses membagi dataset menjadi data latih (train) dan data uji (test) merupakan hal yang harus dilakukan sebelum membuat model. Proses ini sebaiknya dilakukan di awal sebelum proses lainnya [[4]](https://www.oreilly.com/library/view/hands-on-predictive-analytics/9781789138719/), hal ini bertujuan agar kita tidak mengotori data uji dengan informasi yang kita dapat dari data latih. 

Pada pendekatan ini kita hanya akan menggunakan sejumlah `10000` sampel data dari seluruh dataframe. 

Selanjutnya, kita bagi data train dan validasi dengan komposisi 80:20. Namun sebelumnya, kita perlu melakukan :
* Pemetaan (mapping) data user dan books menjadi satu value terlebih dahulu.
* Buatlah rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training. 

## Modeling
---

Pada proyek ini, pengembangan model dilakukan menggunakan 2 pendekatan, antara lain : 

**1. _Content Based Filtering_**

* Kelebihan:
  * Teknik ini baik dipakai ketika skala pengguna (_user_) yang besar.
  * Teknik ini dapat menemukan ketertarikan spesifik dari seorang pengguna (_user_), dan dapat merekomendasikan item yang jarang disukai orang lain.

* Kekurangan:
  * Karena _meta feature_ yang digunakan kita yang menentukan sendiri, kualitas dari rekomendasi tergantung kualitas dari _meta feature_ itu sendiri.

**2. _Collaborative Filtering_**

* Kelebihan :
  * Tidak memerlukan atribut untuk setiap item pada dataset seperti yang dibutuhkan oleh pendekatan _Content-Based Filtering_

* Kekurangan :
  * Membutuhkan data dari preferensi pengguna, misalnya atribut rating. Jika ada item baru (belum ada rating) maka sistem tidak akan merekomendasikan item tersebut.

### **Model Development dengan _Content Based Filtering_**

**1. Menggunakan TF-IDF Vectorizer**

* Pada pemodelan dengan _Content-Based Filtering_ ini, teknik TF-IDF Vectorizer akan digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap nama penulis buku (author).

* TF-IDF atau _Term Frequency-Inverse Document Frequency_ berfungsi untuk mengukur seberapa penting suatu kata terhadap kata-kata lain yang ada dalam dokumen.

* Penerapannya menggunakan fungsi `TfidfVectorizer()`.

**2. Melakukan fit dan transformasi**

* Selanjutnya, lakukan fit dan transformasi ke dalam bentuk matriks menggunakan fungsi `fit_transform` dan menampilkan hasilnya.

Berikut output nya :
   
    (2228, 2089)

Keterangan output :

Berdasarkan output di atas dapat diartikan bahwa pada tfidf_matrix terdapat 2228 ukuran data dan 2089 nama penulis buku (author).

**3. Menghasilkan vektor tf-idf dalam bentuk matriks**

* Pada tahap ini menggunakan fungsi `todense()`.

Berikut cuplikan outputnya :

    matrix([[0., 0., 0., ..., 0., 0., 0.],
            [0., 0., 0., ..., 0., 0., 0.],
            [0., 0., 0., ..., 0., 0., 0.],
            ...,
            [0., 0., 0., ..., 0., 0., 0.],
            [0., 0., 0., ..., 0., 0., 0.],
            [0., 0., 0., ..., 0., 0., 0.]])

**4. Menghitung derajat kesamaan menggunakan Cosine Similarity**

* Disini, kita menggunakan fungsi `cosine_similarity()` dari library sklearn.

Berikut cuplikan outputnya :

    array([[1., 0., 0., ..., 0., 0., 0.],
           [0., 1., 0., ..., 0., 0., 0.],
           [0., 0., 1., ..., 0., 0., 0.],
           ...,
           [0., 0., 0., ..., 1., 0., 0.],
           [0., 0., 0., ..., 0., 1., 0.],
           [0., 0., 0., ..., 0., 0., 1.]])

Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**5. Melihat matriks kesamaan setiap buku**

Mari kita lihat matriks kesamaan setiap buku dengan menampilkan judul buku dalam 5 sampel kolom (axis = 1) dan 10 sampel baris (axis=0). Berikut cuplikan outputnya : 

![Output Matriks Kesamaan Setiap Buku](https://user-images.githubusercontent.com/90541793/196044376-f6c8e11c-1f7f-4777-87f4-6e9172bd30b9.PNG)

Gambar 4. Tabel Matriks Kesamaan Setiap Buku

**Keterangan :**

Angka 1.0 mengindikasikan bahwa buku pada kolom X (horizontal) memiliki kesamaan dengan buku pada baris Y (vertikal), dan sebaliknya.

**6. Mendapatkan Rekomendasi**

Pada proyek ini kita akan membuat fungsi untuk mendapatkan rekomendasi judul buku berdasarkan nama penulis (author) buku dengan k sebagai jumlah rekomendasi. Dalam fungsi di bawah ini, kita akan mendapatkan 5 rekomendasi.

Kode Fungsi Sistem Rekomendasi :

    def author_recommendations(title, similarity_data=cosine_sim_df, items=data[['title', 'author']], k=5):
      index = similarity_data.loc[:, title].to_numpy().argpartition(range(-1, -k, -1))
      closest = similarity_data.columns[index[-1:-(k+2):-1]]
      closest = closest.drop(title, errors='ignore')
      return pd.DataFrame(closest).merge(items).head(k)

Selanjutnya, mari kita terapkan fungsi di atas untuk mendapatkan rekomendasi.

Sebagai contoh, buku yang sudah dibaca adalah "Deception Point" yang ditulis oleh Dan Brown.

Berikut penerapannya.

    # Mendapatkan rekomendasi judul buku berdasarkan nama penulis (author) dari buku yang berjudul Deception Point
    author_recommendations('Deception Point')

Berikut outputnya :

Tabel 5. Hasil Rekomendasi 

| # |	title	| author	| 
| -------- | -------- | -------- |
| 0	| Angels &amp; Demons | Dan Brown | 
| 1 |	Digital Fortress: A Thriller | Dan Brown |
| 2	| The Da Vinci Code	| Dan Brown	| 
| 3	| Hyperion	| DAN SIMMONS	|
| 4	| Starsong (Tsr Books) |	Dan Parkinson	| 

Berhasil !!!

* Melalui ouput di atas sistem telah memberikan rekomendasi 5 judul buku berdasarkan kata kunci nama author, yakni "Dan".


### **Model Development dengan _Collaborative Filtering_**

Berikut tahapan dalam pengembangan model dengan _Collaborative Filtering_.

**1. Proses Training Model**

* Setelah proses data preparation selesai, kita lanjut pada proses training model.

* Pada tahap ini kita membuat sistem menggunakan `class RecommenderNet` dan melakukan proses embedding

* Kemudian tahap compile model menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation. 

* Latih model menggunakan fungsi `fit()`.

**2. Mendapatkan Rekomendasi**

* Untuk mendapatkan rekomendasi judul buku, pertama kita ambil sampel user secara acak dan definisikan variabel "book_never_read" yang merupakan daftar judul buku yang belum pernah dibaca oleh pengguna.

* Selanjutnya, untuk memperoleh rekomendasi judul, gunakan fungsi `model.predict()` dari library Keras.

* Berikut output hasil rekomendasi dari sistem.

Tabel 6. Hasil Rekomendasi Buku dengan Rating Tinggi dari Pengguna

| Top 10 Book Recommendation |
| -------- |
| Seabiscuit : LAURA HILLENBRAND | 
| Bridget Jones's Diary : Helen Fielding |
| Four Blind Mice : James Patterson	|
| Life of Pi : Yann Martel |
| Left Behind: A Novel of the Earth's Last Days (Left Behind No. 1) : Tim Lahaye |
| OLD MAN AND THE SEA : Ernest Hemingway |
| The Unbearable Lightness of Being : Milan Kundera |
| Daughter of Fortune : A Novel (Oprah's Book Club (Hardcover)) : Isabel Allende |
| A Cup of Tea (Ballantine Reader's Circle) : Amy Ephron |
| Jemima J: A Novel About Ugly Ducklings and Swans : Jane Green |



* Melalui ouput di atas sistem telah memberikan rekomendasi 10 judul buku sesuai preferensi pengguna dan yang memiliki rating tertinggi berdasarkan penilaian yang diberikan oleh pengguna. 


## Evaluation
---
Setelah melalui tahap pengembangan model dan pengujian, serta mencoba mendapatkan rekomendasi dari model yang telah dibuat, pada tahap ini akan dilakukan evaluasi dari hasil yang didapatkan. 

**1. Content Based Filtering**

Melihat dari hasil rekomendasi yang diberikan, sistem telah memberikan rekomendasi buku berdasarkan kata kunci nama penulis (_author_) dari buku yang pernah dibaca oleh pengguna (_user_). Hal ini dapat diartikan bahwa sistem rekomendasi sudah bisa memberikan rekomendasi sesuai dengan tujuan dari pengembangan sistem, yakni untuk menghasilkan rekomendasi buku berdasarkan nama penulis buku yang pernah dibaca oleh pengguna (_user_).

**2. Collaborative Filtering**

Untuk evaluasi model yang dibangun dengan pendekatan ini yakni menggunakan metrik evaluasi _Root Mean Squared Error_ (RMSE). RMSE memberi gambaran tentang seberapa banyak kesalahan dalam prediksi yang dibuat oleh sistem. Tujuannya tentu saja untuk mendapatkan eror atau tingkat kesalahan seminimal mungkin. 

---

**Formula :**

![rumus RMSE](https://user-images.githubusercontent.com/90541793/196046772-545a568a-e824-468b-a593-6850c1d9ec2f.PNG)

Keterangan :

At = Nilai data aktual

Ft = Nilai hasil peramalan (_forecasting_)

N = Banyaknya data

**Cara Kerja :**

RMSE dihitung dengan mengkuadratkan error (prediksi " observasi) dibagi dengan jumlah data (= rata-rata), lalu diakarkan.

Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

---

**Hasil Visualisasi Metrik**

Untuk melihat visualisasi proses training model, mari kita plot metrik evaluasi dengan matplotlib. Berikut hasil visualisasi model.

![Hasil Visualisasi Metrik](https://user-images.githubusercontent.com/90541793/196047133-7282d2cd-fbf5-42c9-8097-b221536549a6.PNG)

Gambar 5. Visualisasi Metrik RMSE

Dari hasil plot metrik, dapat diartikan sbb :
* Proses training model untuk data train cukup smooth walaupun pada epoch awal nilai error sempat naik, tapi kemudian menurun secara signifikan hingga nilai error akhir sebesar `0.3985`.
* Sedangkan pada data validasi, nilai error tidak menurun secara signifikan, dan error akhirnya sebesar 0.4281.
* Walaupun nilai error yang didapat cukup baik untuk sistem rekomendasi, namun model ini masih _underfitting_.

## Daftar Referensi
---

[1] Saleh, Tawakkal. (2014). Pentingnya Membaca dan Menggunakan Perpustakaan Dalam Mengubah Kehidupan Manusia. _JUPITER_. Vol. 13 No.1.

[2] Ilham, Bahrul U. (2022). Harbuknas 2022: Literasi Indonesia Peringkat Ke-62 Dari 70 Negara. Retrieved [16 Oktober 2022] from : [Link](https://bisniskumkm.com/harbuknas-2022-literasi-indonesia-peringkat-ke-62-dari-70-negara/#:~:text=Harbuknas%202022%20%3A%20Literasi%20Indonesia%20Peringkat%20Ke%2D62%20Dari%2070%20negara,-UNESCO%20Menyebut%20indeks)

[3] [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) : Collected by Cai-Nicolas Ziegler in a 4-week crawl (August / September 2004) from the Book-Crossing community with kind permission from Ron Hornbaker, CTO of Humankind Systems. Contains 278,858 users (anonymized but with demographic information) providing 1,149,780 ratings (explicit / implicit) about 271,379 books.
