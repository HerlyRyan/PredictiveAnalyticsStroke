## Laporan Proyek Machine Learning - Prediksi Stroke pada Data Kesehatan

### Domain Proyek

#### Latar Belakang

Stroke adalah penyakit pada otak berupa gangguan fungsi saraf lokal dan atau global, yang muncul mendadak, progresif, dan cepat. Gangguan fungsi saraf pada stroke disebabkan oleh gangguan peredaran darah otak non traumatik.

Stroke merupakan salah satu penyakit yang mempengaruhi jutaan orang di seluruh dunia dan menjadi penyebab utama kecacatan dan kematian. Pengidentifikasian dini faktor risiko dan prediksi potensi stroke menjadi sangat penting dalam upaya pencegahan, pengobatan, dan pengelolaan penyakit ini. Dalam beberapa tahun terakhir, teknik-teknik machine learning telah memperoleh perhatian besar dalam bidang medis, khususnya dalam
prediksi dan diagnosis penyakit berdasarkan data klinis.

Stroke merupakan salah satu penyebab utama kematian dan kecacatan di seluruh dunia. Deteksi dini risiko stroke sangat penting untuk mencegah komplikasi serius dan meningkatkan kualitas hidup pasien. Dengan memanfaatkan data kesehatan dan algoritma machine learning, kita dapat membangun model prediksi yang membantu profesional medis dalam mengidentifikasi individu dengan risiko stroke lebih tinggi.

#### Sumber Dataset

Dataset yang digunakan berasal dari kaggle dengan nama **[Stroke Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)**, yang berisi data pasien terkait faktor risiko stroke. Dataset ini banyak digunakan dalam penelitian kesehatan dan tersedia secara publik di berbagai platform data sains.

#### Mengapa Masalah Ini Penting?

- **Pencegahan Dini:** Deteksi risiko stroke dapat mendorong intervensi medis lebih awal.
- **Efisiensi Layanan Kesehatan:** Membantu rumah sakit dan klinik memprioritaskan pasien berisiko tinggi.
- **Pengurangan Biaya:** Mengurangi biaya pengobatan jangka panjang akibat komplikasi stroke.

#### Hasil Riset Terkait

Beberapa penelitian telah menunjukkan bahwa machine learning mampu meningkatkan akurasi prediksi penyakit kronis, termasuk stroke, dibandingkan metode statistik tradisional.

1. FADLI, MUHAMAD, and Rizal Adi Saputra. "Klasifikasi dan evaluasi performa model Random Forest untuk prediksi stroke." Jurnal Teknik 12.2 (2023).
2. Caroline, Cynthia. Penerapan Deep Neural Network dengan Dropout dan CostSensitive Learning untuk Prediksi Penyakit Stroke. Diss. Institut Teknologi Harapan Bangsa, 2022.

---

### Business Understanding

#### Problem Statements

- Bagaimana model machine learning dapat memprediksi kemungkinan seseorang terkena stroke berdasarkan data kesehatan?
- Algoritma mana yang memberikan hasil terbaik dalam hal akurasi prediksi stroke?

#### Goals

- Membangun model prediksi stroke yang akurat menggunakan data kesehatan pasien.
- Mengidentifikasi fitur-fitur kunci yang paling berpengaruh terhadap risiko stroke.
- Mencari algoritma mana yang terbaik untuk prediksi stroke

#### Solution Statements

- Menggunakan algoritma machine learning untuk klasifikasi seperti Random Forest, dan XGBoost.
- Menerapkan teknik deep learning dengan Dense Neural Network atau Fully Connected Network untuk menangkap pola dari data untuk prediksi stroke
- Melakukan evaluasi model menggunakan metrik seperti akurasi, precision, recall, dan F1-score.
- Melakukan hyperparameter tuning untuk meningkatkan performa model.

---

### Data Understanding

#### Deskripsi Dataset

Dataset terdiri dari data pasien dengan berbagai data kesehatan pasien. Setiap baris merepresentasikan satu pasien. Data ini diambil pada tahun 2021 dengan sumber dari kaggle data diupload 4 tahun lalu

#### Fitur pada Dataset

| Nama Kolom        | Deskripsi                                                         | Tipe Data |
| :---------------- | :---------------------------------------------------------------- | :-------- |
| id                | ID unik pasien                                                    | Integer   |
| gender            | Jenis kelamin (Male, Female, Other)                               | Kategori  |
| age               | Usia pasien                                                       | Numerik   |
| hypertension      | Riwayat hipertensi (0: Tidak, 1: Ya)                              | Kategori  |
| heart_disease     | Riwayat penyakit jantung (0: Tidak, 1: Ya)                        | Kategori  |
| ever_married      | Pernah menikah (Yes/No)                                           | Kategori  |
| work_type         | Jenis pekerjaan (Private, Self-employed, Govt_job, children, etc) | Kategori  |
| Residence_type    | Tempat tinggal (Urban/Rural)                                      | Kategori  |
| avg_glucose_level | Rata-rata kadar glukosa darah                                     | Numerik   |
| bmi               | Indeks massa tubuh                                                | Numerik   |
| smoking_status    | Status merokok (never, formerly, smokes, Unknown)                 | Kategori  |
| stroke            | Target (0: Tidak stroke, 1: Stroke)                               | Kategori  |

