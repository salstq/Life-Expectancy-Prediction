# Laporan Proyek Machine Learning - Salsa Tashfiyatul Qolbi

## Domain Proyek
Proyek ini berada dalam domain Kesehatan, khususnya Kesehatan global dengan tujuan utama untuk memprediksi harapan hidup suatu negara. Harapan hidup merupakan salah satu indikator yang paling penting dalam menilai kualitas hidup dan pembangunan negara karena menggambarkan banyak aspek kesehatan masyarakat, kesejahteraan ekonomi, dan efektivitas sistem layanan kesehatan.

Di sebagian besar negara, terutama negara berkembang, harapan hidup tetap dipengaruhi oleh beberapa kompleksitas seperti tingginya angka anak, kelangkaan gizi, rendahnya tingkat pendidikan, buruknya kses layanan kesehatan, serta faktor sosial-ekonomi lainnya. Menurut World Health Organization, faktor-faktor seperti status ekonomi, infrastruktur sosial, dan kualitas layanan kesehatan berpengaruh besar dalam menentukan harapan hidup sebuah populasi (WHO, 2025).

Permasalahan yang dihadapi adalah kompleksitas hubungan antar variabel-variabel tersebut, yang sulit dianalisis hanya dengan pendekatan statistik dasar. Di sinilah machine learning menjadi relevan, karena memiliki kemampuan untuk mempelajari pola dan hubungan non-linear dari data multivariat secara lebih efektif. Dengan membangun model prediktif berbasis machine learning, dapat membantu mengidentifikasi faktor-faktor paling signifikan yang memengaruhi harapan hidup, serta memperkirakan harapan hidup suatu negara berdasarkan data historis dan indikator sosial-ekonomi yang tersedia.

Proyek ini mempunyai tujuan untuk tidak hanya memprediksi nilai harapan hidup dengan akurat, tapi juga memberi kemampuan pengetahuan pada pengambil kebijakan dan institusi kesehatan internasional dalam merencanakan strategi intervensi yang lebih spesifik sasaran berdasarkan data.

## Business Understanding

### Problem Statements
- Dapatkah umur harapan hidup suatu negara diprediksi secara akurat berdasarkan faktor-faktor sosial, ekonomi, dan kesehatan?
- Apa saja faktor yang paling berpengaruh terhadap harapan hidup suatu negara?
- Algoritma regresi mana yang memberikan performa terbaik dalam memprediksi harapan hidup?

### Goals
- Membangun model prediktif untuk memperkirakan nilai harapan hidup berdasarkan data sosial, ekonomi, dan kesehatan.
- Mengidentifikasi fitur-fitur yang paling signifikan dan berkontribusi besar terhadap prediksi harapan hidup.
- Membandingkan performa beberapa algoritma regresi dan memilih model terbaik.

### Solution Statements
- Menerapkan beberapa algoritma regresi, yaitu Linear Regresi, Random Forest, dan Gradient Boosting.
- Melakukan preprocessing data secara lengkap, seperti imputasi missing value, penanganan outlier, encoding, dan stadarisasi.
- Melakukan hyperparameter tuning pada model terbaik untuk meningkatkan performa.
- Menggunakan metrik MAE, MSE, RMSE, dan R² untuk mengevaluasi model.

## Data Understanding
Dataset Life Expectancy (WHO) yang berasal dari Kaggle [Life Expectancy (WHO)](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who). Dataset ini memiliki 2938 baris dan 22 kolom yang terdiri atas 20 kolom numerik dan 2 kolom kategorikal dengan rincian sebagai berikut:

**Informasi Dataset**
# Life Expectancy Dataset
| **Judul**       | Life Expectancy Dataset                                                             |                  
|-----------------|-------------------------------------------------------------------------------------|
| **Author**      | KumarRajarshi                                                                       |
| **Source**      | [Kaggle](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who)          |
| **Visibility**  | Public                                                                              |
| **Usability**   | 8.24                                                                                |

