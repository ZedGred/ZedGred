# Laporan Proyek Machine Learning - Pebiyan Firmansyah 

## Project overview 
Pada saat ini film telah menjadi salah satu media hiburan dalam mengkomunikasikan pesan, informasi, atau pendapat, yang bermafaat bagi banyak orang[1]. Judul film yang telah banyak beredar dapat membuat masyarakat cenderung kesulitan untuk menemukan film yang mereka inginkan, maka dibutuhkanlah sebuah rekomendasi film[1].

Sistem rekomendasi telah dimanfaatkan sebagai strategi yang efektif untuk dapat mengelola banyaknya informasi yang tersedia dan memberikan rekomendasi suatu item sesuai dengan keinginan pengguna[2]. 

Berbagai macam industri seperti *e-commerce, streaming video* hingga penyedia layanan film telah menggunakan sistem rekomendasi untuk meningkatkan produktifitas dan efisiensi dalam mengembangkan sistem sehingga memberikan layanan terbaik kepada konsumen[2].

## Business Understanding

### Problem Statements
- Bagaimana cara menyiapkan data agar dapat digunakan untuk membuat model?
- Bagaimana cara model dapat memberikan rekomendasi yang sesuai untuk pengguna?
### Goals
- Melakukan menyiapkan data agar model dapat memberikan rekomendasi yang sesuai untuk pengguna.
- Membuat  model yang dapat memberikan rekomendasi berdasarkan data yang dimiliki pengguna.

### Solution Approach
- Menggunakan model *content based filtering* untuk merekomendasikan film berdasarkan genre yang pernah ditonton oleh pengguna.
- Menggunakan model *collaborative filtering* untuk merekomendasikan film berdasarkan rating yang diperoleh dari pengguna lain.

