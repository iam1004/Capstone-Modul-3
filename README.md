# Angel_Capstone3 - Hotel Booking Demand

## Overview

Dalam industri perhotelan, mengelola pembatalan dan ketidakdatangan sangat penting untuk menjaga profitabilitas dan efisiensi operasional. Para manajer hotel akan terkena dampak langsung dari jumlah pembatalan, yang memengaruhi ketersediaan kamar, staf, dan perkiraan pendapatan. 

Maka dari itu, dengan mengumpulkan data dari pemesanan sebelumnya, Hotel ingin mengetahui pesanan mana yang kiranya akan dibatalkan atau pun tidak dengan membuat model. Model akan diterapkan untuk memprediksi kemungkinan pembatalan pada saat konfirmasi pemesanan.

Dengan hasil model ini, **Manajer hotel** dapat memprediksi pembatalan terlebih dahulu, memungkinkan mereka untuk menetapkan ulang ruangan atau mengelola daftar tunggu dengan lebih efisien. Dan **Tim pemasaran** dapat menyesuaikan penawaran dan komunikasi untuk mengurangi pembatalan dari pelanggan berisiko tinggi dengan memahami faktor risiko pembatalan. **Tim Front Desk & Layanan Pelanggan** juga dapat menjangkau pelanggan secara lebih proaktif dengan menawarkan insentif untuk mencegah pembatalan, atau menyesuaikan ekspektasi pelanggan.

## Problem Statement

Pembatalan yang tidak diantisipasi dapat menyebabkan hilangnya pendapatan, terutama selama musim puncak atau ketika kamar dipesan digunakan sebagai cadangan bagi pelanggan dalam daftar tunggu. Dengan memprediksi pembatalan pemesanan sebelum terjadi, hotel dapat mengelola inventarisnya dengan lebih baik, mengoptimalkan strategi pemesanan, dan meningkatkan layanan pelanggan.

## Goals

**Tujuan utama** dari proyek ini adalah untuk membangun model pembelajaran mesin yang dapat memprediksi status pembatalan pemesanan berdasarkan data historis pemesan sebelumnya. Dengan klasifikasi biner, kita akan mendapatkan hasilnya (variabel target) yang berupa: 

- 1: Pemesanan dibatalkan
- 0: Pemesanan tidak dibatalkan

Selain itu, kita juga dapat **Identifikasi Prediktor Utama Pembatalan**, dengan wawasan yang kita dapatkan tentang fitur mana (misalnya, segmen pasar, jumlah perubahan pemesanan, jenis deposit) yang memiliki dampak paling signifikan terhadap kemungkinan pembatalan.

## Analytic Approach

Yang pertama, kita akan melakukan *Feature Selection* untuk memilih fitur-fitur yang berguna dan berpengaruh untuk diinput pada model (contoh : `previous_cancellations` dan `booking_changes` mungkin berkorelasi, jika kedua fitur ini sangat berkorelasi, kami mungkin mempertimbangkan untuk mempertahankan salah satunya saja), lalu kita juga akan melakukan *Feature Engineering* dengan mengunakan fitur-fitur yang disediakan untuk menciptakan wawasan tambahan jika diperlukan (contoh : Menggabungkan `previous_cancellations` dan `booking_changes` untuk membuat fitur "riwayat pembatalan" atau Mengkodekan variabel kategori menjadi numerikal seperti `market_segment`, `deposit_type`, dan `Reserved_room_type` untuk pembelajaran mesin)

Selanjutnya, kita akan masuk pada tahap *Model Selection* menguji model dengan melatih dan mengevaluasi model-model klasifikasi seperti Logistic Regression, K-Nearest Neighbors (KNN), Decision Tree Classifier, Random Forest Classifier, XGBoost Classifier, LightGBM Classifier dan Gradient Boosting Classifier. Lalu kita akan membandingkan performa model dengan metriks Akurasi, Presisi, Skor F1 dan AUC.

Dari hasil ini, kita dapat menentukan model mana yang performanya paling bagus dan kita akan lanjut pada tahap *Hyperparameter Tuning*, pada tahap ini, kita akan mencari value untuk hyperparameter. Lalu kita akan mengevaluasi performa model sebelum dan sesudah tuning.

## Metric Evaluation

Metrik evaluasi harus dipilih berdasarkan masalah bisnis dan bagaimana pemangku kepentingan akan menggunakan model tersebut. Karena model ini akan membantu dalam memprediksi pembatalan, metrik berikut akan sangat relevan:
- Accuracy and Precision: Memastikan bahwa model tidak memprediksi pembatalan secara berlebihan, meminimalkan jumlah prediksi pembatalan yang salah, yang dapat menyebabkan hilangnya pendapatan jika tindakan diambil terlebih dahulu.
- Recall: Mengukur seberapa baik model mampu mengidentifikasi pemesanan yang benar-benar akan dibatalkan. Dengan kata lain, recall mengevaluasi kemampuan model untuk mendeteksi pembatalan sebelum terjadi, sehingga hotel dapat mengambil tindakan yang tepat (misalnya mengelola inventaris kamar, menyesuaikan harga, menawarkan insentif untuk menghindari pembatalan, dll.).
- Skor F1: Metrik yang seimbang antara presisi dan perolehan, yang mencerminkan efektivitas model secara keseluruhan dalam memprediksi pembatalan.
- Important Features: Mengetahui fitur mana yang paling berpengaruh pada pembatalan untuk mengoptimalkan stategi pemesanan dan meningkatkan layanan pelanggan agar lebih tepat sasaran.
