# AI_USAGE.md — Project UTS S2AI-101 (Face Anti-Spoofing)

Mahasiswa: Rahmanda Afridiansyah (P36.2026.00018)

## Alat
Claude (Anthropic), model Claude Sonnet 5.5 (sesuai konfigurasi sesi kerja).

## Tujuan penggunaan
- Menganalisis kelayakan waktu dan memilih opsi pengumpulan (Report).
- Merancang eksperimen anti-spoofing yang ringan.
- Menulis kode Python: ekstraksi fitur, pemodelan, evaluasi per subjek, tuning, ablasi, fine-tuning, analisis kesalahan, dan kontrol ukuran.
- Debugging error di Google Colab dan cara mengambil dataset tanpa mengunduh ke laptop.
- Mencari referensi, memeriksa metadata sitasi, dan menyusun draf report (.docx).
- Merapikan notebook untuk repositori (menghapus metadata akun, menambah catatan alur) tanpa mengubah hasil.

## Prompt penting
1. Melampirkan brief Project UTS dan meminta analisis apakah waktunya terkejar.
2. Topik Face Anti-Spoofing / Liveness Detection / Deepfake dari catatan mahasiswa.
3. Cara mengambil CelebA-Spoof ke Colab tanpa mengunduh ke laptop.
4. Kode ekstraksi fitur (MobileNetV3-Small, FFT, LBP), baseline, model, tuning, ablasi, dan fine-tuning.
5. Penyusunan draf report dan verifikasi referensi.
6. Memeriksa paper pembanding IEEE Access dan menulis paragraf perbandingan (Bagian 4.4, referensi [7]).

## Keluaran AI yang dipakai
Kode pada notebook 01_FeatureExtraction, 02_Baseline_Models, dan 03_FineTuning, rancangan eksperimen
(metrik APCER/BPCER/HTER, pembagian per subjek, fusi fitur CNN dengan LBP/FFT, fine-tuning end-to-end,
kontrol ukuran citra), dan draf report.

## Kesalahan AI yang ditemukan dan dikoreksi selama proses
- Pola pencarian berkas menangkap file `_BB.txt` sehingga jumlah citra awal terhitung 17.053;
  jumlah citra sebenarnya 8.512. Dikoreksi sebelum analisis dan dicatat di data audit report.
  Di notebook 01 kode pencariannya sengaja tidak diubah supaya sama dengan yang menghasilkan angka report;
  hanya ditambah catatan.
- Perkiraan awal bahwa kuota Drive tidak cukup ternyata keliru (penyimpanan mahasiswa 5 TB);
  hambatan sebenarnya adalah batas unduh Google untuk file publik.
- Istilah di judul report sempat diganti beberapa kali (dari "CNN beku" menjadi "CNN pretrained") atas
  permintaan mahasiswa karena kurang akademis.

## Kontribusi dan tindakan mahasiswa
- Memilih topik dari catatan riset sendiri.
- Menyalin bagian arsip dataset ke Google Drive dan menjalankan seluruh notebook di Google Colab.
- Melaporkan keluaran notebook (angka, tabel, gambar) yang dipakai di report.
- Mengambil metadata sitasi referensi [2], [4], [5], [6], [7] dari IEEE Xplore.

## Validasi
- Seluruh angka di report berasal dari eksekusi notebook oleh mahasiswa di Google Colab.
- Referensi [1] diperiksa di halaman Springer, [3] di halaman CVF Open Access, dan
  [2], [4], [5], [6], [7] melalui halaman IEEE Xplore ("Cite This").
- Klaim ablasi pada paper [7] dicocokkan dengan Tabel 8 paper tersebut (ROSE-Youtu).

## Keputusan ilmiah
Pemilihan topik dilakukan mahasiswa. Rancangan eksperimen disarankan oleh AI dan disetujui mahasiswa.
