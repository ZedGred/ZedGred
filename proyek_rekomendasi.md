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
- Menggunkan model *content based filtering* untuk merekomendasikan film berdasarkan genre yang pernah ditonton oleh pengguna.
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
TfidfVectorizer pada *library sklearn*.
- Merubah hasil dari data yang di rubah dengan TfidfVectorizer menjadi metrik dengan *todense* agar dapat digunakan untuk membuat model.

### Collaborative filtering
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

Kelebihan:

- Memberikan rekomendasi yang personal dan dapat menjelaskan alasan di balik rekomendasi tersebut.
- Tidak memerlukan data dari pengguna lain, sehingga lebih mudah untuk diskalakan ke jumlah pengguna yang besar.

Kekurangan:

- Kurangnya kemampuan untuk merekomendasikan *item* yang sangat berbeda dari yang telah disukai oleh pengguna.
- Membutuhkan banyak pengetahuan *domain* karena representasi fitur dari item adalah *hand-engineered*, sehingga model hanya akan sebaik fitur yang dirancang.

### Model collaborative filtering 
*Model collaborative filtering* adalah sistem rekomendasi yang memberikan rekomendasi kepada pengguna berdasarkan preferensi atau perilaku pengguna lain yang memiliki kesamaan.Model yang digunakan adalah model *RecommenderNet*.Sebuah arsitektur jaringan saraf tiruan yang digunakan dalam sistem rekomendasi berbasis *machine learning*.
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

Kelebihan:
- memberikan rekomendasi yang disesuaikan dengan - preferensi individu pengguna.
- Menggunakan data dari banyak pengguna untuk memberikan rekomendasi yang lebih akurat.

Kekurangan:
- Sulit memberikan rekomendasi untuk pengguna atau item baru yang belum memiliki data peringkat yang cukup.
- Dapat menjadi tantangan ketika jumlah pengguna dan item sangat besar.
## Evaluation
Metrik yang digunakan adalah metrik *cosine simliarty* untuk *content based filtering* dan *root mean squared error* untuk *collaborative filtering*.
### Cosine simliarty 
Cosine similarity adalah metrik yang mengukur kemiripan antara dua vektor non-nol dalam ruang berdimensi-n dengan menghitung kosinus sudut di antara mereka.
Formula metrik sebagai berikut :


$$
\text{similarity} (\mathbf{A}, \mathbf{B}) = \cos (\theta) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\|\|\mathbf{B}\|}
$$


Cosine similarity bekerja dengan mengukur sudut cosinus antara dua vektor dalam ruang multidimensi.
### Root mean squared error
*Root Mean Square Error* adalah metrik yang digunakan untuk mengukur seberapa baik model prediksi dapat memperkirakan nilai sebenarnya.


$$
RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(P_i - O_i)^2}
$$


P_i  = adalah nilai prediksi ke-i

O_i  = nilai observasi ke-i

n = jumlah total observasi.

*Root Mean Square Error* bekerja dengan mengukur kesalahan prediksi model terhadap nilai sebenarnya.
### Kesimpulan
Berdasarkan Tabel 6.metrik *RMSE* yaitu 0.2011 dan val *RMSE* yaitu 0.2106 memiliki kesalahan yang kecil karena memiliki data berjumlah ribuan.

|epoch|loss|val loss|
|---|---|---|
|1|0.6377|0.6273|
|2|0.6181|0.6208|
|3|0.6127|0.6186|
|4|0.6094|0.6177|
|5|0.6073|0.6171|

**Tabel 6.hasil loss dan val loss pada metrik *rame.***

Pada Tabel 6.hasil dari loss dan vall loss semakin menurun yang menandakan model tidak mengalami overfitting dan dapat beradaptasi dengan data baru.

Tujuan proyek telah tercapai karena model dapat memberikan rekomendasi *movie* yang sesuai berdasarkan genre dan rating yang diberikan oleh pengguna. 


## Daftar Referensi 
[1]Fajriansyah M.Adikara P. P.Widodo A. W."Sistem Rekomendasi Film Menggunakan Metode Content Based Filtering".Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer (2021).Tersedia : [tautan](https://www.mendeley.com/catalogue/785e4f4a-edf1-3709-a92e-796c25f949ec)

[2]Muhammad Rizqi Az Zayyad, Arrie Kurniawardhani."Penerapan Metode Deep Learning pada Sistem Rekomendasi Film".AUTOMATA 2 (1), 2021.Tersedia : [tautan](Penerapan Metode Deep Learning pada Sistem Rekomendasi Film)