## Data Understanding
Data yang dipakai untuk membuat model adalah *Movies & Ratings for Recommendation System*.Dataset terbagi menjadi 2 *file* yaitu *movies.csv* yang berisi 9742 sampel dan *ratings.csv* yang berisi 100836.[Kaggle](https://www.kaggle.com/datasets/nicoletacilibiu/movies-and-ratings-for-recommendation-system/download?datasetVersionNumber=1)

Berikut adalah informasi deskripsi statistik :

|index|movieId|title|genres|
|---|---|---|---|
|0|1|Toy Story \(1995\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|
|1|2|Jumanji \(1995\)|Adventure&#124;Children&#124;Fantasy|
|2|3|Grumpier Old Men \(1995\)|Comedy&#124;Romance|
|3|4|Waiting to Exhale \(1995\)|Comedy&#124;Drama&#124;Romance|
|4|5|Father of the Bride Part II \(1995\)|Comedy|

**Tabel 1.isi *dataset file movie***
Pada Tabel 1,Berisi sebagian informasi tentang *title,movieId dan genres* pada *dataset movie*.

|index|userId|movieId|rating|timestamp|
|---|---|---|---|---|
|count|100836\.0|100836\.0|100836\.0|100836\.0|
|mean|326\.1|19435\.3|3\.5|1205946087\.4|
|std|182\.6|35531\.0|1\.0|216261036\.0|
|min|1\.0|1\.0|0\.5|828124615\.0|
|25%|177\.0|1199\.0|3\.0|1019123866\.0|
|50%|325\.0|2991\.0|3\.5|1186086662\.0|
|75%|477\.0|8122\.0|4\.0|1435994144\.5|
|max|610\.0|193609\.0|5\.0|1537799250\.0|

**Tabel 2.Deskripsi *userId,movieId,rating dan	timestamp.***
Pada Tabel 2,berisi informasi tentang *mean*(rata-rata) ,data terkecil hingga terbesar pada variabel *userId,movieId,rating dan timestamp.*
### Variabel-variabel pada dataset Movies & Ratings for Recommendation System adalah sebagai berikut:

**File Movie**
- *movieId* = *id* pada setiap *movie*
- *title* = judul nama *movie*
- *genres* = jenis genre movie(action,adventure,animation,children,comedy,crime dll)

**File Rating**
- *userId* = *id* untuk setiap pengguna
- *movieId* = *id* untuk setiap *movie*
- *rating* =  penilaian *movie* yang di berikan oleh pengguna
- *timestamp* = stempel waktu ketika pengguna memberikan penilaian.

### Visualisasi pada dataset
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(6).png?raw=true)

**Gambar 1.Jumlah data *rating.***
Pada Gambar 1,sebagian besar pengguna memberikan *rating* 4.0 yang menunjukan rata-rata pengguna puas dengan *movie* yang mereka tonton.

## Data Preparation
### Content based filtering 
- Menemukan representasi fitur penting dari setiap Genre *movie* menggunakan 
*TfidfVectorizer* pada *library sklearn*.
- Merubah hasil dari data yang di rubah dengan *TfidfVectorizer* menjadi metrik dengan *todense* agar dapat digunakan untuk membuat model.

### Collaborative filtering
- menghapus variabel timstamp karena tidak memiliki informasi yang relevan untuk memberikan rekomendas.
- mengubah data menjadi *list* agar data dapat digunakan untuk disandikan (*endcode*).
- Melakukan *encode* dengan *enumarate* dan memasukan hasil endcode dengan *mapping* sehingga data dapat digunakan untuk melatih model.
- membuat variabel *min,max*,jumlah data *movie* dan *user* pada data dan mengubah data menjadi tipe *float* agar data dapat di olah dengan mudah oleh model.
- Mengacak data dengan *sample* agar distribusi ketika pembagian data menjadi *random*.
- Menentukan variabel x dan y pada data dan melakukan normalisasi pada data y dengan skala 0 sampai 100 berdasarkan *min* dan *max* pada data agar data dapat mudah diproses dengan mudah oleh model.
- Membagi data menjadi 0.8 untuk data train dan test 0.2 dengan mengalikan 0.8 pada jumlah data lalu mencarinya dengan *index.*

## Modeling and Result
### Model based filtering
*Model content-based filtering* adalah sistem rekomendasi dan analisis data yang berfokus pada karakteristik atau konten dari *item-item* yang ingin direkomendasikan untuk pengguna.
**Berikut hasil model yang merekomendasikan dari *Toy Story* (1995) :**
|index|title|genres|
|---|---|---|
|0|The Good Dinosaur \(2015\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|
|1|Adventures of Rocky and Bullwinkle, The \(2000\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|
|2|Moana \(2016\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|
|3|Wild, The \(2006\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|
|4|Emperor's New Groove, The \(2000\)|Adventure&#124;Animation&#124;Children&#124;Comedy&#124;Fantasy|

**Tabel 3.hasil rekomendasi *content based filtering.***

Metode yang digunakan:

**TfidfVectorizer**
*TfidfVectorizer* adalah metode yang digunakan untuk mengubah teks menjadi angka yang dapat diproses oleh algoritma pembelajaran mesin. Ini mengukur seberapa penting sebuah kata dalam dokumen dalam kumpulan data.
Parameter:

- *input: ‘content’ (default)*,Jenis input yang diharapkan; bisa berupa konten string atau *byte*.
- *encoding: ‘utf-8’(default)*,*Encoding* yang digunakan untuk mendekode *byte* menjadi *string.*
- *decode_error: ‘strict’(default)*,Instruksi jika terdapat *byte* yang tidak sesuai dengan *encoding* yang diberikan.
- *strip_accents: None(default)*,Menghapus aksen dan normalisasi karakter lainnya selama tahap *preprocessing.*
- *lowercase: True(default)*,Mengubah semua karakter menjadi huruf kecil sebelum *tokenisasi*.
- *preprocessor: None(default)*,Fungsi untuk menggantikan tahap *preprocessing* sambil mempertahankan *tokenisasi* dan pembuatan *n-gram.*
- *tokenizer: None(default)*,Fungsi untuk menggantikan tahap *tokenisasi.*
- *analyzer: ‘word’(default)*,Menentukan apakah fitur harus dibuat dari *n-gram* kata atau karakter.
- *stop_words: None(default)*,Kata-kata yang akan diabaikan selama proses pembuatan fitur.
- *token_pattern: r"(?u)\\b\\w\\w+\\b"(default)*,Pola *regex* untuk menentukan *token*.
- *ngram_range: (1, 1)(default)*,Rentang *n-gram* yang akan diekstraksi dari teks.
- *max_df: 1.0(default)*,Batas maksimum frekuensi dokumen yang akan diabaikan.
- *min_df: 1(default)*,Batas minimum frekuensi dokumen yang akan diabaikan.
- *max_features: None(default)*,Jumlah maksimum fitur yang akan diekstraksi.
- *vocabulary: None(default)*,Kosakata yang telah ditentukan sebelumnya untuk pembuatan fitur.
- *binary: False(default)*,Jika *True*, semua nilai frekuensi *non-zero* akan diatur menjadi 1.
- *dtype: numpy.float64(default)*,Tipe data dari matriks hasil.
- *norm: ‘l2’(default)*,Norma yang digunakan untuk normalisasi *vektor*.
- *use_idf: True(default)*,Menggunakan *inverse document frequency* untuk menimbang fitur.
- *smooth_idf: True(default)*,Menambahkan satu ke statistik dokumen untuk menghindari pembagian dengan nol.
- *sublinear_tf: False(default)*,Menerapkan skala sublinear untuk frekuensi.

**Cosine simliarty**
*Cosine similarity* adalah metode pengukuran kesamaan antara dua *vektor* dalam ruang *multidimensi*. Ini digunakan untuk mengukur seberapa mirip atau berbedanya dua dokumen atau teks berdasarkan kata-kata yang terdapat di dalamnya.
Parameter:
- X = *tfidfmatrix*,*array* dari bentuk (*n_samples_X, n_features*), data input.
- Y = *None(default),array* dari bentuk (*n_samples_Y, n_features*), data *input*. Jika *None*, *output* akan menjadi kesamaan pasangan antara semua sampel di X.
- *dense_output* = *True(default),True* akan mengembalikan *output* padat bahkan. Jika *False*, outputnya akan disimpan secara *explesit*.

**Fungsi recommender**
Fungsi *recommender* adalah fungsi untuk mencari index yang diberikan untuk mencari rekomendasi.
Parameter :

- Nama_movie = *Toy story* (1995),Nama *movie*.
- *Similarity_data*  = *cosine_sim_dif*,*Dataframe* *mengenai similarity* yang telah kita definisikan sebelumnya.
- *Items* = [*'title','genres'*],Nama dan fitur yang digunakan untuk mendefinisikan kemiripan.
- *k = 5* ,Banyak rekomendasi yang ingin diberikan.

**Kelebihan dan Kekurangan**

Kelebihan:

- Memberikan rekomendasi yang personal dan dapat menjelaskan alasan di balik rekomendasi tersebut.
- Tidak memerlukan data dari pengguna lain, sehingga lebih mudah untuk diskalakan ke jumlah pengguna yang besar.

Kekurangan:

- Kurangnya kemampuan untuk merekomendasikan *item* yang sangat berbeda dari yang telah disukai oleh pengguna.
- Membutuhkan banyak pengetahuan *domain* karena representasi fitur dari item adalah *hand-engineered*, sehingga model hanya akan sebaik fitur yang dirancang.

### Model collaborative filtering 
*Model collaborative filtering* adalah sistem rekomendasi yang memberikan rekomendasi kepada pengguna berdasarkan preferensi atau perilaku pengguna lain yang memiliki kesamaan.
**Berikut adalah hasil model yang merekomendasikan *user* 1:**

memberikan rekomendasi untuk user: 1
movie dengan rating tinggi untuk user
title|genres
|---|---|
|Indiana Jones and the Last Crusade (1989)  |Action&#124;Adventure
|Pink Floyd: The Wall (1982) |Drama&#124;Musical
|Excalibur (1981) | Adventure&#124;Fantasy
|From Russia with Love (1963) | Action&#124;Adventure&#124;Thriller
|M* A* S*H (a.k.a. MASH) (1970) | Comedy&#124;Drama&#124;War

**Tabel 4.Daftar *movie* pernah ditonton  pengguna.**
Pada Tabel 4,berisi daftar *movie* yang diberikan rating tinggi oleh user untuk mencari selera dari pengguna.

**Top 10 rekomendasi movie**
|title|genres|
|---|---|
|Miller's Crossing (1990) | Crime&#124;Drama&#124;Film-Noir&#124;Thriller
|Graduate, The (1967)|Comedy&#124;Drama&#124;Romance|
|Femme Nikita, La (Nikita) (1990) | Action&#124;Crime&#124;Romance&#124;Thriller|
|Bridge on the River Kwai, The (1957) |Adventure&#124;Drama&#124;War
|Chinatown (1974) | Crime&#124;Film-Noir&#124;Mystery&#124;Thriller|
|Shining, The (1980) | Horror|
|Evil Dead II (Dead by Dawn) (1987) | Action&#124;Comedy&#124;Fantasy&#124;Horror
|Great Escape, The (1963) |Action&#124;Adventure&#124;Drama&#124;War
|Back to the Future (1985) |Adventure&#124;Comedy&#124;Sci-Fi|
|Cool Hand Luke (1967) | Drama|

**Tabel 5.Daftar rekomendasi untuk pengguna**
Pada Tabel 5,berisi hasil rekomendasi *movie* yang belum pernah ditonton oleh pengguna.

Metode yang digunakan :

**Arsitektur recommenderNet**
*RecommenderNet* adalah arsitektur jaringan saraf tiruan yang digunakan dalam sistem rekomendasi berbasis *machine learning*.
Parameter :

- num_users=610 ,jumlah pengguna.
- num_movies =9724,jumlah *movie*.
- embedding_size=50 ,ukuran embedding.


**Kelebihan dan Kekurangan**
Kelebihan:
- memberikan rekomendasi yang disesuaikan dengan - preferensi individu pengguna.
- Menggunakan data dari banyak pengguna untuk memberikan rekomendasi yang lebih akurat.

Kekurangan:
- Sulit memberikan rekomendasi untuk pengguna atau item baru yang belum memiliki data peringkat yang cukup.
- Dapat menjadi tantangan ketika jumlah pengguna dan item sangat besar.
## Evaluation
Metrik yang digunakan adalah metrik *precision* untuk *content based filtering* dan *root mean squared error* untuk *collaborative filtering*.
### Precision
*Precision* adalah metrik evaluasi yang mengukur seberapa akurat model dalam memprediksi kelas tertentu.
Hasil :
Dari 5 item yang direkomendasikan,precision sistem memberikan rekomendasi sama sebesar 5/5 persen sehingga *precision* adalah 100 persen.

Formula metrik sebagai berikut:

$$
P = \\frac{TP}{TP + FP} 
$$

TP = Jumlah *True Positive*
FP = Jumlah *False Positive*

Cara kerja metrik *precision*adalah dengan membagi jumlah prediksi positif yang benar.
### Root mean squared error
*Root Mean Square Error* adalah metrik yang digunakan untuk mengukur seberapa baik model prediksi dapat memperkirakan nilai sebenarnya.
Hasil :
Berdasarkan metrik *RMSE* yaitu 0.2011 dan val *RMSE* yaitu 0.2106 memiliki kesalahan yang kecil karena memiliki data berjumlah ribuan.

|epoch|loss|val loss|
|---|---|---|
|1|0.6377|0.6273|
|2|0.6181|0.6208|
|3|0.6127|0.6186|
|4|0.6094|0.6177|
|5|0.6073|0.6171|

**Tabel 6.hasil loss dan val loss pada metrik *rmse.***

Pada Tabel 6.hasil dari loss dan vall loss semakin menurun yang menandakan model tidak mengalami overfitting dan dapat beradaptasi dengan data baru.

Formula metrik sebagai berikut :

$$
RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(P_i - O_i)^2}
$$


P_i  = adalah nilai prediksi ke-i

O_i  = nilai observasi ke-i

n = jumlah total observasi.

*Root Mean Square Error* bekerja dengan mengukur kesalahan prediksi model terhadap nilai sebenarnya.
### Kesimpulan

Tujuan proyek telah tercapai karena model dapat memberikan rekomendasi *movie* yang sesuai berdasarkan genre dan rating yang diberikan oleh pengguna.


## Daftar Referensi 
[1]Fajriansyah M.Adikara P. P.Widodo A. W."Sistem Rekomendasi Film Menggunakan Metode Content Based Filtering".Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer (2021).Tersedia : [tautan](https://www.mendeley.com/catalogue/785e4f4a-edf1-3709-a92e-796c25f949ec)

[2]Muhammad Rizqi Az Zayyad, Arrie Kurniawardhani."Penerapan Metode Deep Learning pada Sistem Rekomendasi Film".AUTOMATA 2 (1), 2021.Tersedia : [tautan](Penerapan Metode Deep Learning pada Sistem Rekomendasi Film)
