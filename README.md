**SENTIMENT ANALYSIS OF USER X ON PUBLIC PERCEPTION AND OPINION ABOUT SCHIZOPHRENIA USING INDOBERT METHOD**


**Deskripsi**

Skripsi ini membahas penerapan model IndoBERT untuk menganalisis sentimen masyarakat Indonesia terhadap skizofrenia melalui platform media sosial X (sebelumnya Twitter). Tujuan dari penelitian ini adalah untuk memahami persepsi publik dan membantu mengidentifikasi potensi stigma atau dukungan terhadap penderita skizofrenia.

**Tujuan**

- Mengidentifikasi kecenderungan opini masyarakat Indonesia terhadap skizofrenia.
- Mengukur performa model IndoBERT dalam klasifikasi sentimen (positif, netral, negatif).

**Dataset**

- Sumber: Platform media sosial X
- Jumlah Tweet: 1004 tweet berbahasa Indonesia
- Periode: 1 Januari – 25 Maret 2024
- Distribusi Sentimen: 150 Positif, 630 Negatif, 220 Netral

**Tools dan Teknologi**
- Bahasa Pemrograman: Python, dijalankan di Google Colab untuk akselerasi GPU.
- Model Bahasa: IndoBERT (pretrained model untuk Bahasa Indonesia), digunakan untuk _fine-tuning_ klasifikasi sentimen.
- _Library NLP_: _Hugging Face Transformers_ (untuk IndoBERT), _Scikit-learn_ (evaluasi, confusion matrix), _Pandas/Numpy_ (manipulasi data), Sastrawi (tokenisasi Bahasa Indonesia), dan library lain seperti _Tweepy/snscrape_ (pengambilan tweet).
- Lingkungan Kerja: Google Colab atau Jupyter Notebook dengan GPU (untuk pelatihan model dalam waktu wajar).

**Metodologi**
1. **Pengumpulan Data (_Crawling_)**: Tweet dikumpulkan dari API X/Twitter berdasarkan kata kunci “skizofrenia” dengan filter bahasa Indonesia. Langkah ini mengikuti praktik analisis sentimen berbasis NLP dengan pengumpulan data teks dari media sosial.
2. **Praseprocessing**: Data teks dibersihkan (menghapus URL, tagar, tanda baca, angka), di-tokenize, dinormalisasi (huruf kecil, stemmer Sastrawi), dan dihitung stopword removal. Hal ini untuk memastikan input berkualitas ke model.
3. **Pelabelan Data**: Setiap tweet diberi label positif, netral, atau negatif terkait persepsi skizofrenia melalui pemeriksaan manual (misalnya dua annotator). Label ini menjadi target kelas untuk pelatihan.
4. **Pelatihan Model**: IndoBERT fine-tuning dilakukan pada data pelatihan yang sudah bersih. Model dilatih untuk memprediksi sentimen tweet. Pendekatan serupa menggunakan IndoBERT telah dilaporkan efektif, karena model ini memahami konteks dua arah dalam bahasa Indonesia.
5. **Evaluasi Model**: Kinerja model diuji pada data uji terpisah. Metode evaluasi mencakup penghitungan akurasi, precision, recall, dan F1-score per kelas menggunakan _confusion matrix_. Laporan klasifikasi (_classification report_) dibangun untuk mengukur performa keseluruhan dan tiap kelas.

**Hasil dan Evaluasi**

Model IndoBERT menghasilkan performa yang baik dalam mengklasifikasikan sentimen tentang skizofrenia. Akurasi keseluruhan mencapai sekitar 0.89 (89%). Rincian metrik per kelas ditampilkan dalam tabel berikut:

<img width="606" height="255" alt="Screenshot 2025-10-06 150949" src="https://github.com/user-attachments/assets/b6328d40-c375-478e-bee0-3764fea0174f" />

Tabel di atas menunjukkan bahwa _F1-score_ tertinggi dicapai pada kelas Positif (0.92) dan terendah pada kelas Netral (0.84). Akurasi 0.89 mengindikasikan model IndoBERT mampu menangkap pola sentimen secara baik. Namun, _F1-score_ yang lebih rendah pada kelas Netral menunjukkan model lebih sulit membedakan tweet bersifat netral karena pola linguistiknya kurang jelas.

**Kesimpulan**

Analisis menunjukkan bahwa masyarakat Indonesia cenderung memiliki sentimen negatif terhadap skizofrenia, mengindikasikan masih adanya stigma. IndoBERT terbukti efektif dalam mengklasifikasikan tweet berbahasa Indonesia meskipun performa terhadap sentimen positif perlu ditingkatkan.

**Saran**

- Menggunakan dataset yang lebih seimbang antar label sentimen
- Menguji varian lain dari IndoBERT seperti IndoBERT-Lite atau IndoBERT-Large
- Meningkatkan jumlah _epoch_ dan teknik regularisasi
