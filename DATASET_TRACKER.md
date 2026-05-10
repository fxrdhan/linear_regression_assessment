# Dataset Tracker - Linear Regression Assessment

File ini dipakai untuk tracking progress dan pembagian penanggung jawab. Berbeda dari `AGENTS.md`, file ini boleh berubah selama pengerjaan.

## Aturan Update

- Isi kolom `Penanggung Jawab` dengan nama agent/orang yang mengerjakan dataset.
- Gunakan status singkat seperti `Belum`, `Proses`, `Review`, atau `Selesai`.
- Catat blocker penting di kolom `Catatan`.
- Jangan mengubah aturan format notebook di file ini; aturan tetap berada di `AGENTS.md`.

## Tracker

| No | Dataset | Target | Folder | Penanggung Jawab | Folder | Assessment | Kunci Jawaban | Catatan |
|---:|---|---|---|---|---|---|---|---|
| 1 | Concrete Compressive Strength | `Concrete compressive strength` | `01_concrete_compressive_strength` |  | Selesai | Selesai | Selesai | Contoh format utama sudah tersedia. |
| 2 | Energy Efficiency | `Y1` / Heating Load | `02_energy_efficiency` | Codex | Selesai | Selesai | Selesai | Target dipilih satu: Heating Load (`Y1`). |
| 3 | Real Estate Valuation | `Y house price of unit area` | `03_real_estate_valuation` | Codex | Selesai | Selesai | Selesai | Kolom `X1 transaction date` dihapus sebelum modeling. |
| 4 | Auto MPG | `mpg` | `04_auto_mpg` | Codex | Selesai | Selesai | Selesai | Missing value pada `horsepower` dihapus sebelum modeling. |
| 5 | Combined Cycle Power Plant | `PE` | `05_combined_cycle_power_plant` | Codex | Selesai | Selesai | Selesai | Duplikat penuh dihapus; fitur numerik semua. |
| 6 | Bike Sharing Dataset | `cnt` | `06_bike_sharing_dataset` | Codex | Selesai | Selesai | Selesai | Kolom `dteday` dihapus; duplikat setelah drop tanggal ikut dihapus. |
| 7 | Wine Quality | `quality` | `07_wine_quality` | Codex | Selesai | Selesai | Selesai | Target skor diskret; visual EDA memakai count plot dan boxplot. |
| 8 | Student Performance | `G3` | `08_student_performance` | Codex | Selesai | Selesai | Selesai | Kolom kategori di-encode dengan `pd.get_dummies()`. |
| 9 | Air Quality | `CO(GT)` | `09_air_quality` | Codex | Selesai | Selesai | Selesai | Nilai sentinel `-200` diubah menjadi missing; target dipilih `CO(GT)`. |
| 10 | Medical Cost Personal Dataset / Insurance | `charges` | `10_medical_cost_personal_dataset_insurance` | Codex | Selesai | Selesai | Selesai | Kaggle; file utama `insurance.csv`, kategori di-encode dengan `pd.get_dummies()`. |
| 11 | Fish Market | `Weight` | `11_fish_market` | Codex | Selesai | Selesai | Selesai | Kaggle; sumber diganti ke mirror yang bisa diakses, file utama `Fish.csv`, `Species` di-encode dengan `pd.get_dummies()`. |
| 12 | Seoul Bike Sharing Demand | `Rented Bike Count` | `12_seoul_bike_sharing_demand` | Codex | Selesai | Selesai | Selesai | Target diambil dari kolom fitur UCI; `Date` dihapus, kategori di-encode, visual memakai line plot per jam dan boxplot musim. |
| 13 | House Rent Prediction Dataset | `Rent` | `13_house_rent_prediction_dataset` | Codex | Selesai | Selesai | Selesai | Kaggle; file utama `House_Rent_Dataset.csv`, kolom teks detail dihapus, kategori ringkas di-encode. |
| 14 | Airfoil Self-Noise | `scaled-sound-pressure` | `14_airfoil_self_noise` |  | Belum | Belum | Belum | Cek nama kolom jika data mentah tidak punya header. |
| 15 | Yacht Hydrodynamics | `residuary resistance` | `15_yacht_hydrodynamics` |  | Belum | Belum | Belum | Dataset kecil, cocok untuk struktur sederhana. |
| 16 | Appliances Energy Prediction | `Appliances` | `16_appliances_energy_prediction` |  | Belum | Belum | Belum | Dataset lebih besar; drop/parse date secara sederhana. |
| 17 | Concrete Slump Test | `Compressive Strength or SLUMP or FLOW` | `17_concrete_slump_test` |  | Belum | Belum | Belum | Pilih satu target saja. |
| 18 | Computer Hardware | `PRP` | `18_computer_hardware` |  | Belum | Belum | Belum | Drop nama model atau encode kategori jika dipakai. |
| 19 | QSAR Fish Toxicity | `LC50` | `19_qsar_fish_toxicity` |  | Belum | Belum | Belum | Fitur numerik ringkas. |
| 20 | Abalone | `Rings` | `20_abalone` |  | Belum | Belum | Belum | Encode kolom `Sex`. |
