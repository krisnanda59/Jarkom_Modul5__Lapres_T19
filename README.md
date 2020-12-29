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
 - Pertama Konfigurasikan UML *SURABAYA* dengan syntax berikut;  
```iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o eth0 -j SNAT --to-source 10.151.76.82```
  ![1_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal1_syntax.png)
 
### Nomor 2
 - Pertama Konfigurasikan UML *SURABAYA* dengan syntax berikut;  
```iptables -A FORWARD -p tcp --dport 22 -d 10.151.77.160/29 -i eth0 -j DROP```
  ![2_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%202_syntax.png)

### Nomor 3
 - Pertama Konfigurasikan UML *MALANG&MOJOKERTO* dengan syntax berikut;  
```iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j REJECT```
  ![3_1](https://github.com/krisnanda59/Jarkom_Modul5__Lapres_T19/blob/main/dokum%20shift%205/soal%203_syntax.png)




