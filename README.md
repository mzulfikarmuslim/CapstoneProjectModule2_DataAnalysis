# CapstoneProjectModule2_DataAnalysis
Folder ini berisi Capstone Project Purwadhika BSD membuat Data Analysis

## CPM2_mzm.ipynb
### INTRODUCTION
Departemen Kepolisian Boston menyediakan sistem pelaporan insiden kejahatan untuk mendokumentasikan rincian awal seputar insiden yang ditanggapi oleh petugas BPD. 

Kumpulan data berisi catatan dari sistem laporan insiden kejahatan terbaru yang difokuskan untuk menangkap jenis kejahatan serta kapan dan di mana insiden itu terjadi.

### BUSINESS UNDERSTANDING
Sebagai seorang data analyst, kita akan mencoba menjawab beberapa pertanyaan berikut:

- Jenis kejahatan apa yang paling umum?
- Apakah jumlah kejahatan berubah dari hari ke hari? Bulan? Tahun?
- Di mana berbagai jenis kejahatan paling mungkin terjadi?

### DATA PREPARATION AND CLEANING

1. Menghapus Data Duplikat
2. Memperbaiki Kesalahan Struktur
- Menyesuaikan format penulisan INCIDENT_NUMBER,
- Menyesuaikan OFFENSE_DESCRIPTION dengan OFFENSE_CODE,
- Menyesuaikan penulisan OFFENSE_CODE_GROUP yang huruf besar semua menjadi huruf besar di awal kata,
- Mengubah tipe data OCCURED_ON_DATE menjadi datetime, etc
3. Menangani Missing Values 
- SHOOTING, UCR_PART, DISTRICT, REPORTING_AREA, STREET, dan Location
4. Menambah Kolom Baru
- TIME : Morning (4:00-11:59), Afternoon (12:00-19:59), Night (20:00-3:59)
- WEEK : Weekend (‘Saturday’, ’Sunday’), Weekday (‘Monday’ s.d. ‘Friday’)
5. Memilih Kolom Yang Relevan
- Informasi kriminalitas : INCIDENT_NUMBER, UCR_PART, OFFENSE_CODE_GROUP, OFFENSE_DESCRIPTION, SHOOTING
- Waktu kejadian : OCCURRED_ON_DATE, YEAR, MONTH, WEEK, DAY_OF_WEEK, TIME, HOUR
- Tempat kejadian : DISTRICT, REPORTING_AREA, STREET, Lat, Long
6. Menghapus Kembali Data Duplikat


