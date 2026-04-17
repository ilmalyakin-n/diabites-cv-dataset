# 👁️ DiaBites: Nutrition Label Object Detection (YOLOv11 Dataset)

Repositori ini berfokus pada tahapan penyediaan, anotasi, dan rekayasa dataset *Computer Vision* untuk proyek **DiaBites**. Tujuan utama dari *pipeline* ini adalah mendeteksi dan melakukan *cropping* pada area "Informasi Nilai Gizi" pada kemasan makanan/minuman di Indonesia sebelum data tersebut diekstraksi oleh mesin OCR (*Optical Character Recognition*).

Sebagai luaran teknis dari tim Data Science, repositori ini berisi dataset mentah, dataset berformat YOLO, serta skrip eksperimental untuk melatih model deteksi objek menggunakan **YOLOv11** sebagai *proof-of-concept* kelayakan data.

🔗 **Tautan Penting:**
* **Roboflow Universe (Dataset Asli):** [InformasiGiziApp-vieqt](https://universe.roboflow.com/infogizi/informasigiziapp-vieqt)
* **Google Colab Notebook:** [YOLOv11_Training_Pipeline.ipynb](https://colab.research.google.com/drive/1XseChtTAsytjUPeQrLuzf0CL9IOfYzhT?usp=sharing)
* **Pembagian Dataset (Google Drive):** [all_images & all_labels](https://drive.google.com/drive/folders/1TlzNg-VV2iqdqtRAUAWbH0ir_ido4ak3?usp=sharing)
* **Unduh Dataset & Model (Releases):** [Tautan ke halaman GitHub Releases kamu]

---

## 📂 Struktur Data & Aset (Tersedia di GitHub Releases)

Untuk menjaga performa repositori, seluruh file dataset dan bobot model biner (.pt) yang berukuran besar dikompresi dan diunggah ke bagian **Releases**.

* 📁 `raw_dataset.zip` (Tersedia di Releases): Berisi arsip mentah berupa **1.741 gambar** kemasan produk Indonesia (`all_images`) beserta file anotasi labelnya (`all_labels`) yang diekspor dari Roboflow.
* 📁 `yolov11_ready_dataset.zip` (Tersedia di Releases): Berisi dataset yang sudah melalui proses pembagian (*Train, Valid, Test*) dan diformat khusus untuk arsitektur YOLOv11 (`InformasiGiziApp.v4i.yolov11`).

---

## 💻 Source Code & Hasil Evaluasi (Di Repositori Ini)

File-file di bawah ini tersedia langsung di dalam *branch* utama repositori untuk kebutuhan dokumentasi dan *reproducibility*.

### 1. Skrip Pelatihan (Training Pipeline)
* 📓 `training_yolo11.ipynb`: *Jupyter Notebook* yang dijalankan di Google Colab. Berisi alur kerja (*pipeline*) untuk mengunduh dataset dari Roboflow, mengatur *environment* Ultralytics YOLOv11, melakukan proses *training* dengan penyesuaian *hyperparameter*, hingga proses inferensi dan penyimpanan model akhir (`best.pt`).

### 2. Evaluasi Model (Folder `Program/`)
Folder ini berisi visualisasi dan metrik hasil *training* yang dilakukan oleh tim Data Science untuk memvalidasi bahwa dataset sudah anotasi dengan benar dan model mampu belajar membedakan area target.
*  `confusion_matrix.png`: Hasil akurasi deteksi *bounding box*.
*  `results.png`: Grafik penurunan *loss* selama *epoch* pelatihan.
*  `val_batch0_labels.jpg`: Contoh prediksi *bounding box* model terhadap area Informasi Nilai Gizi pada *validation set*.

---

## 🚀 Peran Repositori dalam Arsitektur DiaBites

Pembuatan model YOLOv11 di dalam repositori ini bertindak sebagai **sarana eksperimental (Proof-of-Concept)** oleh tim Data Science. 
Hal ini bertujuan untuk memastikan dataset 1.741 gambar yang telah dianotasi memiliki kualitas yang cukup (*high mAP*) untuk dilatih. Model (`best.pt`) dan dataset ini selanjutnya akan diserahkan kepada divisi **AI Engineer** untuk diintegrasikan ke dalam layanan *Backend* berbasis FastAPI/Flask sebagai tahap prapemrosesan (memotong gambar secara otomatis) sebelum dikirim ke mesin OCR untuk ekstraksi teks gizi.

---
*Dikembangkan oleh Tim Data Science DiaBites*
