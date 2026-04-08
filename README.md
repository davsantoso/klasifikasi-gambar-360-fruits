
---
# 🍎 Fruit Image Classification using CNN (TensorFlow)

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi **Convolutional Neural Network (CNN)** menggunakan TensorFlow/Keras untuk melakukan klasifikasi gambar buah.

Dataset yang digunakan adalah **Fruits 360**, yang berisi puluhan ribu gambar buah dengan berbagai kelas.

Model berhasil mencapai **akurasi 100% pada training dan testing set** untuk 20 kelas yang digunakan dalam eksperimen ini.
---

## 🎯 Tujuan Proyek

Proyek ini dibuat untuk memenuhi kriteria berikut:

- Menggunakan dataset minimal 10.000 gambar
- Memiliki minimal 3 kelas
- Menggunakan model Sequential dengan Conv2D dan Pooling Layer
- Mengimplementasikan Callback
- Mencapai akurasi minimal 95%
- Menyimpan model dalam format:
  - SavedModel
  - TensorFlow Lite (TF-Lite)
  - TensorFlow.js (TFJS)
- Melakukan inference menggunakan model yang telah disimpan

---

## 📂 Dataset

Dataset: **Fruits 360**

Karakteristik dataset:

- Gambar berukuran 100x100 piksel
- Background putih
- Objek buah berada di tengah
- Tersedia folder Training dan Test
- Total gambar > 90.000

Dalam proyek ini digunakan **20 kelas buah** dengan total data jauh di atas 10.000 gambar.

---

## 🏗 Arsitektur Model

Model dibangun menggunakan `Sequential` API dengan struktur berikut:

- Conv2D (32 filters) + BatchNormalization + MaxPooling
- Conv2D (64 filters) + BatchNormalization + MaxPooling
- Conv2D (128 filters) + BatchNormalization + MaxPooling
- Conv2D (256 filters) + MaxPooling
- Flatten
- Dense (256) + Dropout
- Dense (Softmax)

Optimizer: Adam
Loss Function: Categorical Crossentropy
Metrics: Accuracy

---

## 🔁 Callback

Model menggunakan EarlyStopping:

- Monitor: `val_accuracy`
- Patience: 5
- Restore best weights: True

Tujuan callback adalah untuk mencegah overfitting dan menghentikan training secara otomatis ketika performa validasi tidak meningkat.

---

## 📊 Hasil Training

Hasil akhir:

- Training Accuracy: 100%
- Validation Accuracy: 100%
- Testing Accuracy: 100%

Classification report menunjukkan precision, recall, dan f1-score sebesar 1.00 pada seluruh kelas.

---

## 📈 Visualisasi

Proyek ini menampilkan:

- Grafik accuracy vs epoch
- Grafik loss vs epoch

Visualisasi digunakan untuk menganalisis proses pembelajaran model dan memastikan tidak terjadi overfitting.

---

## 💾 Format Model yang Disimpan

Model disimpan dalam tiga format:

### 1️⃣ Keras Format

```
model.keras
```

### 2️⃣ SavedModel

```
saved_model_fruits/
```

Digunakan untuk deployment dan konversi ke TF-Lite dan TFJS.

### 3️⃣ TensorFlow Lite

```
fruits_model.tflite
```

Digunakan untuk deployment pada perangkat mobile atau embedded.

### 4️⃣ TensorFlow.js

```
tfjs_model/
```

Digunakan untuk deployment pada browser berbasis JavaScript.

---

## 🔍 Inference

Inference dilakukan dengan:

- Load model yang telah disimpan
- Memproses 1 gambar uji
- Melakukan prediksi kelas
- Menampilkan confidence score

Contoh output inference:

```
Prediksi: Apple Red 1
Confidence: 0.99
```

Screenshot hasil inference disertakan pada notebook.

---

## 🚀 Cara Menjalankan Proyek

### 1️⃣ Jalankan di Google Colab dengan GPU (T4)

Aktifkan:

```
Runtime → Change runtime type → GPU
```

### 2️⃣ Install dependencies

```
pip install tensorflow tensorflowjs kagglehub
```

### 3️⃣ Download dataset

Menggunakan kagglehub:

```
moltean/fruits
```

### 4️⃣ Jalankan seluruh cell notebook

---

## 📦 Requirements

File `requirements.txt` dapat dibuat dengan:

```
pip freeze > requirements.txt
```

---

## 🧠 Insight

Akurasi tinggi (100%) dimungkinkan karena:

- Background seragam
- Objek terpusat
- Resolusi konsisten
- Variasi noise rendah

Dataset ini relatif mudah untuk CNN sehingga model sederhana mampu mencapai performa maksimal.

---
