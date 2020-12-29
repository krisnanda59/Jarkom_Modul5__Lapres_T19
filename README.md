# Jarkom_Modul5_Lapres_T19
Penyelesaian Soal Shift 5 Komunikasi Data, dan Jaringan Data 2020\
Kelompok T19
  * Made Krisnanda Utama (05311840000033)
  * Muhammad Irsyad Ali (05311840000041)


---

## Tahap Persiapan
### A: Pembuatan Topologi
 - Pertama-tama kami membuat file ```topologi.sh``` dengan isi seperti dibawah;
  
  ![topologi_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/topologi_persiapan.png)
 
 
 
### B: Subnetting(CIDR)
 - Pertama-tama kita membagi subnet, lalu menghitungnya di tiap bagian seperti dibawah;
  
  ![subnetting_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/pembagian%20subnet_persiapan.png)
   
   - Gabungkan Host A1 - A2 & A5 - A6 hingga membentuk Host baru yaitu B1 & B2 dengan Subnet Mask /23.
   - Kemudian gabungkan Host B1 - A3 & B2 - A4 hingga membentuk Host baru yaitu C1 & C2 dengan Subnet Mask /22.
   - Terakhir gabungkan Host C1 - C2 hingga membentuk Host baru yaitu D1 dengan Subnet Mask /21.
 - Dengan pembulatan yang telah diperoleh kami dapat membuat IP tree, seperti berikut;
  
  ![subnetting_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/tree_persiapan.png)
 
 - Dari pohon tersebut akan mendapat pembagian IP sebagai berikut;  
  
  ![subnetting_3](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/Pembagian%20IP_persiapan(%20ditulis%20jangan%20dimasukin%20gambar).png)

 - Kemudian pada semua UML Router, ke file ```/etc/sysctl.conf``` kemudian uncomment ```net.ipv4.ip_forward=1```, dan aktifkan dengan syntax ```sysctl -p```.
 - Disini kami melakukan subnetting pada setiap UML berdasarkan pembagian IP yang sudah dilakukan, subentting dilakukan pada ```/etc/network/interfaces``` 
 - Setelah itu UML di restart menggunakan ```service networking restart```.  
   
  # Berikut subnetting yang dilakukan pada semua UML: 
   - Router *SURABAYA*
    
     ![topologi_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20surabaya_persiapan.png)
   
   - Router *KEDIRI*  
     
     ![topologi_3](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20kediir_persiapan.png)
   
   - Router *BATU*  
     
     ![topologi_4](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20batu_persiapan.png)
   
   - Server *MADIUN*  
     
     ![topologi_5](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20madiun_persiapan.png)
   
   - Server *PROBOLINGGO*  
     
     ![topologi_6](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20probolinggo_persiapan.png)
   
   - Server *MALANG*  
     
     ![topologi_7](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20malang_persiapan.png)
   
   - Server *MOJOKERTO*  
     
     ![topologi_8](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20mojokerto_persiapan.png)
   
   - Klien *GRESIK*  
     
     ![topologi_9](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20gresik_persiapan.png)
   
   - Klien *SIDOARJO*  
     
     ![topologi_10](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/interfaces%20sidoarjo_persiapan.png)
 

### C: Routing
 - Routing dilakukan dengan mengisi file ```etc/network/interface```.
 - Kemudian isi file route.sh pada UML  *SURABAYA* dan *KEDIRI*.
   
  ![routing_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/routing%20surabaya_persiapan.png)
   
  ![routing_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/routing%20kediri_persiapan.png)
 
 
### D: DHCP Relay dan DHCP Server
 - Pertama isi file ```/etc/dhcp/dhcpd.conf``` pada UML *MOJOKERTO*.
 - Kemudian isi file ```/etc/default/isc-dhcp-relay``` pada UML *SURABAYA*, *KEDIRI*, *BATU*, dan *MOJOKERTO*.
 
## Soal
### Nomor 1
Soal 1 meminta kami untuk membuat topologi yang sudah dibuat dapt mengakses keluar, maka diminta untuk membuat konfigurasi pada *SURABAYA* tanapa menggunakan *Masquerade*
 - Pertama Konfigurasikan UML *SURABAYA* dengan syntax berikut;  
```iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o eth0 -j SNAT --to-source 10.151.76.82```
* -t nat NAT merupakan table yang kami guanakan
* -A POSTROUTING POSTROUTING sebagai chain yang digunakan
* -j SNAT mengubah source address yang awalnya berupa private IPv4 address, menjadi --to-source 10.151.70.66 yaitu IP eth0 SURABAYA kelopok t19 karena SURABAYA adalah satu-
satunya router yang terhubung ke cloud melalui eth0.
  
  ![1_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_syntax.png)
  
 - Kemudian hasilnya seperti dibawah;   
 
  ![1_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_surabaya%20berhasil%20ping.png)  
  
  ![1_3](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_sidoarjo%20berhasil%20ping.png)  
  
  ![1_4](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_probolinggo%20berhasil%20ping.png)  
  
  ![1_5](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_mojokerto%20berhasil%20ping.png)  
  
  ![1_6](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_malang%20berhasil%20ping.png)  
  
  ![1_7](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_madiun%20berhasil%20ping.png)  
  
  ![1_8](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_kediri%20berhasil%20ping.png)  
  
  ![1_9](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_gresik%20berhasil%20ping.png)  
  
  ![1_10](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_bukti_batu%20berhasil%20ping.png)  
 
### Nomor 2
Soal meminta kami untuk mendrop semua akses SSH dari luar Topologi (UML) Kalian pada server yang memiliki ip DMZ (DHCP dan DNS SERVER) pada SURABAYA demi menjaga keamanan.
 - Pertama Konfigurasikan UML *SURABAYA* dengan syntax berikut;  
```iptables -A FORWARD -p tcp --dport 22 -d 10.151.71.128/29 -i eth0 -j DROP```
* -A FORWARD FORWARD sebagai chain yang kami gunakan untuk menyaring paket dengan protokol TCP dari luar topologi menuju ke DHCP Server MOJOKERTO dan DNS Server MALANG
* -p tcp mendefinisakn paket dengan protokol apa yang akan di filter
* --dport 22 mendefinisikan paket dengan port berapa yang akan di filter
* - d 10.151.77.160/29 -i eth0 merupakan ip destionation
* -j DROP adalah action yang digunakan dimana akan membuang semua paket yang tidak memenuhi kriteria filter.

  ![2_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%202_syntax.png)

 - Kemudian hasilnya seperti dibawah;
 
  ![2_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%202_bukti_mengirim%20paket%20dari%20luar%20ke%20malang%20sebagai%20contoh.png)  
 
### Nomor 3
Soal meminta kami untuk membatasi DHCP dan DNS server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan yang berasal dari mana saja menggunakan iptables pada masing 
masing server, selebihnya akan di DROP.

- Pertama Konfigurasikan UML *MALANG&MOJOKERTO* dengan syntax berikut;  
```iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j REJECT```
* -A INPUT merupakan chain yang kami gunakan untuk memfilter paket yang menuju jaringan lokal
* -p icmp merupakan pendefinisian protokol yang digunakan
* --connlimit-above 3 memberikan batas maksimal koneksi yaitu 3
* --conlimit-mask 0 mendefinisikan untuk paket yang berasal darimana saja
* -j REJECT merukana action yang digunakan berfungsi untuk menolak koneksi keempat dengan di DROP.  
  
  ![3_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_syntax.png)

 - Kemudian hasilnya seperti dibawah; 
  
  ![3_2](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_%20bukti_uml%20ke%201%20yang%20ping%20ke%20malang(tidak%20di%20drop)_nomor%203.png)  
  
  ![3_3](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_%20bukti_uml%20ke%202%20yang%20ping%20ke%20malang(tidak%20di%20drop)_nomor%203.png)  
  
  ![3_4](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_%20bukti_uml%20ke%203%20yang%20ping%20ke%20malang(tidak%20di%20drop)_nomor%203.png)  
  
  ![3_5](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_%20bukti_uml%20ke%204%20yang%20ping%20ke%20malang(berhasil%20didrop)_nomor%203.png)  
  
  
 




