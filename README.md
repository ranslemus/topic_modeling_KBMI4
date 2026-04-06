# ‼️TEAM PLEASE READ‼️ 
## !! PENTING !! Perintah Git untuk Inisialisasi Proyek
```
cd "jalur/ke/folder/proyek/kalian"
git clone https://github.com/ranslemus/topic_modeling_KBMI4.git
```

## !! PENTING !! Do this only ONCE. Please buat branch baru, kita ga merge2 ke main, karena  main nnti adalah kerjaan yang paling optimal
```
git checkout -b (nama branch baru)
git status
git add (apa aja yang di add)
git commit -m "Update: ...."
git push origin (nama branch baru)
```

## ONLY TIME TO PULL DARI MAIN IS TO SYNC CONFIG & DATA. INI YG HARUS DILAKUIN RUTIN. Kalo udah di branch kalian, pasti from time to time config dan data akan diubah. Cara update semua file tersebut:
1. Update catatan dari server (tanpa menggabungkan apapun dulu)<br>
```
git fetch origin main
```
2. Ambil file spesifik dari pusat (main) ke branch lokal sekarang, FILE YANG PERLU DIUPDATE BIASANYA YNG DI COMMAND INI DOANG<br>
```
git checkout origin/main -- config.yaml requirements.txt assets/ data/ README.md
```
3. Simpan perubahan sinkronisasi tersebut<br>
```
git commit -m "pesan commit"
```

4. Push ke branch u<br>
```
git push origin (nama branch lu)
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

---

## INSTRUKSI TIM
1. Python 3.10+
2. Patuhi config.yaml: Jangan mengubah parameter min_cluster_size atau n_neighbors di file lokal tanpa diskusi tim. Jika menemukan parameter yang lebih baik, update di repo agar semua orang menggunakan setting yang sama.
3. Kamus Slang (Dictionary): Jika kamu menambahkan kata baru di assets/kamus_slang_bank.json, segera commit agar proses preprocessing teman yang lain tidak berbeda hasilnya.
4. Random Seed: seed -> 42.

---

## CARA PEMAKAIAN config.yaml FILE

1. Install pyyaml
```
pip install pyyaml
```
2. Baca config di python:
```
import yaml
def load_config(config_path="config.yaml"):
    with open(config_path, "r") as f:
        return yaml.safe_load(f)
config = load_config()
```

3.  Sekarang kalian bisa akses isi config seperti dictionary Python
```
print(f"Project Name: {config['project']['name']}") <- kalo akses yang nested kek gini
print(f"Using Model: {config['indobert']['model_name']}") <- kalo akses yang nested kek gini
```


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