**Metadata**
| Kolom                         | Deskripsi                                         | Tipe Data    |
|-------------------------------|---------------------------------------------------|--------------|
| Country                       | berisi 193 negara                                 | Kategorikal       |
| Year                          | tahun pengambilan data                            | Integer      |
| Status                        | berisi status dari sebuha negara, negara berkembang atau negara maju | Kategorikal  |
| Life Expectancy               | harapan hidup berdasarkan umur                    | Float        |
| Adult Mortality               | kematian orang dewasa per 1000 populasi           | Float        |
| Infant Deaths                 | kematian bayi per 1000 populasi                   | Integer      |
| Alcohol                       | konsumsi alcohol per kapita                       | Float        |
| Percentage Expenditure        | persentase pengeluaran untuk Kesehatan pada produk domestic bruto per kapita | Float     |
| Hepatitis B                   | cakupan imunisasi pada anak usia 1 tahun          | Float        |
| Measles                       | kasus campak yang tercatat per 1000 populasi      | Integer      |
| BMI                           | rata-rata indeks massa tubuh seluruh populasi     | Float        |
| Under-five deaths             | angka kematian anak dibawah 5 tahun per 1000 kematian | Integer      |
| Polio                         | cakupan imunisasi polio pada anak umur 1 tahun    | Float        |
| Total expenditure             | pengeluaran pemerintah umum untuk Kesehatan sebagai persentase dari total pengeluaran pemerintah | Float  |
| Diphtheria                    | cakupan imunisasi Diphtheria tetanus toxoid dan pertussis (DTP3) pada anak umur 1 tahun | Float  |
| HIV/AIDS                      | kematian per 1000 kelahiran hidup anak dengan HIV/AIDS (0-4 tahun) | Float|
| GDP                           | produk domestic bruto per kapita di USD           | Float       |
| Population                    | populasi dari negara                              | Float       |
| Thinness 10-19 years          | prevalensi kurus pada anak dan remaja usia 10-19 tahun | Float  |
| Thinness 5-9 years            | prevalensi kurus pada anak dan remaja usia 5-9 tahun | Float    |
| Income composition            | Indeks Pembangunan Manusia dalam hal komposisi pendapatan sumber daya (indeks berkisar antara 0 sampai 1) | Float |
| Schooling                     | Jumlah Tahun Sekolah (tahun)                      | Float       |

### Exploratory Data Analysis
Pada tahap ini dilakukan analisis untuk data yang ada di dalam dataset seperti dilihat
| Kolom                             | Jumlah Non-NUll    | TIpe Data     |
|-----------------------------------|--------------------|---------------|
| Country                           | 2938 non-null      | object        |
| Year                              | 2938 non-null      | int64         |
| Status                            | 2938 non-null      | object        |
| Life expectancy                   | 2928 non-null      | float64       |
| Adult Mortality                   | 2928 non-null      | float64       |
| infant deaths                     | 2938 non-null      | int64         |
| Alcohol                           | 2744 non-null      | float64       |
| percentage expenditure            | 2938 non-null      | float64       |
| Hepatitis B                       | 2385 non-null      | float64       |
| Measles                           | 2938 non-null      | int64         |
| BMI                               | 2904 non-null      | float64       |
| under-five deaths                 | 2938 non-null      | int64         |
| Polio                             | 2919 non-null      | float64       |
| Total expenditure                 | 2712 non-null      | float64       |
| Diphtheria                        | 2919 non-null      | float64       |
| HIV/AIDS                          | 2938 non-null      | float64       |
| GDP                               | 2490 non-null      | float64       |
| Population                        | 2286 non-null      | float64       |
| thinness  1-19 years              | 2904 non-null      | float64       |
| thinness 5-9 years                | 2904 non-null      | float64       |
| Income composition of resources   | 2771 non-null      | float64       |
| Schooling                         | 2775 non-null      | float64       |

Output di atas menunjukkan bahwa dataset memiliki 2938 data dan 22 kolom.
- Terdapat 2 tipe data object
- Terdapat 4 tipe data int64
- Terdapat 16 tipe data float64
- Terdapat Missing Value
  
### EDA - Univariate Analysis
Berikut adalah persebaran data atau distribusi data dari fitur numerik.
![alt text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/numerical_distribution.png)

Berikut adalah persebaran data atau distribusi data dari fitur kategorikal.
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/categorical_distribution.png)

### Correlation Matrix
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/corr_heatmap.png)
Terdapat beberapa kolom numerik yang memiliki korelasi yang cukup tinggi, seperti kolom GDP dengan kolom percentage expenditure. Kolom-kolom yang memiliki korelasi tinggi, akan dihapus salah satunya untuk menghindari bias pada data.

## Data Preparation
Teknik yang akan dilakukan:
- Ganti nama kolom : mengganti nama kolom yang salah dan tidak rapih
- Missing value : mengganti nilai kosong dengan nilai median
- Duplikasi data : cek apakah terdapat data yang terduplikasi
- Fitur selection : menghapus beberapa fitur yang tidak relevan dan berkorelasi tinggi 
- Outliers checking & handling : Mengurangi outliers
- Standarisasi : Menyamakan skala fitur
- Label encoding : Mengubah fitur kategorikal menjadi numerik
- Split data : Membagi dataset menjadi 2, yaitu data latih (70%) dan data uji (20%)

