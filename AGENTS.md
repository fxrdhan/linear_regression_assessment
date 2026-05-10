# Instruksi Agent - Generate Notebook Assessment Linear Regression

Agent berikutnya harus menjalankan proses pembuatan notebook secara looping dari daftar dataset pada `linear_regression_dataset_spreadsheet.xlsx` atau `linear_regression_dataset_spreadsheet.csv`.

Untuk setiap baris dataset, buat dua notebook:

- Notebook assessment / soal untuk peserta.
- Notebook kunci jawaban / clean solution.

Kedua notebook harus memiliki layout yang sama persis. Perbedaannya hanya pada isi code cell, output, dan jawaban analisis.

Spreadsheet berisi kolom:

- `No`
- `Dataset`
- `Source URL`
- `Recommended Target`
- `Deskripsi Singkat`

## Nama File Output

Untuk setiap dataset, buat:

- Folder dataset: gunakan format nomor dataset + slug nama dataset.
- Assessment: gunakan format nomor dataset + slug nama dataset + `_linear_regression.ipynb`.
- Kunci jawaban: gunakan prefix `Kunci_Jawaban_` + nama file assessment.

Contoh:

- Folder: `01_concrete_compressive_strength`
- Assessment: `01_concrete_compressive_strength_linear_regression.ipynb`
- Kunci jawaban: `Kunci_Jawaban_01_concrete_compressive_strength_linear_regression.ipynb`

Struktur setiap dataset wajib seperti ini:

```text
01_concrete_compressive_strength/
├── 01_concrete_compressive_strength_linear_regression.ipynb
└── Kunci_Jawaban_01_concrete_compressive_strength_linear_regression.ipynb
```

Jangan menaruh notebook dataset langsung di root folder project. Root folder hanya untuk file pengarah seperti `AGENTS.md`, spreadsheet dataset, dan dokumen spesifikasi.

## Alur Notebook Wajib

Setiap notebook harus mengikuti urutan besar berikut:

1. Setup
2. Load Dataset
3. Data Understanding
4. Data Cleaning
5. Exploratory Data Analysis
6. Feature dan Target
7. Train-Test Split
8. Feature Scaling
9. Linear Regression Model
10. Prediksi dan Evaluasi
11. Kesimpulan

Setiap code cell harus didahului markdown heading level 3 (`###`) yang menjelaskan langkah di bawahnya.

## Format Notebook Assessment

Notebook assessment adalah template pengerjaan peserta.

Aturan:

- Layout harus sama persis dengan notebook kunci jawaban.
- Code cell utama dikosongkan agar peserta mengisi sendiri.
- Jangan isi code cell kosong dengan komentar.
- Jangan gunakan kata `TODO`.
- Jangan sertakan output apa pun.
- Jangan sertakan execution count.
- Code cell tidak boleh memiliki trailing whitespace atau baris kosong di akhir cell.
- Bagian teknis berikut boleh sudah terisi default:
  - `warnings.filterwarnings("ignore")`
  - `pd.set_option("display.float_format", lambda x: f"{x:.3f}")`
  - `sns.set_theme(style="whitegrid")`
- Untuk dataset UCI yang menggunakan `fetch_ucirepo`, code cell pengambilan dataset wajib sudah terisi default, misalnya `concrete = fetch_ucirepo(id=165)`.
- Untuk dataset Kaggle, code cell upload atau load path file utama boleh sudah terisi default jika hanya berupa boilerplate akses file.
- Markdown setelah output cell pada kunci jawaban harus diubah menjadi pertanyaan untuk peserta.
- Pertanyaan harus memakai blockquote Markdown.
- Jika ada lebih dari satu pertanyaan, pisahkan setiap pertanyaan menjadi blockquote sendiri.
- Setelah setiap pertanyaan, beri ruang jawaban berupa `...`.
- Bagian kesimpulan jangan memakai blockquote. Gunakan paragraf biasa dengan bracket isian.

Contoh format pertanyaan:

```markdown
> Berdasarkan output `info()`, apa tipe data setiap kolom?

...

> Apakah jumlah non-null menunjukkan adanya missing value?

...
```

Contoh format kesimpulan assessment:

```markdown
## 11 - Kesimpulan

Lengkapi kesimpulan berikut berdasarkan seluruh output notebook:

Dataset [nama dataset] digunakan untuk memprediksi [target] berdasarkan [fitur utama]. Data [tidak memiliki/memiliki] missing value dan memiliki [jumlah] baris duplikat penuh.
```

## Format Notebook Kunci Jawaban

Notebook kunci jawaban adalah versi clean solution.

Aturan:

