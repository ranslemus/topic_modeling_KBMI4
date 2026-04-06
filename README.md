## !! PENTING !! Perintah Git untuk Inisialisasi Proyek

cd "jalur/ke/folder/proyek/kalian"
git clone https://github.com/ranslemus/topic_modeling_KBMI4.git

## Please buat branch baru, kita ga merge2 ke main, karena nanti buat main adalah kerjaan yang paling optimal
git checkout -b (nama branch baru)
git status
git add assets/kamus_slang_bank.json
git commit -m "Update: ...."
git push origin (nama branch baru)

## Gausah gabung ke main


# 🏦 Identifikasi Keluhan Nasabah Bank KBMI 4 Berbasis Aspek 
### Pendekatan Hybrid IndoBERT dan BERTopic

Proyek ini adalah bagian dari penelitian skripsi untuk melakukan pemodelan topik (topic modeling) pada ulasan aplikasi mobile banking Bank KBMI 4 (BCA, BRI, Mandiri, BNI) menggunakan integrasi model **IndoBERT** untuk *embedding* dan **BERTopic** untuk klasterisasi aspek keluhan.

---

## 👥 Anggota Tim (Project Members)
* **Gavriel Sebastian Christianus** (2702300221)
* **Reuben Anselmus Adel** (2702314901)
* **Neil Jovianus Sumarta** (2702224212)
* **Dosen Pembimbing:** Samuel Philip, S. Kom., M. Kom. (D6825)

---

## 🚀 Gambaran Umum Proyek
Tujuan utama proyek ini adalah mengotomatisasi identifikasi keluhan utama nasabah dari Google Play Store yang bersifat tidak terstruktur. Dengan menggunakan pendekatan *Hybrid*, kita mengharapkan hasil klasterisasi yang lebih koheren dan sensitif terhadap konteks bahasa Indonesia (slang, singkatan, dan *code-switching*).

**Target Bank:**
1. PT Bank Central Asia Tbk (BCA mobile & myBCA)
2. PT Bank Rakyat Indonesia (Persero) Tbk (BRImo)
3. PT Bank Mandiri (Persero) Tbk (Livin’ by Mandiri)
4. PT Bank Negara Indonesia (Persero) Tbk (BNI Mobile Banking)

---

## INSTRUKSI TIM
1. Gunakan Python 3.10+
2. Update Library: Jika ada perubahan di requirements.txt, segera jalankan:
pip install -r requirements.txt
3. Patuhi config.yaml: Jangan mengubah parameter min_cluster_size atau n_neighbors di file lokal tanpa diskusi tim. Jika menemukan parameter yang lebih baik, update di repo agar semua orang menggunakan setting yang sama.
4. Kamus Slang (Dictionary): Jika kamu menambahkan kata baru di assets/kamus_slang_bank.json, segera commit agar proses preprocessing teman yang lain tidak berbeda hasilnya.
5. Random Seed: Kita menggunakan seed: 42. Jangan diubah agar hasil klasterisasi tetap reproducible.


## 🛠️ Struktur Folder
```text
.
├── assets/             # Kamus slang dan daftar stopwords
├── data/               
│   ├── raw/            # File CSV hasil scraping mentah
│   └── processed/      # Data yang sudah dibersihkan
├── logs/               # Catatan training model
├── results/            # Visualisasi, model .pkl, dan hasil topik
├── config.yaml         # SINGLE SOURCE OF TRUTH (Parameter Utama)
└── requirements.txt    # Daftar library Python
// FILE KERJA (tentative)
├── preprocess.py       # Script pembersihan teks
└── train_hybrid.py     # Script utama training model