### Ganti nama kolom 
Terdapat kesalahan penamaan pada kolom thinness 1-19 years, isi dari kolom tersebut adalah data orang dari umur 10-19 tahun, sehingga kolom itu harus diganti namanya. Selain itu, terdapat beberapa kolom yang penamaannya tidak rapih.

### Missing Value
Terlihat bahwa dalam dataset terdapat missing value. Karena data yang hilang semuanya berada pada kolom numerik, maka solusi yang dapat dilakukan adalah dengan imputasi atau mengisi missing value dengan median. Walaupun penanganan missing value termasuk tahap data preparation, namun tetap dilakukan sebelum EDA agar hasil dari EDA dapat memberikan hasil yang maksimal.

### Duplikasi Data
Tidak terdapat data yang terduplikasi. Sama hal nya dengan missing value, cek duplikasi data dilakukan sebelum EDA.

### Fitur Selection
Memilih fitur yang relevan dan menghapus fitur yang tidak relevan serta berkorelasi tinggi. Adapun fitur yang dihapus adalah infant deaths, percentage expenditure, Country, thinness 10-19 years, Hepatitis B

### Outlier Checking & Handling
Outlier dapat mempengaruhi hasil akhir dari model, maka dari itu diperlukan tindakan untuk mengurangi bahkan menghilangkan outlier. Saya menggunakan IQR Method untuk menangani outlier.

#### Langkah-langkah IQR Method
1. **Pilih Fitur Numerik**:
  Kolom yang dipakai adalah kolom numerik, karena rentang terhadap outlier.
2. **Hitung Kuartil dengan IQR**:
  - Q1 (Kuartil 1): Nilai yang memisahkan 25% data terendah dari 75% data lainnya.
  - Q3 (Kuartil 3): Nilai yang memisahkan 75% data terendah dari 25% data tertinggi.
  - IQR (Interquartile Range): Rentang antara Q3 dan Q1. Ini mengukur sebaran nilai tengah dari data.
3. **Tentukan Ambang Batas Outlier**:  
   - Batas bawah: \( Q1 - 1.5 \times IQR \)  
   - Batas atas: \( Q3 + 1.5 \times IQR \)
4. **Filter Outlier**:  
   Baris data dengan nilai di luar batas bawah dan atas dianggap sebagai outlier dan dihapus dari dataset.

#### Kenapa Menggunakan IQR Method?
IQR Method digunakan untuk mendeteksi dan menangani outlier dalam dataset. Alasan menggunakan IQR method adalah:
- tidak terpengaruh oleh distribusi data
- fokus pada data tengah
- efektif untuk deteksi outlier ekstrem
- cocok untuk data skewed

Setelah penanganan oulier terhadap kolom numerik, data berkurang menjadi 1149 baris. Hasil Boxplot setelah difilter dapat dilihat di bawah ini.
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/adultmortalityboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/alcoholboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/bmiboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/diphtheriaboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/gdpboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/hivaidsboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/incomeboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/lifeexpectancyboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/measlessboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/polioboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/populationboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/schoolingboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/thinness5-9yearsboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/totalexpenditureboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/under-fivedeathsboxplot.png)
![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/yearboxplot.png)

### Label Encoding 
Untuk melakukan label encoding maka akan menggunakan function ```get_dummies()```. Fitur yang di encoding hanya fitur Status.

### Split Data
Pada tahap ini, dataset akan dibagi menjadi dua yaitu data latih dan data uji. Data train berguna untuk melatih model sedangkan data test berguna untuk menguji performa dari model. 
```X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)```
Pada tahap ini, dibagi menjadi 70% data latih dan 30% data uji.

## Modelling
Menggunakan tiga model, yaitu:
- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor
  
Selain menggunakan tiga model, pada tahap modelling juga dilakukan tuning, dengan tahapan sebagai berikut: 
- Feature Importance
- Hyperparameter Tuning

### Linear Regression
Linear Regression adalah model paling sederhana karena memetakan hubungan linier antara input (X) dengan target (y) dengan persamaan garis lurus. Parameter yang digunakan adalah parameter default.
Kelebihan:
- Sederhana dan cepat
- Bisa digunakan sebagai baseline model
Kekurangan:
- Tidak cocok untuk hubungan non-linier
- Sangat sensitif dengan outliers

### Random Forest Regressor
Random Forest Regressor adalah ensemble model berbasis pohon keputusan. Algoritma ini membangun banyak pohon keputusan secara acak pada subset data, kemudian menggabungkan hasil prediksi dari masing-masing pohon dengan metode voting. Parameter yang digunakan adalah parameter default.
Kelebihan:
- Kuat terhadap overfitting
- Tidak sensitif terhadap outliers
Kekurangan:
- Lebih lambat dari Linear Regression
- Butuh tuning parameter untuk performa maksimal

