# Jarkom_Modul4_Lapres_T06
<b> Laporan Resmi Praktikum Jaringan Komputer </b> <br>
Modul 4 - SUBNETTING AND ROUTING <br>
Kelompok T06
1. Hana Ghaliyah Azhar  (05311840000032)
2. Azmi                 (05311840000047)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### SOAL
![Soal Shift Modul 4](https://user-images.githubusercontent.com/26424136/101798768-0ef6d280-3b3e-11eb-990d-b051a19735c1.png)

#### Catatan
1. <b>Cisco Packet Tracer</b> dan <b>UML</b> menggunakan metode perhitungan CLASSLESS yang <b>berbeda</b>. 
Keterangan: Bila di <b>CPT menggunakan VLSM</b>, maka di <b>UML menggunakan CIDR</b> atau <b>sebaliknya</b>.
2. <b>CLOUD</b> diberikan IP TUNTAP
3. Server diberikan IP DMZ
4. Berikan memori sebesar <b>64MB</b> pada <b>setiap UML</b>
5. Pembagian IP dan routing harus <b>SEEFISIEN MUNGKIN</b>.
6. Pastikan semua UML dapat melakukan ping ke its.ac.id

### PENYELESAIAN
#### Pembagian IP
- Menentukan jumlah subnet yang ada pada topologi <br>
<img width="468" alt="topologi soal shift" src="https://user-images.githubusercontent.com/26424136/101800967-757cf000-3b40-11eb-9434-1f4587f9aced.PNG"> <br>
Terdapat 13 subnet di dalam topologi. <br>

- Metode Classless: <b>VLSM (Variable Length Subnet Masking)</b>
1. Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan <i>labelling</i> netmask berdasarkan jumlah IP yang dibutuhkan. <br>
<img width="181" alt="vlsm 1" src="https://user-images.githubusercontent.com/26424136/101802827-7747b300-3b42-11eb-8e04-ee7f2eaf9ff0.PNG"> <br>
Berdasarkan total IP dan netmask yang dibutuhkan, maka kita dapat menggunakan netmask <b>/19</b> untuk memberikan pengalamatan IP pada subnet. <br>
2. Hitung pembagian IP dan Lakukan subnetting dengan menggunakan pohon tersebut untuk pembagian IP sesuai dengan kebutuhan masing-masing subnet yang ada. <br>
![pohon pembagian IP VLSM](https://user-images.githubusercontent.com/26424136/101801011-80d01b80-3b40-11eb-9854-a8a654af22d0.png) <br>
3. Dari pohon tersebut akan mendapat pembagian IP sebagai berikut. <br>
<img width="317" alt="vlsm 2" src="https://user-images.githubusercontent.com/26424136/101802833-79117680-3b42-11eb-9bc0-6e4380ee5f62.PNG"> <br>

#### Routing
ONGOING
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### PENYELESAIAN
#### Pembagian IP
- Menentukan subnet yang ada dalam topologi dan lakukan labelling netmask terhadap masing-masing subnet kemudian menggabungkan subnet-subnet sampain menjadi subnet besar. <br>
![Soal Shift Modul 4 CIDR](https://user-images.githubusercontent.com/61286109/101828554-4aa49300-3b64-11eb-9e4a-820dc2e9d676.PNG) <br>
 Subnet besar dalam topologi di atas yaitu <b>/17</b><br>

- Metode Classless <b>CIDR (Classless Inter Domain Routing)</b>
1. Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan <i>labelling</i> netmask berdasarkan jumlah IP yang dibutuhkan. <br>
![Labelling Netmask](https://user-images.githubusercontent.com/61286109/101823151-edf1aa00-3b5c-11eb-8ae1-e6922df3711a.PNG) <br>
Berdasarkan total IP dan netmask yang dibutuhkan, maka kita dapat menggunakan netmask <b>/19</b> untuk memberikan pengalamatan IP pada subnet. <br>
2. Hitung pembagian IP dan Lakukan subnetting dengan menggunakan pohon tersebut untuk pembagian IP sesuai dengan kebutuhan masing-masing subnet yang ada. <br>
![Tree CIDR T6](https://user-images.githubusercontent.com/61286109/101823687-bc2d1300-3b5d-11eb-8ca1-b6790de6ad1d.png) <br>
3. Dari pohon tersebut akan mendapat pembagian IP sebagai berikut. <br>
![Pembagian Subnet1](https://user-images.githubusercontent.com/61286109/101824064-470e0d80-3b5e-11eb-8ab4-60e4ee9b9059.PNG) <br>
