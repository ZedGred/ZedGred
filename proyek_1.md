__# Laporan Proyek Machine Learning - Pebiyan Firmansyah 

## Domain Proyek

Obesitas adalah penyakit kronis yang ditandai dengan penumpukan lemak berlebih di tubuh, yang dapat menyebabkan berbagai masalah kesehatan dan psikologi.

**Tambahan :**
- Prediksi obesitas adalah proses untuk mengestimasi tingkat obesitas seseorang berdasarkan faktor-faktor yang mempengaruhinya. Prediksi obesitas dapat dilakukan dengan menggunakan berbagai metode, seperti regresi dan klasifikasi.

- Obesity is a multifactorial condition, whose etiopathogenesis and evolution are influenced by multiple situations interacting among them. It affects almost all scopes of people's health status, being the range of comorbidities very wide. Customization, active attitude, obesity and comorbidities assessment are crucial diagnostic factors. Taking into account the natural history of the disease, the early identification and management may avoid or lessen the evolution of comorbidities and, ultimately, reduce fatal events, improve quality of life and increase life expectancy. The high prevalence reached in developed countries, as well as the prevalence and incidence rates that it is obtaining in developing countries, have made obesity a major health worldwide problem. As consequence of its social and economic implications, obesity has become one of the main threats to public health and to maintaining the balance in health systems.  :  [Obesity and overweight](https://www.mendeley.com/catalogue/7ecbf93d-afbf-3501-8932-91e65c9f27ce)

## Business Understanding

Berdasarkan data yang dihimpun World Population Review, jumlah penderita obesitas di seluruh dunia meningkat hampir tiga kali lipat sejak 1975,tentu saja kita tidak ingin keluarga dan kerabat kita terkena obesitas.prediksi yang kita gunakan untuk menentukan kategori berat badan seseorang.

### Problem Statements

- berapa nilai fitur yang bisa dianggap seseorang mengalami obesitas.

### Goals

- membuat model yang dapat memprediksi nilai fitur untuk menentukan kategori berat badan.

**Tambahan :**
### Solution statements

- untuk mencapai model yang akurat kita membutuhkan beberapa model klasifikasi dan memilih model terbaik.model yang saya gunakan adalah svm,randomforest,dan logisticregression.

- untuk memecahkan masalah klasifikasi saya menggunakan metrics accuracy.

## Data Understanding

Kumpulan Data Prediksi Obesitas menyediakan kumpulan atribut komprehensif terkait demografi individu, kebiasaan gaya hidup, dan indikator kesehatan, yang bertujuan untuk memfasilitasi prediksi prevalensi obesitas.[Kaggle](https://www.kaggle.com/datasets/mrsimple07/obesity-prediction/download?datasetVersionNumber=1)
memiliki jumlah data yaitu 1000 sample.


### Variabel-variabel pada obesity prediction dataset adalah sebagai berikut:

- Age       : Usia seseorang.
- Gender : Jenis kelamin individu.
- Height  : Ketinggian individu.
- Weight : Berat individu.
- BMI      : Metrik yang dihitung berasal dari berat dan tinggi badan individu.
- PhysicalActivityLevel : Tingkat aktivitas fisik individu.
- ObesityCategory       : Tingkatan kategori obesitas.

**Tambahan :**
- visualisasi pada jumlah dataset
![visualisasi jumlah data](https://github.com/ZedGred/Proyek_1/blob/main/eda.png?raw=true)

## Data Preparation
- Melakukan encoding pada data kategori.
- Melakukan pembagian data.

**Tambahan :**
- Melakukan Encoding dengan OneHotEncoder dan menghapus kolom kategori yang telah di encoding seperti contoh di bawah :
```
from sklearn.preprocessing import OneHotEncoder
obes=pd.concat([obes,pd.get_dummies(obes['Gender'],prefix='Gender')],axis=1)
obes.drop(['Gender'],axis=1,inplace=True)
obes.head()
```
- Menggunakan Train_Test_Split untuk membagi data seperti contoh dibawah :
```
from sklearn.model_selection import train_test_split
X=obes[['Age','Height','Weight','BMI','PhysicalActivityLevel','Gender_Female','Gender_Male]]
y=obes['ObesityCategory']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 123)
```

- Melakukan Encoding agar fitur kategori dapat di input oleh model.

- Melakukan pembagian data untuk menguji seberapa baik jika model di beri data baru

## Modeling
Model yang saya gunakan untuk menyelesaikan masalah klasifikasi adalah RandomForest , svm , dan LogisticRegression.
```
from sklearn.ensemble import RandomForestClassifier
rf = RandomForestClassifier()
rf.fit(X_train, y_train)
```
- Mengimport model yang akan di gunakan.
- Menyimpan model pada variabel.
- Melatih model dengan data latih dengan fit.

**Tambahan :**

- Kelebihan:
  - RandomForest        : Mampu menangani data yang tidak seimbang.
  - SVM                         : Efektif untuk jumlah dimensi lebih besar dari sampel.
  - LogisticRegression : Sangat efektif untuk klasifikasi data biner.
- Kekurangan :
   - RandomForest        : Membutuhkan waktu komputasi yang lama dan memori yang besar.
  - SVM                         : Kurang efektif untuk kasus klasifikasi data yang kompleks.
  - LogisticRegression : Rentang terhadapp overfitting pada dataset yang tidak seimbang.
- Model RandomForest adalah model terbaik karena bisa mengatasi data yang tidak seimbang dan data yang saya gunakan terbilang sedikit sehingga dapat menghasilkan akurasi skor yang paling tinggi di antara model lainnya.

## Evaluation
- Metrik yang saya gunakan adalah metrics akurasi yang menghitung jumlah data yang diprediksi dengan benar.
```
                   Train Test   
SVM                98.5  99.0
RandomForest       100.0 99.5
LogisticRegression 96.25 96.5

```
Dari data di atas model RandomForest memiliki akurasi train dan test paling tinggi di antara model lainnya.
**Tambahan :**
- Formula metrics akurasi adalah sebagai berikut : 
```
Akurasi=TP+TN/FP+FN+TP+TN
TP = True positive
TN = True negative 
FP = False positive
FN = False negative
```

- Metrik akurasi bekerja dengan membandingkan label yang diprediksi oleh model dengan label yang sebenarnya dari data. 