### Gradient Boosting Regressor
Gradient Boosting Regressor adalah model ensemble lain berbasis decision tree, tapi menggunakan pendekatan boosting, artinya membangun pohon bertahap, di mana tiap pohon mencoba memperbaiki error dari pohon sebelumnya. Parameter yang digunakan adalah parameter default.
Kelebihan:
- Akurasi tinggi
- Bisa menangani berbagai jenis data
Kekurangan:
- Rentan overfitting
- Butuh waktu lebih lama

#### Feature Importance
Memilih fitur yang paling penting pada algoritma Random Forest. Memilih 10 fitur tertinggi, yaitu Income composition of resources, Adult Mortality, thinness 5-9 years, Total expenditure, Alcohol, Population, Schooling, GDP, under-five deaths, BMI

#### Hyperparameter Tuning
RandomizedSearchCV adalah metode pencarian hyperparameter untuk model machine learning yang melakukan pencarian secara acak pada ruang parameter yang telah ditentukan. Metode ini lebih efisien daripada GridSearchCV, karena tidak mencoba semua kombinasi parameter tetapi memilih acak iterasi yang telah ditentukan.

RandomizedSearchCV digunakan untuk mencari kombinasi parameter terbaik secara acak dari:
- n_estimators: Jumlah pohon dalam hutan
- max_depth: Kedalaman maksimum tiap pohon
- min_samples_split: Minimum sampel untuk membagi node
- min_samples_leaf: Minimum sampel pada daun
- max_features: Jumlah fitur yang dipertimbangkan di setiap split
- bootstrap: Apakah memakai bootstrapped samples atau tidak

Pengaturan RandomizedSearchCV:
- n_iter=50: Jumlah kombinasi parameter yang diacak.
- cv=5: 5-fold cross-validation.
- scoring='r2': Evaluasi berdasarkan nilai R² score.
- n_jobs=-1: Menggunakan seluruh core CPU untuk mempercepat proses.
- random_state=42: Untuk hasil yang konsisten.

Setelah melakukan proses tuning menggunakan RandomizedSearchCV dengan 50 iterasi dan validasi silang sebanyak 5 fold, diperoleh kombinasi hyperparameter terbaik untuk model Random Forest Regressor sebagai berikut:
- n_estimators = 100
Jumlah pohon keputusan (trees) yang digunakan dalam ensemble model adalah 100. Jumlah ini cukup untuk memberikan performa yang stabil tanpa menambah waktu komputasi yang berlebihan.
- min_samples_split = 5
Minimum jumlah sampel yang diperlukan untuk membagi (split) sebuah node dalam pohon keputusan adalah 5. Ini membantu menghindari pembentukan node yang terlalu kecil dan mengurangi risiko overfitting.
- min_samples_leaf = 4
Minimum jumlah sampel yang harus ada di setiap daun (leaf) pohon adalah 4. Ini juga berfungsi sebagai regularisasi agar model tidak terlalu kompleks.
- max_features = 'sqrt'
Setiap pohon hanya menggunakan subset fitur sebanyak akar kuadrat dari total fitur yang tersedia untuk mencari pembagian terbaik, yang dapat meningkatkan keragaman antar pohon dan mengurangi korelasi antar pohon.
- max_depth = 10
Kedalaman maksimum tiap pohon dibatasi hingga 10 tingkat, sehingga pohon tidak tumbuh terlalu dalam dan menghindari overfitting.
- bootstrap = True
Setiap pohon dibangun menggunakan sampling bootstrap (sampling dengan pengembalian) dari data pelatihan, sesuai dengan prinsip Random Forest.

## Evaluation
Pada evaluasi terdapat 3 tahap evaluasi, yaitu
- Evaluasi Test Set
- Cross-Validation
- Evaluasi Train & Test Hyperparameter Tuning
  
### Evaluasi Test Set
| **Model**                 | **MAE** | **MSE** | **RMSE** | **R²** |
|---------------------------|---------|---------|----------|--------|
| Linear Regression         | 2.141503757392989 | 8.316375553550452 | 2.883812676570802 | 0.731487625387514 |
| Random Forest             | 1.1829101449275359 | 3.1442941043478125 | 1.7732157523403103 | 0.8984795875316107 |
| Gradient Boosting         | 1.3263824607665666 | 3.613384062531356 | 1.9008903341674805 | 0.8833339922217691 |

Dari hasil evaluasi, terlihat bahwa model RandomForest menjadi model terbaik untuk melatih data.

