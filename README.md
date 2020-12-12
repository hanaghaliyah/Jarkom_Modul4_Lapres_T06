# Jarkom_Modul4_Lapres_T06
<b> Laporan Resmi Praktikum Jaringan Komputer </b> <br>
Modul 4 - SUBNETTING AND ROUTING <br>
Kelompok T06
1. Hana Ghaliyah Azhar  (05311840000032)
2. Azmi                 (05311840000047)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## SOAL
![Soal Shift Modul 4](https://user-images.githubusercontent.com/26424136/101798768-0ef6d280-3b3e-11eb-990d-b051a19735c1.png)

### Catatan
1. <b>Cisco Packet Tracer</b> dan <b>UML</b> menggunakan metode perhitungan CLASSLESS yang <b>berbeda</b>. 
Keterangan: Bila di <b>CPT menggunakan VLSM</b>, maka di <b>UML menggunakan CIDR</b> atau <b>sebaliknya</b>.
2. <b>CLOUD</b> diberikan IP TUNTAP
3. Server diberikan IP DMZ
4. Berikan memori sebesar <b>64MB</b> pada <b>setiap UML</b>
5. Pembagian IP dan routing harus <b>SEEFISIEN MUNGKIN</b>.
6. Pastikan semua UML dapat melakukan ping ke its.ac.id

## PENYELESAIAN
### CPT Menggunakan Metode Classless VLSM (Variable Length Subnet Masking)
#### Subnetting (Pembagian IP)
- Menentukan jumlah subnet yang ada pada topologi <br>
<img width="468" alt="topologi soal shift" src="https://user-images.githubusercontent.com/26424136/101800967-757cf000-3b40-11eb-9434-1f4587f9aced.PNG"> <br>
Terdapat 13 subnet di dalam topologi. <br>
B1 : 10.151.73.184 <br>
B2 : 10.151.73.176 <br>
<b>NB:</b> server menggunakan ip dmz
- Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan <i>labelling</i> netmask berdasarkan jumlah IP yang dibutuhkan. <br>
<img width="181" alt="vlsm 1" src="https://user-images.githubusercontent.com/26424136/101802827-7747b300-3b42-11eb-8e04-ee7f2eaf9ff0.PNG"> <br>
Berdasarkan total IP dan netmask yang dibutuhkan, maka kita dapat menggunakan netmask <b>/19</b> untuk memberikan pengalamatan IP pada subnet. <br>
- Hitung pembagian IP dan Lakukan subnetting dengan menggunakan pohon tersebut untuk pembagian IP sesuai dengan kebutuhan masing-masing subnet yang ada. <br>
![pohon pembagian IP VLSM](https://user-images.githubusercontent.com/26424136/101984456-21931800-3cb4-11eb-8f6a-e3c72a7aa81c.png) <br>
- Dari pohon tersebut akan mendapat pembagian IP sebagai berikut. <br>
<img width="317" alt="vlsm 2" src="https://user-images.githubusercontent.com/26424136/101802833-79117680-3b42-11eb-9bc0-6e4380ee5f62.PNG"> <br>

#### Mengatur Interface pada CPT
- Atur IP untuk masing-masing interface yang ada di setiap device sesuai dengan pembagian subnet pada pohon VLSM.
- Interface dapat diatur pada menu `Config > INTERFACE > “nama interface”`. Isi alamat IP dan subnet mask dari subnet interface tersebut. <br>
<b>NB:</b> Untuk melihat arah port, dapat menghover device pada saat di <i>logic view</i>, atau dapat selalu diaktifkan di `Options > Preferences > Always Show Port Labels in Logical Workspace`
1. Surabaya (Router)
Atur IP pada interface `FastEthernet0/1` SURABAYA yang mengarah ke Cloud
```
IPv4 Address 10.151.72.89 Subnet Mask 255.255.255.252
```
Atur IP pada interface `FastEthernet0/0` SURABAYA yang mengarah ke PC SAMPANG
```
IPv4 Address 192.168.24.1 Subnet Mask 255.255.252.0
```
Atur IP pada interface `Ethernet1/0` SURABAYA yang mengarah ke MOJOKERTO (server)
```
IPv4 Address 10.151.73.185 Subnet 255.255.255.248
```
Atur IP pada interface `Ethernet1/1` SURABAYA yang mengarah ke PASURUAN
```
IPv4 Address 192.168.0.1 Subnet 255.255.255.252
```
Atur IP pada interface `Ethernet1/2` SURABAYA yang mengarah ke BATU
```
IPv4 Address 192.168.0.9 Subnet 255.255.255.252
```

#### Routing
1. Pada Surabaya
```
Network 192.168.0.128 Netmask 255.255.255.128 Next Hop 192.168.0.2
Network 192.168.8.0 Netmask 255.255.248.0 Next Hop 192.168.0.2
Network 192.168.20.0 Netmask 255.255.252.0 Next Hop 192.168.0.2
Network 192.168.0.4 Netmask 255.255.255.252 Next Hop 192.168.0.2
Network 192.168.16.0 Netmask 255.255.252.0 Next Hop 192.168.0.10
Network 192.168.2.0 Netmask 255.255.254.0 Next Hop 192.168.0.10
Network 192.168.0.16 Netmask 255.255.255.240 Next Hop 192.168.0.10
Network 192.168.1.0 Netmask 255.255.255.0 Next Hop 192.168.0.10
Network 192.168.4.0 Netmask 255.255.252.0 Next Hop 192.168.0.10
Network 10.151.73.176 Netmask 255.255.255.248 Next Hop 192.168.0.10
Network 192.168.0.12 Netmask 255.255.255.252 Next Hop 192.168.0.10
```
2. Pada Pasuruan
```
Network 192.168.0.128 Netmask 255.255.255.128 Next Hop 192.168.0.6
Network 192.168.8.0 Netmask 255.255.248.0 Next Hop 192.168.0.6
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.0.1
```
3. Pada Probolinggo
```
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.0.5
```
4. Pada Batu
```
Network 192.168.0.16 Netmask 255.255.255.240 Next Hop 192.168.2.2
Network 192.168.1.0 Netmask 255.255.255.0 Next Hop 192.168.0.14
Network 192.168.4.0 Netmask 255.255.252.0 Next Hop 192.168.0.14
Network 10.151.73.176 Netmask 255.255.255.248 Next Hop 192.168.0.14
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.0.9
```
5. Pada Madiun
```
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.2.1
```
6. Pada Kediri
```
Network 192.168.4.0 Netmask 255.255.252.0 Next Hop 192.168.1.2
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.0.13
```
7. Pada Blitar
```
Network 0.0.0.0 Netmask 0.0.0.0 Next Hop 192.168.1.1
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### UML Menggunakan Metode Classless CIDR (Classless Inter Domain Routing)
#### Topologi dan Pembagian IP
1. Menentukan subnet yang ada dalam topologi dan lakukan labelling netmask terhadap masing-masing subnet kemudian menggabungkan subnet-subnet sampai menjadi subnet besar. <br>
![Subnetting CIDR T6](https://user-images.githubusercontent.com/61286109/101955213-febf2000-3c2f-11eb-86a7-a62a38707eaf.PNG) <br>
Hasil yang didapat adalah <b>Netmask /16</b> untuk subnet besar topologi diatas. <br> 
2. Pembagian IP dengan pohon berdasarkan penggabungan subnet yang telah dilakukan.. <br>
![Pohon CIDR T6](https://user-images.githubusercontent.com/61286109/101984162-3a023300-3cb2-11eb-8ebd-ab3ac6c1044d.png) <br>
3. Dari pohon tersebut akan mendapat pembagian IP sebagai berikut. <br>
![Pembagian Subnet1](https://user-images.githubusercontent.com/61286109/101958235-89eee480-3c35-11eb-9b36-d3a997064abb.PNG) <br>

#### Konfigurasi Pada Tiap UML
1. Pertama, membuat file `topologi.sh`.<br>
![Konfigurasi UML T6](https://user-images.githubusercontent.com/61286109/101959345-bad01900-3c37-11eb-88c9-2474700139ee.PNG) <br>
![Konfigurasi2 UML T6](https://user-images.githubusercontent.com/61286109/101959482-fff44b00-3c37-11eb-9ccd-ff1f8017fc9a.PNG) <br>
2. 
