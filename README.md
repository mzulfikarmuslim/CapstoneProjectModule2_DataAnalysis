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

### KESIMPULAN

Dari analisis yang telah dilakukan, kita bisa membuat kesimpulan dan menjawab pertanyaan seputar insiden kriminal yang terjadi di Boston untuk periode Juni 2015 - September 2018 sebagai berikut :
- `Jenis kejahatan apa yang paling umum?`
    * Motor Vehicle Accident Response dengan jumlah sebanyak 36.574 kasus merupakan jumlah kasus tertinggi dari data insiden kejahatan yang disediakan oleh Departemen Kepolisian Boston (BPD). Hal ini menunjukkan insiden kecelakaan lalu lintas merupakan jenis insiden yang paling sering terjadi.
    * Insiden kejahatan dengan kategori Part One (violent & property crime) yang paling sering terjadi adalah Larceny, Larceny From Motor Vehicle, dan Aggravated Assault. Sedangkan yang paling jarang terjadi adalah Homicide. 
    * Insiden kejahatan dengan kategori Part Two yang paling sering terjadi adalah Drug Violation, Simple Assault, dan Vandalism dengan jumlah kejahatan yang relatif seragam di kisaran 15000 - 16500 kasus.
    * Insiden lainnya (Part Three) yang paling sering terjadi adalah Motor Vehicle Accident Response, Medical Assistance, dan Investigate Person yang lebih menunjukkan aksi/respon yang dilakukan langsung oleh kepolisian. Sehingga kita dapat mengethaui bahwa upaya yang paling sering dilakukan oleh kepolisian Boston banyak berupa penanganan kecelakaan lalu lintas, pemberian bantuan medis, dan penyelidikan orang.
    * 75% kasus Homicide atau pembunuhan yang terjadi disertai oleh aksi penembakan.
    * Insiden kejahatan yang banyak terjadi secara bersamaan diantaranya yaitu : 
        * Larceny Theft From MV - Non Accesory dan Vandalism --> ada kemungkinan kegiatan perusakan/vandalisme diiringi dengan aksi pencurian atau sebaliknya
        * Assault-Aggravated-Battery dan Assault Simple-Battery --> ada kemungkinan kegiatan penyerangan yang bersifat ringan diikuti oleh penyerangan yang bersifat berat atau sebaliknya.
        * Assault Simple-Battery dan Threats To Do Bodily Harm --> ada kemungkinan ancaman untuk melakukan kekerasan diikuti oleh penyerangan yang bersifat ringan atau sebaliknya.

<br>

- `Apakah jumlah kejahatan berubah dari hari ke hari? Bulan? Tahun?`
    * Jumlah kasus tertinggi pada dataset terjadi pada tahun 2017 dan terdapat peningkatan dibandingkan kejadian pada tahun 2016. Namun kita tidak dapat membandingkan jumlah kasus pada tahun 2015 dan 2018 dikarenakan data untuk tahun 2015 hanya ada periode bulan Juni - Desember, sedangkan data tahun 2018 hanya ada periode bulan Januari - September.
    * Secara umum jumlah kasus kejahatan cenderung bersifat cyclical dimana jumlah kejahatan relatif meningkat pada bulan Maret-Agustus, kemudian cenderung turun pada bulan September - Februari dimana titik terendahnya terjadi di bulan Februari.
    * Jumlah kasus tertinggi cenderung terjadi pada bulan Juni - Agustus (periode musim panas) sedangkan jumlah kejahatan cenderung rendah pada bulan Desember (periode musim dingin)
    * Rata-rata jumlah kasus pada Weekday adalah 276 kasus/hari sedangkan pada Weekend adalah 251 kasus/hari.
    * Berdasarkan uji hipotesis, kita memiliki cukup bukti bahwa median jumlah kasus pada 'Weekday' TIDAK SAMA DENGAN median jumlah kasus pada 'Weekend'.
    * Jumlah kasus tertinggi terjadi pada hari Jumat sedangkan kasus terendah terjadi pada hari Minggu.
    * Secara harian kasus kejahatan cenderung bersifat siklikal dimana insiden kejahatan cenderung naik dari pukul 5:00 - 17:59 kemudian berangsur turun pada pukul 18:00 - 4:59.
    * Jumlah kasus tertinggi cenderung terjadi pada pukul 12:00 - 12:59 dan 16:00 - 18:59 sedangkan yang terendah pada pukul 4:00 - 5:59
    * Insiden kejahatan banyak terjadi pada Afternoon (12:00 - 19:59) dengan jumlah hampir 2 kali kejadian baik pada Morning (4:00 - 11:59) maupun Night (20:00 - 3:59)
    * Aggravated Assault, Larceny From Motor Vehicle, Simple Assaul dan Vandalism lebih sering terjadi di Weekend (Akhir Pekan)
    * Drug Violation, Larceny, Investigate Person, Medical Assistance, dan Motor Vehicle Accident Response lebih sering terjadi di Weekday (Hari Kerja)

