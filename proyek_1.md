# Laporan Proyek Machine Learning - Pebiyan Firmansyah 

## Domain Proyek

Obesitas adalah penyakit kronis yang ditandai dengan penumpukan lemak berlebih di tubuh, yang dapat menyebabkan berbagai masalah kesehatan dan psikologi.

Prediksi obesitas adalah proses untuk mengestimasi tingkat obesitas seseorang berdasarkan faktor-faktor yang mempengaruhinya. Prediksi obesitas dapat dilakukan dengan menggunakan berbagai metode, seperti regresi dan klasifikasi.

*As consequence of its social and economic implications, obesity has become one of the main threats to public health and to maintaining the balance in health systems.* :  [Obesity and overweight](https://www.mendeley.com/catalogue/7ecbf93d-afbf-3501-8932-91e65c9f27ce)

## Business Understanding

Berdasarkan data yang dihimpun World Population Review, jumlah penderita obesitas di seluruh dunia meningkat hampir tiga kali lipat sejak 1975.Tentu saja, obesitas juga berdampak pada sosial ekonomi seperti menurunnya kualitas kehidupan penderita, menurunnya produktivitas individu dan negara, tingginya biaya kesehatan negara, dan tingginya biaya yang dikeluarkan individu ketika sakit. 

### Problem Statements

- Berapa nilai fitur yang bisa dianggap seseorang mengalami obesitas.

### Goals

- Membuat model yang dapat memprediksi nilai fitur untuk menentukan kategori berat badan.

### Solution statements

- Untuk mencapai model yang akurat dibutuhkan beberapa model klasifikasi dan memilih model yang terbaik untuk menyelesaikan masalah.model yang akan digunakan adalah *SVM*,*Randomforest*,dan *Logisticregression*.

- Untuk memecahkan masalah klasifikasi akan menggunakan metrik akurasi karena menghitung jumlah benar yang diprediksi oleh model.

## Data Understanding

Data yang dipakai untuk membuat model adalah Obesity Prediction.Jumlah sampel yang berada pada dataset adalah 1000 Sampel.[Kaggle](https://www.kaggle.com/datasets/mrsimple07/obesity-prediction/download?datasetVersionNumber=1)
### Variabel-variabel pada obesity prediction dataset adalah sebagai berikut:

- Age       : Usia seseorang.
- Gender : Jenis kelamin individu(Male,Female).
- Height  : Ketinggian individu.
- Weight : Berat individu.
- BMI      : Metrik yang dihitung berasal dari berat dan tinggi badan individu.
- PhysicalActivityLevel : Tingkat aktivitas fisik individu.
- ObesityCategory       : Tingkatan kategori obesitas(Underweight,Normal weight,Obese,Overweight).

### Visualisasi pada dataset
- Univariate analisis
  - Gambar di bawah menunjukan jumlah data numerik pada dataset.![visualisasi jumlah data](https://github.com/ZedGred/Proyek_1/blob/main/eda.png?raw=true)
  - Gambar di bawah menunjukan jumlah data *normal weight* paling banyak pada dataset.![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(3).png?raw=true)
  Gambar di bawah menunjukan jumlah data kategori *Gender* pada dataset.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(5).png?raw=true)
- Multivariete analisis
  - Gambar di bawah menunjukan jumlah dataset *normal weight* dan *male* paling banyak pada dataset.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(4).png?raw=true)
  - Gambar di bawah menunjukan bar korelasi antara dataset numerik.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(2).png?raw=true)
  - Gambar di bawah menunjukan seberapa besar korelasi antara dataset.
![](https://github.com/ZedGred/Proyek_1/blob/main/download%20(1).png?raw=true)
Terlihat pada gambar di atas menunjukan banyak dataset yang korelasinya mendekati 0 yang berarti tidak ada hubungan linear antara dua variabel pada dataset.

## Data Preparation
- Melakukan encoding pada data kategori.Melakukan Encoding dengan OneHotEncoder dan menghapus kolom kategori yang telah di encoding.Encoding dilakukan agar fitur kategori dapat di input oleh model.
- Melakukan pembagian data.Menggunakan Train_Test_Split untuk membagi data.Proporsi yang digunakan adalah 0.2 dari ukuran dataset karena dapat menjaga keseimbangan  antara data *train* dan *test* agar tidak terjadi *overfitting* dan *underfitting*.Pembagian data dilakukan untuk menguji seberapa baik jika model di beri data baru.



## Modeling
Model yang akan digunakan untuk menyelesaikan masalah klasifikasi adalah *RandomForest* , *SVM* , dan *LogisticRegression*.
- *RandomForest* berkerja dengan cara menggabungkan hasil (N) dari beberapa decision tree untuk membuat random forest.Lalu membuat prediksi untuk setiap pohon yang dibuat.
    - Kelebihan    : Mampu menangani data yang tidak seimbang.
  - Kekurangan : Membutuhkan waktu komputasi yang lama dan memori yang besar.
- *SVM* bekerja dengan memetakan data ke ruang fitur berdimensi tinggi sehingga titik data dapat dikategorikan, bahkan ketika data tidak dapat dipisahkan secara linear.
**Parameter yang di gunakan adalah kernel *linear* yang berfungsi yang menghitung produk titik antara dua vektor fitur**.
  - Kelebihan    : Efektif untuk jumlah dimensi lebih besar dari sampel.
Kekurangan : Kurang efektif untuk kasus klasifikasi data yang kompleks.
- *LogisticRegression* bekerja dengan mengubah kombinasi linier dari variabel independen menjadi probabilitas antara 0 dan 1.
  - Kelebihan    : Sangat efektif untuk klasifikasi data biner.
  - Kekurangan : Rentang terhadap *overfitting* pada dataset yang tidak.


## Evaluation
Metrik yang digunakan adalah metrics akurasi.Metrik akurasi adalah metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar dari total prediksi yang dilakukan. 

Hasil penerapan dari metrik evaluasi adalah sebagai berikut:
| Model            |  *Train*	  | *Test*|
------------ | :-----------: | ----------:|
| *SVM* 	    | 98.75	 | 99.0 |
| *RF*	        | 100.0	 | 99.5 |
| *Logistic* |	96.25	 | 96.5 |

Dari data di atas model *RandomForest* memiliki akurasi *train* dan *test* paling tinggi di antara model lainnya.

- Formula metrik akurasi adalah sebagai berikut : 
```
Akurasi=TP+TN/FP+FN+TP+TN
TP = True positive
TN = True negative 
FP = False positive
FN = False negative
```

- Metrik akurasi bekerja dengan membandingkan label yang diprediksi oleh model dengan label yang sebenarnya dari data. 







