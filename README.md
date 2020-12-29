# Jarkom_Modul5_Lapres_T19
Penyelesaian Soal Shift 5 Komunikasi Data, dan Jaringan Data 2020\
Kelompok T19
  * Made Krisnanda Utama (05311840000033)
  * Muhammad Irsyad Ali (05311840000041)


---

## Tahap Persiapan
### Pembuatan Topologi
 Pertama-tama kami membuat file ```topologi.sh``` dengan isi seperti dibawah;
  ![topologi_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/topologi_persiapan.png)
 
### Subnetting(CIDR)
 - Pertama-tama kita membagi subnet, lalu menghitungnya di tiap bagian seperti dibawah;
  ![subnetting_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/pembagian%20subnet_persiapan.png)
   - Gabungkan Host A1 - A2 & A5 - A6 hingga membentuk Host baru yaitu B1 & B2 dengan Subnet Mask /23.
   - Kemudian gabungkan Host B1 - A3 & B2 - A4 hingga membentuk Host baru yaitu C1 & C2 dengan Subnet Mask /22.
   - Terakhir gabungkan Host C1 - C2 hingga membentuk Host baru yaitu D1 dengan Subnet Mask /21.
 - Kemudian menghitung IP Address yang dibutuhkan contohnya: Jumlah Host, Router, dan Server.
  ![subnetting_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/Pembagian%20IP_persiapan(%20ditulis%20jangan%20dimasukin%20gambar).png)\
 - Terakhir kami membuat IP treenya berdasarkan pembagian subnet yang tadi seperti dibawah;
  ![subnetting_3](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/tree_persiapan.png)

 ### Routing
  - Routing dilakukan dengan mengisi file ```etc/network/interface```.
  - Kemudian isi file route.sh pada uml *SURABAYA* dan *KEDIRI*.
   ![routing_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/routing%20surabaya_persiapan.png)
   ![routing_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/routing%20kediri_persiapan.png)
 
### DHCP Relay dan DHCP Server
 
 
## Soal
### Nomor 1
 
 
### Nomor 2


### Nomor 3