<br>

- `Di mana berbagai jenis kejahatan paling mungkin terjadi?`
    * Jumlah kasus tertinggi terjadi di Distrik Roxbury, Dorchester dan South End. Dimana ketiga area ini saling berdekatan dengan Roxbury sebagai pusatnya (Dorchester terletak di sebelah Timur Roxbury, sedangkan South End terletak di sebelah Utara Roxbury.)
    * Kejahatan tertinggi selanjutnya terletak di sebelah Utara distrik South End yaitu Downstown dan di sebelah Selatan distrik Dorchester yaitu Mattapan
    * Sedangkan Distrik dengan jumlah kejahatan terendah adalah Charlestown.
    * Berdasarkan uji korelasi spearman, didapati hubungan positif antara variable jumlah area dengan jumlah kasus dimana jika jumlah area semakin banyak, maka jumlah kasus juga semakin tinggi. Nilai r = 0.67 juga menunjukkan bahwa jumlah area dan jumlah kasus memiliki hubungan yang kuat.
    * Roxbury sebagai District yang memiliki jumlah kasus tertinggi, memiliki jumlah area yang tinggi pula. Sedangkan Charlestown sebagai District dengan jumlah kasus terendah, memiliki jumlah area yang sedikit pula.
    * District West Roxbury dapat dianggap sebagai outlier dimana jumlah area banyak, namun jumlah kasus cukup rendah.
    * Jumlah kasus kejahatan dengan penembakan paling tinggi terjadi di District Roxburry dengan rata-rata terjadi 69 insiden penembakan per 10.000 kasus.
    * District dengan rate penembakan terendah terjadi di kota Downtown dimana hanya terjadi 3 insiden penembakan per 10.000 kasus.
    * District dengan kasus penembakan tertinggi setelah Roxbury, yaitu Mattapan, Dorchester, Jamaica Plain, dan South End relatif berdekatan dan berbatasan langsung dengan Roxbury
    * Dari table summary di atas kita dapat melihat bahwa jumlah kasus tertinggi untuk jenis kejahatan yang utama seperti 'Aggravated Assault', 'Drug Violation', 'Simple Assault', 'Vandalism', 'Motor Vehicle Accident Response', 'Medical Assistance', dan 'Investigate Person' terjadi di distrik Roxbury.
    * Sedangkan jumlah kasus tertinggi untuk jenis kejahatan 'Larceny' dan 'Larceny From Motor Vehicle' terjadi di distrik South End.

### REKOMENDASI
1. Dapat dipertimbangkan pelaksanaan sosialisasi terkait keselamatan lalu lintas atau penerapan sanksi yang lebih tegas atas pelanggaran lalu lintas , mengingat insiden kejahatan yang paling sering terjadi adalah Motor Vehicle Accident Response.
2. Memberikan pelatihan dasar bagi para Petugas Kepolisian terkait Pertolongan Pertama Pada Kecelakaan agar dapat memberikan bantuan medis (Medical Assitance) yang lebih baik.
3. Meningkatkan kewaspadaan atas penggunaan senjata api di masyarakat umum untuk menghindari kemungkinan terjadinya pembunuhan yang seringkali melibatkan insiden penembakan.
4. Mencermati adanya kemungkinan lebih dari satu tindak pidana yang dilakukan dalam satu kasus (misal adanya kemungkinan tindak pencurian dalam aksi vandalism, ancaman yang disertai aksi penyerangan, etc) agar penanganan kasus dapat lebih komprehensif dan tindak kejahatan yang lebih berat dapat dicegah.
5. Meningkatkan jumlah patroli pada periode-periode kritikal seperti pada bulan Juni - Agustus (musim panas), hari kerja (weekday) dan juga jam makan siang (12:00-12:59) serta jam pulang atau makan malam (16:00 - 18:59) seiring dengan tingginya aktivitas pada periode tersebut.
6. Menambah personil yang bertugas pada siang dan sore hari (12:00 - 19:59) karena kasus kejahatan cenderung meningkat 2x lipat pada periode tersebut.
7. Meningkatkan tingkat kewaspadaan pada jenis kejahatan tertentu di hari yang berbeda (misal Larceny di hari kerja, Vandalism di akhir pekan)
8. Menyesuaikan jumlah personil sesuai dengan jumlah area: semakin banyak area, maka semakin banyak pula personil yang harus ditugaskan.
9. Menkonsentrasikan atau meningkatkan frekuensi patroli di distrik Downstown, South End, Roxburry, Dorchester, dan Mattapan.

Diharapkan analisis ini bisa membantu Departemen Kepolisian Boston (BPD) dalam menerapkan strategi yang tepat untuk mencegah dan mengurangi terjadinya insiden kejahatan di Kota Boston.
