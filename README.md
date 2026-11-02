# Face Anti-Spoofing pada Subset CelebA-Spoof

Kode eksperimen untuk laporan UTS *Foundation of Machine Learning and Optimization* (Magister Kecerdasan Artifisial, UDINUS).
Penulis: Rahmanda Afridiansyah (P36.2026.00018). Dosen: Prof. Dr. Guruh Fajar Shidik.

Laporan membandingkan dua pendekatan berbasis MobileNetV3-Small pada deteksi serangan presentasi wajah:
1. **CNN pretrained** (bobot ImageNet, tanpa training ulang, 576-d) dengan fusi fitur tekstur (LBP) dan frekuensi (FFT radial), diklasifikasikan Logistic Regression / Random Forest.
2. **Fine-tuning end-to-end** MobileNetV3-Small.

## Data
Subset CelebA-Spoof (volume pertama arsip, sekitar 4 GB): 8.511 citra dari 79 subjek setelah audit.
Dataset **tidak disertakan** di repo ini karena lisensinya milik pemilik dataset; unduh dari
sumber resmi CelebA-Spoof (Zhang dkk., ECCV 2020) dan sesuaikan jalur di notebook
(`WORK` dan jalur arsip menunjuk ke Google Drive penulis).

## Notebook (jalankan berurutan di Google Colab, GPU)
| Notebook | Isi |
|---|---|
| `notebooks/01_FeatureExtraction.ipynb` | ekstrak arsip, indeks dan audit berkas, pembagian per subjek, fitur CNN + FFT + LBP |
| `notebooks/02_Baseline_Models.ipynb` | baseline, 10 pembagian per subjek, tuning, ablasi fitur, uji Wilcoxon |
| `notebooks/03_FineTuning.ipynb` | fine-tuning, perbandingan dengan baseline, AUC metadata berkas, analisis kesalahan, kontrol ukuran |

Evaluasi memakai pembagian **per subjek** (70/15/15), ambang dari EER validasi, metrik APCER, BPCER, HTER, dan AUC.

## Ringkasan hasil (rata-rata 10 pembagian)
| Model | HTER | AUC |
|---|---|---|
| CNN pretrained + Logistic Regression | 0,101 | 0,959 |
| CNN pretrained + fusi LBP/FFT | 0,082 | 0,973 |
| Fine-tuning MobileNetV3-Small | 0,024 | 0,998 |

Catatan penting: kelas live dan spoof pada subset ini dapat dibedakan dengan AUC 0,934 hanya dari metadata berkas
(lebar, tinggi, ukuran berkas), sehingga hasil fine-tuning tidak sepenuhnya mencerminkan deteksi artefak serangan.
Setelah ukuran dan ketajaman disamakan, HTER fine-tuning 0,041 (3 pembagian). Tidak ada uji lintas dataset.
Rincian dan keterbatasan ada di laporan.

## Lingkungan
Lihat `requirements.txt` (versi tercetak di notebook). Dijalankan di Google Colab.

## Penggunaan AI
Lihat `AI_USAGE.md`.
