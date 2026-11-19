# PROJECT AKHIR DATA WAREHOUSE KELOMPOK 1

# Data Warehouse & OLAP Crime Analysis in India (2020–2024)

## Team Members

| Role | Name | NIM |
|---|---|---|
| Ketua | Yanaka Sofia Pardede | 24031554065 |
| Anggota | Annisa Ramadhani | 24031554206 |
| Anggota | Ayu Wulan Anggraeni Putri | 24031554177 |

## Project Overview

Proyek ini bertujuan untuk membangun **Data Warehouse** dan melakukan analisis **Online Analytical Processing (OLAP)** terhadap data kriminalitas di India periode 2020–2024. Analisis dilakukan untuk memahami pola kriminalitas berdasarkan dimensi waktu, lokasi, karakteristik korban, kategori kejahatan, serta penggunaan senjata.

Dataset diolah melalui proses **ETL (Extract, Transform, Load)**, kemudian dirancang menggunakan pendekatan **Star Schema** untuk mendukung analisis multidimensi. Hasil pengolahan data selanjutnya dimanfaatkan dalam analisis OLAP dan visualisasi dashboard.

## Dataset Information

- **Dataset:** Indian Crimes Dataset
- **Source:** [Kaggle – Indian Crimes Dataset](https://www.kaggle.com/datasets/sudhanvahg/indian-crimes-dataset)
- **Total Records:** 40,160
- **Total Attributes:** 14

### Main Attributes

- Report Number
- Date Reported
- Date of Occurrence
- City
- Crime Description
- Crime Domain
- Victim Age
- Victim Gender
- Weapon Used
- Police Deployed
- Case Closed
- Date Case Closed

## ETL Process

### 1. Extract

Dataset dibaca dari file CSV menggunakan Python dan library Pandas sebagai tahap awal pengolahan data.

### 2. Transform

Tahapan transformasi data meliputi:

- Konversi atribut tanggal ke format datetime.
- Penanganan missing values.
- Pembuatan atribut waktu, seperti Year, Quarter, Month, dan Day.
- Perhitungan Resolution Days.
- Pembentukan tabel dimensi.
- Pembentukan tabel fakta.

### 3. Load

Data yang telah melalui proses transformasi dimuat ke lingkungan Data Warehouse menggunakan PostgreSQL. Data selanjutnya digunakan dalam lingkungan OLAP dengan Atoti untuk mendukung analisis multidimensi dan visualisasi dashboard.

## Data Warehouse Design

### Star Schema

Data Warehouse dirancang menggunakan pendekatan **Star Schema**, yang terdiri dari satu tabel fakta dan lima tabel dimensi.

### Fact Table

**Fact Crime**

Measures:
- `crime_count`
- `police_deployed`
- `resolution_days`

### Dimension Tables

| Dimension | Attributes |
|---|---|
| Dim Date | year, quarter, month, month_name, day, holiday_type |
| Dim City | city |
| Dim Crime | crime_description, crime_domain |
| Dim Victim | victim_gender, age_group |
| Dim Weapon | weapon_used |

## OLAP Analysis

Analisis OLAP dilakukan untuk melihat pola kriminalitas berdasarkan berbagai dimensi. Analisis yang dilakukan meliputi:

1. Total Crime per Year
2. Top 10 City by Total Crime
3. Crime Domain vs Total Crime
4. Victim Gender vs Total Crime
5. Age Group vs Total Crime
6. Weapon Used vs Total Crime
7. Crime Domain vs Average Resolution Days
8. City vs Average Resolution Days
9. Age Categories vs Total Crime
10. Holiday Type vs Crime Domain
11. Holiday Type vs Total Crime

## Dashboard Visualization

Dashboard dibuat menggunakan **Looker Studio** untuk menyajikan hasil analisis dalam bentuk visualisasi yang informatif dan mudah dipahami.

| No. | Visualization |
|---|---|
| 1 | Total Crime per Year |
| 2 | Victim Gender vs Total Crime |
| 3 | Top 10 City by Total Crime |
| 4 | Crime Domain vs Total Crime |
| 5 | Age Group vs Total Crime |
| 6 | Weapon Used vs Total Crime |
| 7 | Crime Domain vs Average Resolution Days |
| 8 | City vs Average Resolution Days |
| 9 | Age Categories vs Total Crime |
| 10 | Holiday Type vs Crime Domain |
| 11 | Holiday Type vs Total Crime |

## Key Findings

Berdasarkan hasil analisis yang telah dilakukan, diperoleh beberapa temuan utama:

- Jumlah kasus kriminal relatif stabil selama periode 2020–2023.
- Delhi menjadi kota dengan jumlah kasus kriminal tertinggi.
- Other Crime merupakan kategori kejahatan yang paling dominan.
- Korban perempuan tercatat lebih banyak dibandingkan korban laki-laki.
- Kelompok usia lansia memiliki jumlah korban tertinggi.
- Knife menjadi jenis senjata yang paling sering digunakan.
- Violent Crime membutuhkan rata-rata waktu penyelesaian paling lama.
- Republic Day memiliki proporsi kriminalitas tertinggi dibandingkan hari besar lainnya.
