## !! PENTING !! Perintah Git untuk Inisialisasi Proyek
```
cd "jalur/ke/folder/proyek/kalian"<br>
git clone https://github.com/ranslemus/topic_modeling_KBMI4.git
```

## !! PENTING !! Please buat branch baru, kita ga merge2 ke main, karena  main nnti adalah kerjaan yang paling optimal
```
git checkout -b (nama branch baru)
git status
git add assets/kamus_slang_bank.json
git commit -m "Update: ...."
git push origin (nama branch baru)
```
## ONLY TIME TO PULL DARI MAIN IS TO SYNC CONFIG & DATA. Kalo udah di branch kalian, pasti from time to time config dan data akan diubah. Cara update semua file tersebut:
1. Update catatan dari server (tanpa menggabungkan apapun dulu)<br>
```
git fetch origin main<br>
```
2. Ambil file spesifik dari pusat (main) ke branch lokal sekarang<br>
```
git checkout origin/main -- config.yaml requirements.txt assets/ data/
```
3. Simpan perubahan sinkronisasi tersebut<br>
```
git commit -m "pesan commit"
```

--- 

## Kerjaan admin
1. Pastikan kamu di main <br>
```
git checkout main
```
2. Edit file config.yaml (pakai VS Code/Notepad)<br>

3. Simpan dan kirim ke pusat<br>
```
git add config.yaml
git commit -m "Admin: Update n_neighbors di config"
git push origin main
```

# !! Gausah merge ke main !!

---

## INSTRUKSI TIM
1. Python 3.10+
2. Patuhi config.yaml: Jangan mengubah parameter min_cluster_size atau n_neighbors di file lokal tanpa diskusi tim. Jika menemukan parameter yang lebih baik, update di repo agar semua orang menggunakan setting yang sama.
3. Kamus Slang (Dictionary): Jika kamu menambahkan kata baru di assets/kamus_slang_bank.json, segera commit agar proses preprocessing teman yang lain tidak berbeda hasilnya.
4. Random Seed: seed -> 42.

---



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