### Cross-Validation
| **Model**                 | **Mean R² Score**  |
|---------------------------|--------------------|
| Linear Regression         | 0.6353477158861963 |
| Random Forest             | 0.7595618767521196 |
| Gradient Boosting         | 0.7504584639920904 |

Evaluasi menggunakan cross-validation memperlihatkan jika model RandomForest tetap model terbaik untuk melatih data. Karena mode Random Forest menjadi model yang paling baik, maka akan dilakukan optimisasi dengan Hyperparameter Tuning menggunakan RandomizedSearchCV agara hasilnya optimal.

### Evaluasi Train & Test Hyperparameter Tuning

| **Dataset Evaluation**    | **MAE** | **MSE** | **RMSE** | **R²** |
|---------------------------|---------|---------|----------|--------|
| Train Set Evaluation      | 0.9776833482888506 | 2.0755808737338812 | 1.440687639196603 | 0.9318150999682708 |
| Test Set Evaluation       | 1.3225943306624466 | 3.7232335607270075 | 1.9295682316847487 | 0.8797872609058761 |
- Model tidak overfitting: R² pada train = 0.93 dan test = 0.88, jadi performanya stabil di kedua dataset.
- Perbedaan MAE dan RMSE antara train dan test tidak terlalu besar, yang berarti model berhasil belajar pola tanpa terlalu menghafal data.
- Random Forest Regressor dengan tuning + feature selection memberikan hasil prediksi umur harapan hidup yang akurat.

### Mengapa Menggunakan MAE, MSE, RMSE, R², dan Cross-Validation
- MAE : mudah dipahami karena langsung menunjukkan rata-rata kesalahan dalam satuan asli.
- MSE : membantu mendeteksi outlier
- RMSE : Menggabungkan kelebihan MSE (sensitif terhadap error besar) tapi dengan skala yang lebih mudah dipahami.
- R² : Nilainya antara 0 dan 1 (atau negatif jika model sangat buruk), memudahkan interpretasi.
- Cross-Validation : teknik validasi model dengan cara membagi data menjadi beberapa bagian (fold), lalu melatih dan menguji model secara bergiliran di setiap fold. Berguna untuk menghindari overfitting.

Berikut adalah visualisasi antara aktual data dengan prediksi data.

![alt_text](https://github.com/salstq/Life-Expectancy-Prediction/blob/main/Gambar/Visualisasi.png)

## Dampak Model terhadap Business Understanding
### Apakah Model Menjawab Problem Statements?
- **Ya**, model berhasil membangun prediksi umur harapan hidup menggunakan beberapa algoritma regresi, berhasil mengidentifikasi faktor-faktor penting, seperti fitur importance yang telah dissebutkan di atas, dan berhasil menentukan mana algoritma yang memberikan performa terbaik.

### Apakah Model Berhasil Mencapai Goals?
- **Ya**, model berhasil mengidentifikasi fitur-fitur yang signifikan dalam memprediksi harapan hidup, dan model mampu membangun model yang dapat memprediksi dengan akurat. Penggunaan tiga jenis algoritma ini memungkinkan untuk dilakukan perbandingan terhadap performa masing-masing model, dan didapat model terbaik, yaitu Random Forest Regressor.

### Apakah Solusi yang Direncanakan Berdampak?
- **Ya**, model ini berdampak, karena memeberikan prediksi akurat untuk umur harapan hidup, dapat membantu pemngambil kebijakan memahami faktor utama yang mempengaruhi harapan hidup, dan hasil dapat digunakan untuk intervensi kebijakan berbasis data di bidang kesehatan dan ekonomi.

## Kesimpulan
Berdasarkan hasil di atas, dapat dikatakan bahwa model mampu memprediksi umur harapan hidup dengan hasil akurasi menggunakan algoritma Random Forest Regressor yaitu 88%. SSelain itu, dari hasil visualisasi menggunakan correlation matrix, diketahui bahwa fitur "Income Composition of Resources" yang merupakan indikator pembangunan manusia dalam aspek komposisi pendapatan sumber daya (dengan nilai indeks berkisar antara 0 hingga 1) memiliki korelasi yang sangat kuat terhadap umur harapan hidup. Hal ini menegaskan bahwa faktor sosial-ekonomi memainkan peran penting dalam menentukan tingkat kesehatan dan umur suatu populasi. Oleh karena itu, dapat dikatakan bahwa analisis ini dapat menjawab dari kedua problem statements.

## Referensi 
_Social determinants of health_ [Sumber_referensi](https://www.who.int/news-room/fact-sheets/detail/social-determinants-of-health)

