# Latar Belakang (konteks)
Sebuah bank yang menawarkan produk deposit berjangka. Setiap baris merepresentasikan satu calon nasabah yang dihubungi oleh tim marketing, dengan informasi terkait karakteristik pribadi (usia, pekerjaan), informasi ekonomi (saldo, pinjaman, perumahan, dll), serta hasil panggilan sebelumnya. Tujuan dari dataset ini adalah untuk memahami karakteristik dan perilaku nasabah yang cenderung melakukan deposit.

# Bussines Problem
Tim marketing memiliki keterbatasan sumber daya (tenaga dan waktu) dalam melakukan panggilan promosi. Tanpa model prediksi, setiap calon nasabah dihubungi secara acak yang dapat menyebabkan banyak panggilan tidak menghasilkan konversi (nasabah tidak tertarik untuk melakukan deposit).
Masalah bisnis utamanya adalah: "Bagaimana mengurangi jumlah panggilan yang tidak efektif tanpa menurunkan jumlah nasabah yang melakukan deposit?

# Goals
Tujuan analisis ini adalah membangun model machine learning yang mampu:
  1. Memprediksi apakah calon nasabah akan melakukan deposit setelah dihubungi menggunakan model machine learning.
  2. Membantu tim marketing menargetkan panggilan hanya kepada calon nasabah yang berpotensi tinggi untuk konversi.
  3. Mengukur seberapa besar penghematan biaya operasional yang dapat dicapai dengan menggunakan model dibandingkan tanpa model.

# Approach
  1. Melakukan pembersihan dan praproses data, termasuk encoding variabel kategorikal dan transformasi numerik menggunakan scaling dan tanpa scaling.
  2. Membangun pipeline dengan dua model utama:
      - Baseline model: Memilih salah satu dari 7 model.
      - Tuned model: menggunakan baseline model terbaik dengan optimasi hyperparameter.
  3. Melakukan pembagian data train dan test.
  4. Mengevaluasi performa model dengan metrik utama F1-score, karena metrik ini menyeimbangkan precision dan recall.
      - Precision = seberapa banyak nasabah yang benar deposit dari semua jumlah nasabah yang diprediksi akan deposit oleh model.
      - Recall = seberapa banyak calon nasabah melakukan deposit yang berhasil ditangkap model.
  5. Mengevaluasi hasil dengan confusion matrix, precision-recall curve, Classification Report dan SHAP values untuk interpretabilitas.

# Data
- Fitur numerik:
  - age : Umur nasabah
  - balance : Rata-rata saldo
  - campaign : Jumlah kontak selama campaign
  - pdays : Jumlah hari sejak kontak terakhir
- Fitur kategori:
  - job : Jenis pekerjaan
  - housing : Status pinjaman rumah
  - loan : Status pinjaman pribadi
  - contact : Jenis kontak komunikasi
  - month : Bulan kontak terakhir
  - poutcome : Hasil campaign sebelumnya
- Target:
  - deposit : Target (yes/no)

# Hasil dan Kesimpulan
  1. Kesimpulan Teknikal
      - Model LGBM dengan hyperparameter tuning memberikan performa terbaik dengan F1 Test = 0.70 dan PR-AUC = 0.81.
      - Tuning meningkatkan keseimbangan precision dan recall tanpa menyebabkan overfitting.
      - Berdasarkan evaluasi confusion matrix, model mampu mengurangi panggilan salah target (FP) dan menambah panggilan yang tepat (TP).
      - Model ini cocok untuk digunakan pada data kampanye aktual karena performanya stabil dan generalisasi baik.
  2. Kesimpulan Finansial
      - Model LGBM menghasilkan efisiensi biaya dan tenaga dengan tetap mempertahankan efektivitas prediksi tinggi.
      - Dalam jangka panjang, penerapan model serupa pada skala ribuan kampanye dapat menghemat tenaga dan biaya kampanye per tahun dan meningkatkan ROI marketing.
