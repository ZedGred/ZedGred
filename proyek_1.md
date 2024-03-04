# Laporan Proyek Machine Learning - Pebiyan Firmansyah 

## Domain Proyek

Obesitas merupakan penyakit kronis dan multi faktorial dan juga disebut penyakit inflamasi kronik yang ditandai dengan peningkatan total lemak tubuh[1].

Dampak obesitas terhadap kesehatan masyarakat meliputi percepatan proses penuaan, gangguan kecerdasan, resistensi insulin, kanker, osteoatritis, kolelithiasis, dan kematian pada usia muda.Karena penyakit ini merupakan penyakit kronis yang memiliki implikasi kesehatan yang besar, pencegahan, deteksi, dan penanganan tepat waktu sangat penting[1].

Prevalensi obesitas pada masa kanak-kanak telah meningkat secara signifikan dan saat ini merupakan salah satu masalah kesehatan masyarakat yang paling serius[3].

Prediksi obesitas adalah proses untuk mengestimasi tingkat obesitas seseorang berdasarkan faktor-faktor yang mempengaruhinya.Prediksi obesitas dapat dilakukan dengan menggunakan berbagai metode, seperti regresi dan klasifikasi.

Aplikasi menggunakan fungsi prediksi untuk memperkirakan kategori obesitas pengguna berdasarkan data yang dimasukkan seperti BMI, berat, tinggi, usia, dan jenis kelamin[4].

