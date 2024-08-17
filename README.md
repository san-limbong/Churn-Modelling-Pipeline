# Proyek Pengembangan dan Pengoperasian Sistem Machine Learning Pipeline Menggunakan Apache Beam

![dataset-cover churn](https://github.com/user-attachments/assets/9bd2e156-185c-41bf-af33-dc2cc7041ba7)


| | Deskripsi |
| ----------- | ----------- |
| Dataset | [Churn Modelling](https://www.kaggle.com/datasets/shrutimechlearn/churn-modelling/data) |
| Masalah | Dalam industri perbankan, memahami faktor-faktor yang menyebabkan nasabah meninggalkan bank adalah hal yang sangat penting. Dataset ini menyediakan rincian mengenai nasabah sebuah bank, termasuk atribut-atribut seperti negara asal, jenis kelamin, usia, lamanya menjadi nasabah, saldo rekening, jumlah produk bank yang digunakan, kepemilikan kartu kredit, status keaktifan sebagai anggota, dan estimasi gaji. Tujuan utama dari analisis ini adalah untuk mengidentifikasi pola dan faktor-faktor yang signifikan yang mempengaruhi keputusan nasabah untuk meninggalkan bank. Dengan mengetahui faktor-faktor ini, bank dapat merancang strategi yang lebih efektif untuk mempertahankan nasabahnya dan mengurangi tingkat churn. Model prediksi yang dibangun dari data ini dapat membantu bank dalam melakukan intervensi yang lebih tepat waktu dan sasaran dalam usaha mempertahankan nasabah, sehingga meningkatkan kepuasan dan loyalitas nasabah. |
| Solusi machine learning | Solusi yang akan dibangun adalah model klasifikasi menggunakan neural network yang dapat membantu mendeteksi kemungkinan seorang nasabah bank melakukan churn. |
| Metode pengolahan | Data bank pelanggan diproses melalui beberapa tahap menggunakan komponen-komponen TFX. Tahapan pemrosesan dimulai dengan pembacaan data dari direktori yang ditentukan melalui CsvExampleGen, yang membagi data menjadi dua bagian, yaitu pelatihan dan evaluasi. Statistik data kemudian dihasilkan oleh StatisticsGen, sementara skema data ditentukan oleh SchemaGen. ExampleValidator memastikan bahwa data tersebut sesuai dengan skema yang ditentukan. Selanjutnya, transformasi data dilakukan menggunakan modul transformasi khusus yang mengonversi fitur kategorikal menjadi vektor satu-hot dan mengubah fitur numerik menjadi skala antara 0 dan 1. |
| Arsitektur model | Model didefinisikan menggunakan Keras dengan input berupa fitur kategorikal yang di-one-hot encoding dan fitur numerik yang telah diskalakan. Input ini kemudian dikombinasikan melalui lapisan concatenate. Lapisan-lapisan dense berturut-turut dengan aktivasi ReLU kemudian digunakan untuk membuat model lebih dalam dan kompleks, dengan lapisan-lapisan berukuran 256, 64, dan 16 unit. Akhirnya, model menghasilkan output melalui lapisan dense dengan satu neuron dan fungsi aktivasi sigmoid, yang digunakan untuk klasifikasi biner. Model ini dioptimasi menggunakan Adam dengan laju pembelajaran 0.001, dan metrik yang digunakan adalah akurasi biner. Model kemudian dilatih dengan data yang telah diproses sebelumnya, serta diintegrasikan ke dalam pipeline TFX untuk pengujian dan evaluasi lebih lanjut. |
| Metrik evaluasi | Metrik yang digunakan meliputi Area Under Curve (AUC) untuk menilai area di bawah kurva ROC, False Positive untuk menghitung kesalahan klasifikasi data negatif sebagai positif, False Negative untuk menghitung kesalahan klasifikasi data positif sebagai negatif, True Positive untuk mengukur klasifikasi positif yang benar, True Negative untuk mengukur klasifikasi negatif yang benar, dan Binary Accuracy untuk mengukur proporsi prediksi yang benar dalam masalah klasifikasi biner. |
| Performa model | Model ini menunjukkan kinerja yang sangat baik pada data pelatihan dengan nilai loss sebesar 0.0414 dan akurasi binary sebesar 98.52%. Namun, pada data validasi, performanya menurun, dengan nilai loss sebesar 2.0221 dan akurasi binary sebesar 80.87%. Perbedaan performa yang cukup besar antara data pelatihan dan data validasi menunjukkan bahwa model mengalami overfitting. |
| Opsi deployment | Tahap deployment dilakukan menggunakan Railway, sebuah platform yang memungkinkan para pengembang untuk dengan mudah menerapkan aplikasi, termasuk model pembelajaran mesin, ke lingkungan produksi. |
| Web app | Tautan web app [Churn-model](https://churn-modelling-pipeline-production.up.railway.app/v1/models/churn-model/metadata)|
| Monitoring | Pemantauan layanan ini dilakukan menggunakan Prometheus, sebuah layanan sumber terbuka. Hal ini memungkinkan pemantauan perubahan, seperti perubahan jumlah permintaan, secara efektif. |

# Sekilas Mengenai Pipeline Orchestrator
Machine learning pipeline terdiri dari berbagai proses yang saling bergantung dan harus dilakukan dalam urutan yang benar. Pipeline orchestrator bertugas memastikan bahwa semua komponen dijalankan sesuai urutan yang ditentukan.

![beam](https://github.com/user-attachments/assets/a3924295-09ee-46df-9950-fb9cb98e37e3)

Pipeline orchestration mengelola alur kerja berdasarkan ketergantungan tugas dalam grafik pipeline yang bersifat directed dan acyclic. "Directed" berarti alur kerja mengikuti ketergantungan tugas, sedangkan "acyclic" berarti tidak ada siklus dalam alur kerja yang menghubungkan kembali ke tugas yang telah diselesaikan. Karena sifat-sifat ini, pipeline orchestration sering disebut sebagai directed acyclic graphs (DAGs).

TFX sebagai pipeline machine learning end-to-end mendukung berbagai pipeline orchestrator, seperti Apache Beam, Apache Airflow, dan Kubeflow Pipeline. Dalam proyek ini, kita akan menggunakan Apache Beam sebagai pipeline orchestrator untuk mengatur alur kerja pipeline machine learning.

Perlu diketahui bahwa Apache Beam adalah salah satu dependensi yang secara otomatis terinstal saat Anda menginstal TFX, sehingga Anda bisa langsung menggunakannya tanpa perlu instalasi tambahan.


# Proyek Menggunakan TensorFlow Extended (TFX) untuk Membuat Machine Learning Pipeline
Machine learning pipeline dibuat menggunakan komponen yang sebagai berikut:
- ExampleGen
- StatisticGen
- SchemaGen
- ExampleValidator
- Transform
- Trainer
- Resolver
- Evaluator
- Pusher
  
Nb: Seluruh komponen di atas dijalankan menggunakan Pipeline Orchestrator yakni Apache Beam

# Pemantauan Sistem Machine Learning Menggunakan Prometheus

![san-limbong-monitoring](https://github.com/user-attachments/assets/26b67f3f-c7e9-4cad-b164-6a47bed35f31)


# Menjalankan dengan docker

Membuat docker image 

```bash
docker build -t churn-monitoring .\monitoring\
```

Menjelankan docker image dan menentukan port. Ingat bahwa di dalam docker container TF Serving menggunakan port 8501.

```bash
docker run -p 9090:9090 churn-monitoring  
```