#### Distribusi Data

Dataset memiliki ribuan baris data pasien dengan distribusi target (stroke) yang sangat tidak seimbang, di mana kasus stroke jauh lebih sedikit dibandingkan non-stroke.

#### Kondisi Data

- **Missing Values:** Kolom `bmi` dan `smoking_status` memiliki beberapa nilai hilang (N/A, Unknown).
- **Keseimbangan Data:** Target stroke sangat minoritas, perlu penanganan imbalance data.
- **Tipe Data:** Kombinasi data numerik dan kategorik.

---

### Data Preparation

#### Tahapan Data Preparation

- **Pembersihan Data:**
  - Menghapus atau mengimputasi nilai hilang pada kolom `bmi` (misal dengan rata-rata/median).
- **Encoding Data Kategorik:**
  - Label encoding untuk target dan fitur biner.
- **Normalisasi Data Numerik:**
  - Standarisasi/normalisasi kolom pada semua kolom kecuali kolom target setelah kolom kategori diubah dengan Label Encoding.
- **Pembagian Data:**
  - Membagi data menjadi training set (70%), validation set (15%) dan test set (15%).

---

### Modeling

#### Model yang Digunakan

1. **Random Forest Classifier**
   - Algoritma ensemble berbasis pohon keputusan.
   - Parameter utama: n_estimators, max_depth, random_state.
2. **XGBoost Classifier**
   - Algoritma boosting yang populer untuk klasifikasi tabular.
   - Parameter utama: learning_rate, n_estimators, max_depth.
3. **Dense Neural Network**
   - Algoritma deep learning untuk klasifikasi tabular.

#### Penanganan Imbalance Data

- Menggunakan teknik oversampling (SMOTE) atau undersampling.

---

### Evaluation

#### Metrik Evaluasi

- **Accuracy:** Persentase prediksi benar.
- **Precision:** Proporsi prediksi positif yang benar-benar positif.
- **Recall:** Proporsi kasus stroke yang berhasil terdeteksi.
- **F1-score:** Harmoni antara precision dan recall.

#### Hasil Evaluasi (Contoh)

| Model         | Accuracy | Precision | Recall | F1-score |
| :------------ | :------- | :-------- | :----- | :------- |
| Random Forest | 0.95     | 0.97      | 0.95   | 0.96     |
| XGBoost       | 0.95     | 0.95      | 0.97   | 0.96     |
| DNN           | 0.86     | 0.88      | 0.83   | 0.85     |

#### Insight

- **Random Forest Classifier** memiliki Accuracy yang tinggi yaitu 95%, dan memiliki Precision yaitu 97% yang artinya model lebih akurat dalam memprediksi class positive atau mengurangi false positive.
- **XGBoost Classifier** memiliki Accuracy yang tinggi yaitu 95%, dan memiliki Precision yaitu 97% yang artinya model lebih akurat dalam memprediksi class positive atau mengurangi false positive. Selain itu model ini memiliki Recall lebih tinggi dari ketiga model yaitu 96% yang artinya model lebih sensitif terhadap class positive atau mengurangi false negative
- **Dense Neural Network** memiliki Accuracy yang rendah dari ketiga model yaitu 86%, model ini memiliki Precision yaitu 88% yang artinya model lebih akurat dalam memprediksi class positive atau mengurangi false positive.

---

### Rekomendasi

- **Peningkatan Data:** Kumpulkan lebih banyak data pasien stroke untuk meningkatkan performa model.
- **Feature Engineering:** Eksplorasi fitur baru atau interaksi antar fitur yang relevan.
- **Model Ensemble:** Gabungkan beberapa model untuk meningkatkan akurasi dan stabilitas prediksi.
- **Implementasi Nyata:** Integrasikan model ke dalam sistem klinik untuk membantu skrining awal risiko stroke.

---

### Catatan

- Dataset memiliki bias kelas yang perlu diatasi pada tahap modeling.
- Evaluasi model harus mempertimbangkan trade-off antara recall (deteksi kasus stroke) dan precision (menghindari false positive).
- Dokumentasi ini mengikuti struktur dan format README.md proyek machine learning pada umumnya.
