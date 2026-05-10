# Instruksi Agent - Assessment Linear Regression

File ini adalah instruksi statis untuk membuat notebook assessment dan kunci jawaban Linear Regression. Jangan gunakan file ini untuk mencatat progress harian, pembagian tugas, atau status dataset. Semua tracking dinamis wajib ditulis di `DATASET_TRACKER.md`.

## Tujuan

Buat notebook assessment akhir mini bootcamp Machine Learning untuk setiap dataset pada `linear_regression_dataset_spreadsheet.xlsx` atau `linear_regression_dataset_spreadsheet.csv`.

Untuk setiap dataset, agent wajib membuat dua notebook dengan layout cell yang identik:

- notebook assessment untuk peserta,
- notebook kunci jawaban.

Perbedaan hanya boleh ada pada isi code cell, output cell, dan jawaban analisis.

## Input Spreadsheet

Spreadsheet wajib memiliki kolom berikut:

- `No`
- `Dataset`
- `Source URL`
- `Recommended Target`
- `Deskripsi Singkat`

Gunakan `No`, `Dataset`, dan `Recommended Target` sebagai dasar nama file, judul notebook, target modeling, dan kesimpulan.

## Struktur Folder

Setiap dataset wajib memiliki satu folder sendiri.

Format folder:

```text
<no dua digit>_<slug_dataset>
```

Format file:

```text
<no dua digit>_<slug_dataset>_linear_regression.ipynb
Kunci_Jawaban_<no dua digit>_<slug_dataset>_linear_regression.ipynb
```

Contoh:

```text
01_concrete_compressive_strength/
├── 01_concrete_compressive_strength_linear_regression.ipynb
└── Kunci_Jawaban_01_concrete_compressive_strength_linear_regression.ipynb
```

Jangan menaruh notebook dataset langsung di root project. Root project hanya untuk file pengarah seperti `AGENTS.md`, `DATASET_TRACKER.md`, spreadsheet, dan dokumen spesifikasi.

## Urutan Notebook

Setiap notebook wajib memakai urutan section berikut:

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

Setiap code cell wajib didahului markdown heading level 3 (`###`) dengan deskripsi singkat langkah di bawahnya.

## Aturan Umum Cell

- Jangan gunakan kata `TODO`.
- Jangan gunakan `print()` jika output bisa ditampilkan dengan ekspresi terakhir atau `display()`.
- Satu code cell sebaiknya menghasilkan satu output.
- Semua code cell wajib bebas trailing whitespace.
- Source code cell tidak boleh berakhir dengan baris kosong.
- Code cell boleh multi-line jika memang dibutuhkan, tetapi jangan menambah newline kosong di akhir cell.
- Bahasa markdown harus beginner-friendly untuk mahasiswa tingkat awal.
- Jangan membuat analisis terlalu rumit atau terlalu panjang.

## Notebook Assessment

Notebook assessment adalah template pengerjaan peserta.

Aturan wajib:

- Code cell utama harus kosong agar peserta mengisi sendiri.
- Code cell kosong tidak boleh berisi komentar.
- Notebook tidak boleh memiliki output.
- Notebook tidak boleh memiliki execution count.
- Bagian kesimpulan berbentuk paragraf biasa dengan bracket isian, bukan blockquote.

Code cell berikut boleh terisi default karena hanya boilerplate:

```python
warnings.filterwarnings("ignore")
pd.set_option("display.float_format", lambda x: f"{x:.3f}")
sns.set_theme(style="whitegrid")
```

Untuk dataset UCI yang memakai `fetch_ucirepo`, cell pengambilan dataset wajib terisi default.

Contoh:

```python
concrete = fetch_ucirepo(id=165)
```

Untuk dataset Kaggle, cell upload atau load file utama boleh terisi default jika hanya berisi boilerplate akses file.

## Pertanyaan Assessment

Markdown setelah output cell pada notebook kunci jawaban harus diubah menjadi pertanyaan pada notebook assessment.

Format wajib:

- Gunakan blockquote Markdown.
- Pisahkan setiap pertanyaan menjadi blockquote sendiri.
- Tambahkan `...` setelah setiap pertanyaan sebagai ruang jawaban.

Contoh:

```markdown
> Berdasarkan output `info()`, apa tipe data setiap kolom?

...

> Apakah jumlah non-null menunjukkan adanya missing value?

...
```

Format kesimpulan assessment:

```markdown
## 11 - Kesimpulan

Lengkapi kesimpulan berikut berdasarkan seluruh output notebook:

Dataset [nama dataset] digunakan untuk memprediksi [target] berdasarkan [fitur utama]. Data [tidak memiliki/memiliki] missing value dan memiliki [jumlah] baris duplikat penuh.
```

## Notebook Kunci Jawaban

Notebook kunci jawaban adalah clean solution.

