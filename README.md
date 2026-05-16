# kata_dospem_kalo_ikut_auto_A_code
Pengumpulan code case 1, bigdata Challenge, Satria Data, Telkom University

## Deskripsi
 
Notebook ini berisi pipeline lengkap untuk klasifikasi tweet terkait program Makan Bergizi Gratis (MBG) ke dalam 8 kelas menggunakan pendekatan ensemble fine-tuning pretrained language model.
 
**Model yang digunakan:**
- IndoBERTweet (`Aardiiiiy/indobertweet-base-Indonesian-sentiment-analysis`)
- XLM-RoBERTa Large (`FacebookAI/xlm-roberta-large`)
**Strategi:** 5-Fold Stratified Cross Validation → Weighted Soft Voting Ensemble
 
**Metrik evaluasi:** Balanced Accuracy
 
---
 
## Struktur File
 
```
├── kata dospem kalo ikut auto A.ipynb     # Notebook utama
├── case_1_labeled_data.xlsx  # Data latih berlabel (5.000 tweet)
├── case_1_text_to_predict.xlsx # Data uji (1.500 tweet)
├── case_1_template_sheet.xlsx  # Template jawaban
└── README_case1.md           # Dokumentasi ini
```
 
---
 
## Requirements
 
```
torch
transformers
scikit-learn
pandas
openpyxl
numpy
matplotlib
seaborn
wordcloud
accelerate
```
 
 
## Cara Menjalankan
 
**Platform yang direkomendasikan:** Google Colab Pro (GPU A100/L4)  
**Minimum:** Google Colab gratis (GPU T4 16GB)
 
### Langkah-langkah
 
**1.** Upload notebook ke Google Colab
 
**2.** Upload 3 file dataset ke `dataset`:
- `case_1_labeled_data.xlsx`
- `case_1_text_to_predict.xlsx`
- `case_1_template_sheet.xlsx`
**3.** Pastikan runtime menggunakan GPU:
`Runtime → Change runtime type → GPU`
 
**4.** Jalankan semua cell secara berurutan:
`Runtime → Run All`
 
**5.** Ganti nama file output di cell terakhir:
```python
NAMA_TIM = 'kata dospem kalo ikut auto A' 
```
 
**6.** File prediksi otomatis ter-download sebagai `kata dospem kalo ikut auto A.xlsx`
 
 
---
 
## Catatan
 
- Seed sudah di-fix di `SEED = 42` untuk reproducibility
- Early stopping dengan `patience = 3` aktif di setiap fold
- Class weights dihitung otomatis dari distribusi label training
- Loss function: CrossEntropyLoss dengan label smoothing 0.1