*As consequence of its social and economic implications, obesity has become one of the main threats to public health and to maintaining the balance in health systems[2].* :  [Obesity and overweight](https://www.mendeley.com/catalogue/7ecbf93d-afbf-3501-8932-91e65c9f27ce)

## Business Understanding

Obesitas saat ini menjadi permasalahan dunia bahkan *WHO (World Health Organization)* mendeklarasikan sebagai *epidemic global*. Jumlah penderita obesitas di dunia selalu mengalami peningkatan setiap tahunnya[4].

Tentu saja, obesitas juga berdampak pada sosial ekonomi seperti menurunnya kualitas kehidupan penderita, menurunnya produktivitas individu dan negara, tingginya biaya kesehatan negara, dan tingginya biaya yang dikeluarkan individu ketika sakit[1].

Proyek ini bertujuan untuk mengidentifikasi pengguna dari segala usia yang berisiko mengalami obesitas agar melakukan pencegahan untuk mengurangi biaya perawatan kesehatan jangka panjang.

### Problem Statements

- Berapa nilai variabel yang bisa dianggap seseorang mengalami obesitas.Karena untuk mengidentifikasi pengguna mengalami obesitas di perlukan nilai variabel yang di isi seperti BMI, berat, tinggi, usia, dan jenis kelamin.



### Goals

- Membuat model yang dapat memprediksi nilai fitur untuk menentukan kategori obesitas.

### Solution statements

- Untuk mencapai model yang akurat dibutuhkan beberapa model klasifikasi dan memilih model yang terbaik untuk menyelesaikan masalah.model yang akan digunakan adalah *SVM*,*Randomforest*,dan *Logisticregression*.

- Untuk memecahkan masalah klasifikasi akan menggunakan metrik akurasi karena menghitung jumlah benar yang diprediksi oleh model.

## Data Understanding

Data yang dipakai untuk membuat model adalah Obesity Prediction.Jumlah sampel yang berada pada dataset adalah 1000 Sampel.[Kaggle](https://www.kaggle.com/datasets/mrsimple07/obesity-prediction/download?datasetVersionNumber=1)

Berikut adalah informasi deskripsi statistik :

|index|Age|Height|Weight|
|---|---|---|---|
|count|1000\.0|1000\.0|1000\.0|
|mean|50\.0|170\.0|71\.0|
|std|18\.0|10\.0|16\.0|
|min|18\.0|136\.0|26\.0|
|25%|35\.0|164\.0|61\.0|
|50%|50\.0|170\.0|72\.0|
|75%|66\.0|177\.0|81.0|
|max|79\.0|201\.0|119\.0|

**Tabel 1.deskripsi *age, height, dan weight***


Pada Tabel 1,berisi informasi tentang *mean*(rata-rata) ,data terkecil hingga terbesar pada variabel *Age*, *Height*, dan *Weight*.

|index|BMI|PhysicalActivityLevel|
|---|---|---|
|count|1000\.0|1000\.0|
|mean|25\.0|3\.0|
|std|6\.0|1\.0|
|min|8\.0|1\.0|
|25%|21\.0|2\.0|
|50%|25\.0|3\.0|
|75%|29\.0|4\.0|
|max|51\.0|4\.0|

**Tabel 2.deskripsi *BMI, Physical ActivityLevel***

Pada Tabel 2,berisi informasi tentang *mean*(rata-rata) ,data terkecil hingga terbesar pada variabel *BMI* dan *PhysicalActivityLevel*.
### Variabel-variabel pada obesity prediction dataset adalah sebagai berikut:

- Age       : Usia seseorang.
- Gender : Jenis kelamin individu(Male,Female).
- Height  : Ketinggian individu(cm).
- Weight : Berat individu(kg).
- BMI      : Metrik yang dihitung berasal dari berat dan tinggi badan individu.
- PhysicalActivityLevel : Tingkat aktivitas fisik individu.
- ObesityCategory       : Tingkatan kategori obesitas(Underweight,Normal weight,Overweight,Obese).

## Visualisasi pada dataset
### Univariate analisis
![visualisasi jumlah data](https://github.com/ZedGred/Proyek_1/blob/main/eda.png?raw=true)
**Gambar 1.Jumlah dataset numerik**

  Pada Gambar 1,ini menunjukan jumlah data numerik yang berada pada dataset.

  ![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(3).png?raw=true)
**Gambar 2.Jumlah data *obesitycategory***

   Pada Gambar 2,sebagian besar data berada pada *normal weight*.Namun jumlah data pada*overweight* juga hampir sama besar yang menunjukan banyak sampel yang mengalami obesitas.
 
  ![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(5).png?raw=true)
**Gambar 3.Jumlah dataset *gender***

  Pada Gambar 3,dataset *male* memiliki jumlah data yang besar yang menunjukan bahwa sampel lebih banyak di ambil dari laki-laki. 
### Multivariete analisis
  ![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(4).png?raw=true)
**Gambar 4.jumlah data hubungan antara *obesitycategory* dengan *gender***

  Pada gambar 4,terlihat bahwa hubungan *male* dan *Obese* lebih tinggi dari *female* yang menunjukan sampel pria obesitas lebih banyak dari wanita.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(2).png?raw=true)
**Gambar 5.Hubungan antara data numerik**

  Pada Gambar 5.Hubungan antara *BMI* dan *Weight* paling terlihat korelasi antara lain yang menunjukan semaukin besar data *BMI* juga semakin besar data *weight*.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(1).png?raw=true)
**Gambar 6.Besaran korelasi metrik**

  Pada Gambar 6,Menunjukan bahwa sebagian besar mendekati angka 0.Ini menunjukan bahwa tidak ada hubungan signifikan antara fitur numerik.

## Data Preparation
- Melakukan *encoding* pada data kategori.Melakukan Encoding pada variabel kategori dengan *OneHotEncoder* dan menghapus variabel kategori yang telah di encoding.Variabel yang akan di *Encoding* dan dihapus adalah *gender* karene gender adalah variabel kategori.*Encoding* dilakukan agar fitur kategori dapat di *input* oleh model.
- Melakukan pembagian data.Menggunakan *Train_Test_Split* untuk membagi data.Proporsi yang digunakan adalah 0.2 dari ukuran dataset karena dapat menjaga keseimbangan  antara data *train* dan *test* agar tidak terjadi *overfitting* dan *underfitting*.Pembagian data dilakukan untuk menguji seberapa baik jika model di beri data baru.



## Modeling
Model yang akan digunakan untuk menyelesaikan masalah klasifikasi adalah *RandomForest* , *SVM* , dan *LogisticRegression*.
### RandomForest 
*RandomForest* adalah algoritma ensemble yang membangun banyak pohon keputusan dan menggabungkan prediksinya untuk membuat keputusan akhir. *RandomForest* sangat kuat dan dapat menangani data dengan baik, baik linier maupun *non-linier*. Selain itu,*RandomForest* dapat memberikan informasi penting tentang fitur yang penting untuk klasifikasi.
Parameter algoritma:
 
 - *n_estimators* = 100 (*default*).Jumlah pohon keputusan dalam hutan.

  - *min_samples_split* = 2 (*default*).Jumlah minimum sampel yang diperlukan untuk membagi simpul dalam pohon keputusan.

  - *min_samples_leaf*= 1  *(default)*.Jumlah minimum sampel yang diperlukan untuk membentuk daun dalam pohon keputusan.

  - *max_depth* = 5.Kedalaman maksimum pohon keputusan.Mengisi 5 agar tidak terjadi *overfitting*.


  Kelebihan dan kekurangan algoritma : 
   - Kelebihan    : Mampu menangani data yang tidak seimbang.
   - Kekurangan : Membutuhkan waktu komputasi yang lama dan memori yang besar.

### SVM
 *SVM* adalah algoritma klasifikasi yang memisahkan data menjadi dua kelas dengan membuat garis atau hiperplan yang memaksimalkan jarak antara kedua kelas. *SVM* sangat efektif untuk menangani data *linier* dan *non-linier*, dan dapat digunakan untuk klasifikasi biner dan multi-kelas.
Parameter algoritma:
 
  - C = 1.0 (*default*).Berfungsi untuk mengontrol tingkat regularisasi untuk mencegah *overfitting*.

  - *kernel* = *Linear*.Berfungsi untuk memetakan data ke ruang fitur dengan dimensi yang lebih tinggi.Memilih *kernel linear* karena masalah yang di hadapi adalah klasifikasi *linear*.
  - *gamma* = 1.0(*default*).Parameter *kernel RBF* yang mengontrol lebar fungsi kernel.

  Kelebihan dan kekurangan algoritma :

  - Kelebihan    : Efektif untuk jumlah dimensi lebih besar dari sampel.
  - Kekurangan : Kurang efektif untuk kasus klasifikasi data yang kompleks.

### LogisticRegression
 *LogisticRegression* adalah algoritma klasifikasi yang memodelkan probabilitas suatu titik data milik kelas tertentu. *LogisticRegression* sangat efektif untuk data linier dan dapat digunakan untuk klasifikasi biner dan multi-kelas.
Parameter algoritma: 
   - C = 1.0 (*default*).Mengontrol tingkat regularisasi untuk mencegah *overfitting*.
   - *max_iter* = 100 (*default*).Jumlah maksimum iterasi untuk algoritma optimisasi.
  - *solver* = *lbfgs* (default).Algoritma optimisasi yang digunakan untuk menemukan solusi.

  Kelebihan dan kekurangan algoritma :
  - Kelebihan    : Sangat efektif untuk klasifikasi data biner.
  - Kekurangan : Rentang terhadap *overfitting* pada dataset yang tidak.


## Evaluation
Metrik yang digunakan adalah metrik akurasi dan *F1* untuk mengevaluasi kasus klasifikasi.
### Metrik Akurasi
Metrik akurasi adalah metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar dari total prediksi yang dilakukan. 



Hasil penerapan dari metrik evaluasi adalah sebagai berikut:
| Model            |  *Train*	  | *Test*|
  ------------ | :-----------: | ----------:|
| *SVM* 	    | 98.75	 | 99.0 |
| *RF*	        | 100.0	 | 99.5 |
| *Logistic* |	97.875	 | 97.0 |

**Tabel 3.Hasil metrik akurasi**

Pada Tabel 3.*RandomForest* memiliki akurasi *train* dan *test* paling tinggi di antara model lainya.Namun tidak cukup untuk menyimpulkan bahwa *RandomForest* adalah model terbaik.Selisih hasil *train* dan *test* model *logistic* adalah 0.125 lebih rendah dari *RandomForest* yang memiliki selisih 0.5 yang membuat model *RandomForest* lebih rentan terhadap *overfitting*.

  - Formula metrik akurasi adalah sebagai berikut :

$$ Akurasi = {TP + TN \over FP+FN+TP+TN} $$
      TP = *True Positive*
      TN = *True Negative*
      FP = *False Positive*
      FN = *False Negative*

  - Metrik akurasi bekerja dengan membandingkan label yang diprediksi oleh model dengan label yang sebenarnya dari data.

### Metrik F1
Metrik *F1* merupakan ukuran kinerja klasifikasi yang menggabungkan presisi dan daya ingat. Ini dihitung sebagai rata-rata harmonik tertimbang dari presisi dan daya ingat.

  Hasil penerapan dari metrik evaluasi adalah sebagai berikut:
  
  |index|train\(rata-rata\)|test\(rata-rata\)|
  |---|---|---|
  |SVM|98\.725|99\.175|
  |RF|100|99\.65|
  |Logistic|97\.8|97\.57|

  **Tabel 4.Hasil evaluasi dari rata-rata metrik *F1* pada  data *train* dan *test***

  Pada tabel 4.*RandomForest* memiliki *F1* *test* rata-rata tertinggi (99,65%) dan *F1* *train* rata-rata yang sempurna (100%). Hal ini menunjukkan bahwa RF memiliki keseimbangan yang baik antara presisi dan *recall*.rata - rata F1 *test* SVM dan *Logistic* lebih rendah dari *RandomForest*.Hal ini menunjukan bahwa model *RandomForest* tahan terhadap *overfitting*.

  - Formula metrik *F1* adalah sebagai berikut :

    $$ F1 = 2 × (Presisi × Daya Ingat) \over (Presisi + Daya Ingat) $$
Presisi       = proporsi prediksi positif yang benar-benar positif.
daya ingat = proporsi positif sebenarnya yang diprediksi dengan benar.

   - Metrik F1 mengukur kinerja klasifikasi dengan mempertimbangkan keseimbangan antara presisi dan daya ingat.

### Kesimpulan 
Berdasarkan metrik akurasi dan *F1*, *RandomForest* adalah model terbaik dari ketiganya.Karena memiliki akurasi dan rata-rata *F1* *test* yang tinggi.Sehingga dapat menggeneralisasi dengan baik ke data baru.

## Daftar Referensi 

[1] Masrul M."Epidemi obesitas dan dampaknya terhadap status kesehatan masyarakat serta sosial ekonomi bangsa".Majalah Kedokteran Andalas (2018).Tersedia : [tautan](https://www.mendeley.com/catalogue/afadc810-369b-3f4d-ac38-f434e0c805d1)

[2] Vaamonde J. G.,Álvarez-Món M. A."Obesity and overweight".Medicine (Spain) (2020).Tersedia : [tautan](https://www.mendeley.com/catalogue/7ecbf93d-afbf-3501-8932-91e65c9f27ce)

[3] Wollenstein-Seligson D.Iglesias-Leboreiro J.Bernárdez-Zapata I.Braverman-Bronstein A.See fewer.Prevalencia de sobrepeso y obesidad infantil en un hospital privado de la Ciudad de México.Revista Mexicana de Pediatría (2016).Tersedia : [tautan](https://www.mendeley.com/catalogue/3377094c-48af-3134-8a5f-865871c7b4ff)

[4] Setyawan M. D.Pratama M.Trisnanto F.Marlinda L.Hayuningtias R."Aplikasi Diet Planner (Dinner) Bagi Penderita Obesitas Berbasis Android".Reputasi: Jurnal Rekayasa Perangkat Lunak (2020).Tersedia : [tautan](https://www.mendeley.com/catalogue/f4ff6425-377e-32cf-89b9-32423ef86335)