Aturan wajib:

- Code cell berisi kode lengkap.
- Output cell boleh ada dan harus relevan.
- Pertanyaan dari notebook assessment tetap dipakai.
- Setiap `...` pada assessment diganti menjadi jawaban kunci.
- Jawaban kunci harus singkat, jelas, dan sesuai output.
- Kesimpulan akhir ditulis sebagai paragraf lengkap tanpa bracket kosong.

Contoh:

```markdown
> Berdasarkan output `info()`, apa tipe data setiap kolom?

Jawaban: Tipe data kolom terdiri dari data numerik, yaitu `float64` dan `int64`.

> Apakah jumlah non-null menunjukkan adanya missing value?

Jawaban: Tidak, jumlah non-null sama dengan jumlah baris dataset sehingga tidak terlihat missing value dari output `info()`.
```

## Isi Analisis Minimal

Gunakan alur analisis sederhana berikut jika relevan dengan dataset:

- ukuran dataset dengan `df.shape`,
- lima baris pertama dengan `df.head()`,
- informasi dataset dengan `df.info()`,
- missing value dengan `df.isna().sum()`,
- duplikat dengan `df.duplicated().sum()`,
- statistik deskriptif dengan `df.describe()`,
- histogram target,
- korelasi fitur dengan target,
- satu atau dua visualisasi hubungan fitur penting dengan target,
- pemisahan feature dan target,
- train-test split,
- scaling dengan `StandardScaler`,
- model `LinearRegression`,
- evaluasi MAE, RMSE, dan R2,
- visualisasi aktual vs prediksi.

## Aturan Visualisasi

Pilih plot sesuai karakter data. Jangan memakai jenis plot yang sama untuk semua dataset.

- Untuk fitur numerik kontinu, gunakan scatter plot atau regression plot jika hubungan titik data memang mudah dibaca.
- Untuk fitur numerik yang nilainya sedikit atau berbentuk kelompok, gunakan boxplot, bar plot rata-rata, atau line plot rata-rata.
- Untuk fitur kategori, gunakan bar plot rata-rata atau boxplot setelah kategori jelas.
- Untuk fitur waktu atau umur yang berurutan, gunakan line plot rata-rata jika scatter terlalu menumpuk.
- Jangan memaksakan garis regresi pada fitur yang hanya memiliki beberapa nilai unik.
- Judul, label sumbu, dan pertanyaan analisis harus mengikuti plot yang benar-benar dipakai.

## Penanganan Dataset

- Untuk UCI yang tersedia lewat `ucimlrepo`, gunakan `fetch_ucirepo`.
- Untuk Kaggle, gunakan instruksi load dataset yang jelas dan beginner-friendly.
- Jika Kaggle memakai file lokal, sebutkan nama file utama yang harus diupload atau diletakkan di folder kerja.
- Jika dataset memiliki beberapa target, pilih satu target saja.
- Jika ada kolom tanggal, drop atau parse secara sederhana.
- Jika ada kolom kategori, gunakan `pd.get_dummies()`.
- Jika ada missing value, gunakan strategi sederhana seperti drop baris, imputasi median, atau imputasi mode.
- Jika ada nilai sentinel seperti `-200`, ubah menjadi missing value sebelum cleaning.

## Validasi Wajib

Sebelum commit, agent wajib memeriksa:

- setiap dataset memiliki satu folder,
- setiap folder dataset berisi notebook assessment dan kunci jawaban,
- layout cell assessment dan kunci jawaban identik,
- notebook assessment tidak memiliki output,
- notebook assessment tidak memiliki execution count,
- code cell assessment hanya terisi pada boilerplate yang diizinkan,
- semua code cell bebas trailing whitespace dan baris kosong di akhir cell,
- notebook assessment tidak mengandung `TODO`,
- notebook kunci jawaban memiliki kode lengkap,
- semua notebook valid dibaca oleh `nbformat`.

## Aturan Git

Setiap selesai mengedit file, agent wajib membuat commit.

Aturan commit:

- Gunakan conventional commit.
- Commit hanya file yang diedit untuk tugas saat itu.
- Commit harus spesifik terhadap perubahan yang dilakukan.
- Jangan gabungkan perubahan yang tidak berhubungan dalam satu commit.
- Jangan commit sebelum validasi relevan selesai.
- Jangan revert perubahan user kecuali user meminta secara eksplisit.

Contoh:

```text
docs: clarify notebook generation rules
chore: reorganize dataset folders
feat: add assessment notebook for energy efficiency
fix: clean empty outputs in assessment notebook
```

## Tracker

Gunakan `DATASET_TRACKER.md` untuk mencatat:

- penanggung jawab dataset,
- status folder dataset,
- status notebook assessment,
- status notebook kunci jawaban,
- catatan pengerjaan,
- blocker.
