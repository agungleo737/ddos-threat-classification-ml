# DDoS Threat Classification using Decision Tree & Random Forest

Proyek klasifikasi ancaman keamanan siber untuk mendeteksi serangan **DDoS** pada lalu lintas jaringan (*network flow*) menggunakan pendekatan *Supervised Learning* (Decision Tree dan Random Forest).

## Deskripsi Proyek
Pertumbuhan volume lalu lintas jaringan membuat metode deteksi konvensional sulit mengenali pola serangan secara akurat. Model ini mempelajari pola statistik dari *network flow* untuk membedakan trafik normal (**BENIGN**) dan serangan **DDoS**.

* **Nama:** Leo Agung Christian
* **NIM:** 2411501212
* **Tema:** Security Log Analytics and Threat Classification

## Dataset
* **Sumber:** [CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) (`Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv`)
* **Ukuran Awal:** 225.745 baris, 79 kolom
* **Ukuran Setelah Cleaning:** 223.082 baris bersih (128.014 DDoS / 57,38% dan 95.068 BENIGN / 42,62%)

## Pipeline Pengerjaan
1. **Data Cleaning:** Konversi nilai `inf`/`-inf` ke `NaN`, penghapusan 68 *missing values* dan 2.633 baris duplikat.
2. **EDA:** Statistik deskriptif, distribusi kelas, *heatmap* korelasi 10 fitur teratas, dan *boxplot* perbandingan fitur utama.
3. **Feature Engineering:** *Label Encoding*, pembuangan 10 kolom konstan, seleksi 20 fitur berkorelasi tertinggi, *stratified split* 80:20, dan `StandardScaler`.
4. **Model Development & Evaluation:** Pelatihan dan perbandingan performa **Decision Tree** dan **Random Forest**.

## Hasil Evaluasi

| Model | Accuracy | Precision | Recall | F1-Score | FP | FN | Train Time |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Decision Tree** | 99.9552% | 99.9844% | 99.9375% | 99.9609% | 4 | 16 | 0.64s |
| **Random Forest** | **99.9574%** | **99.9883%** | **99.9375%** | **99.9629%** | **3** | **16** | 13.18s |

**Kesimpulan:** Random Forest memberikan performa terbaik secara keseluruhan dengan tingkat kesalahan klasifikasi (*False Positive*) paling minimal.

## Cara Menjalankan
1. Unduh dataset `Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv` dari situs resmi CIC-IDS2017.
2. Buka `UTS_2411501212.ipynb` di Google Colab atau Jupyter Notebook.
3. Letakkan file CSV pada direktori kerja (atau `/content/sample_data/` di Colab), lalu klik **Run All**.