- Layout harus identik dengan notebook assessment.
- Code cell berisi kode lengkap.
- Output boleh ada dan harus relevan.
- Usahakan satu code cell hanya menghasilkan satu output.
- Code cell tidak boleh memiliki trailing whitespace atau baris kosong di akhir cell.
- Hindari `print()` yang tidak perlu.
- Gunakan ekspresi terakhir atau `display()` jika memang perlu menampilkan objek.
- Markdown pertanyaan dari notebook assessment tetap dipakai, tetapi setiap `...` diganti dengan jawaban kunci.
- Jawaban harus singkat, jelas, dan beginner-friendly.
- Kesimpulan akhir ditulis sebagai paragraf lengkap tanpa bracket kosong.

Contoh format jawaban:

```markdown
> Berdasarkan output `info()`, apa tipe data setiap kolom?

Jawaban: Tipe data kolom terdiri dari data numerik, yaitu `float64` dan `int64`.

> Apakah jumlah non-null menunjukkan adanya missing value?

Jawaban: Tidak, jumlah non-null sama dengan jumlah baris dataset sehingga tidak terlihat missing value dari output `info()`.
```

## Kompleksitas Analisis

Notebook harus cukup lengkap tetapi tetap beginner-friendly.

Gunakan pola sederhana:

- `df.shape`
- `df.head()`
- `df.info()`
- `df.isna().sum()`
- `df.duplicated().sum()`
- `df.describe()`
- histogram target
- korelasi fitur dengan target
- satu atau dua visualisasi hubungan fitur penting dengan target
- split train-test
- scaling dengan `StandardScaler`
- model `LinearRegression`
- evaluasi menggunakan MAE, RMSE, dan R2
- visualisasi aktual vs prediksi

Jangan membuat analisis terlalu rumit seperti modul tingkat lanjut. Assessment ini untuk mahasiswa tingkat awal.

## Penanganan Dataset

Gunakan pendekatan yang sesuai dengan sumber:

- Untuk UCI yang tersedia lewat `ucimlrepo`, gunakan `fetch_ucirepo`.
- Pada notebook assessment untuk UCI, cell `fetch_ucirepo(id=...)` jangan dikosongkan karena ID dataset adalah bagian boilerplate, bukan jawaban analisis peserta.
- Untuk Kaggle, berikan cell load dataset yang jelas dan beginner-friendly.
- Jika Kaggle membutuhkan file lokal, buat instruksi markdown agar peserta upload atau menaruh CSV pada path yang jelas.
- Jika ada kolom tanggal, drop atau parse secara sederhana.
- Jika ada kolom kategori, gunakan one-hot encoding dengan `pd.get_dummies()`.
- Jika ada missing value, gunakan strategi sederhana seperti drop baris atau imputasi median/mode sesuai kebutuhan.
- Jika ada nilai sentinel seperti `-200`, ubah menjadi missing value terlebih dahulu.

## Validasi Wajib Setelah Generate

Setelah membuat semua notebook, agent wajib mengecek:

- Setiap dataset menghasilkan satu folder dataset.
- Setiap folder dataset berisi dua file notebook: assessment dan kunci jawaban.
- Notebook assessment tidak memiliki output.
- Notebook assessment tidak memiliki execution count.
- Notebook assessment tidak memiliki code cell utama yang terisi, kecuali setting teknis default yang memang diizinkan.
- Semua code cell bebas trailing whitespace dan tidak memiliki baris kosong di akhir cell.
- Notebook assessment tidak mengandung `TODO`.
- Notebook kunci jawaban memiliki kode lengkap.
- Notebook kunci jawaban memiliki layout cell yang sama dengan assessment.
- Semua notebook valid dibaca oleh `nbformat`.

## Aturan Git

Setiap selesai melakukan pengeditan file, agent wajib membuat commit git.

Aturan commit:

- Gunakan conventional commit.
- Commit harus spesifik terhadap perubahan yang baru dilakukan.
- Jangan menggabungkan perubahan yang tidak berhubungan dalam satu commit.
- Jangan melakukan commit jika validasi perubahan yang relevan belum dilakukan.
- Jika worktree memiliki perubahan lama dari user, jangan revert perubahan tersebut. Commit hanya file yang memang diedit untuk tugas saat itu.

Contoh format commit:

```text
docs: update dataset generation instructions
chore: reorganize dataset folders
feat: add assessment notebook for energy efficiency
fix: clean empty outputs in assessment notebook
```

## Tracker Project

Jangan menyimpan status progress, pembagian penanggung jawab, atau catatan pengerjaan dinamis di `AGENTS.md`.

Gunakan `DATASET_TRACKER.md` untuk mencatat:

- penanggung jawab setiap dataset,
- status folder dataset,
- status notebook assessment,
- status notebook kunci jawaban,
- catatan pengerjaan atau blocker.
