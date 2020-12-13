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
```
IPv4 Address 10.151.72.89 Subnet Mask 255.255.255.252       //SURABAYA yang mengarah ke Cloud
IPv4 Address 192.168.24.1 Subnet Mask 255.255.252.0         //SURABAYA yang mengarah ke PC SAMPANG
IPv4 Address 10.151.73.185 Subnet Mask 255.255.255.248      //SURABAYA yang mengarah ke MOJOKERTO
IPv4 Address 192.168.0.1 Subnet Mask 255.255.255.252        //SURABAYA yang mengarah ke PASURUAN
IPv4 Address 192.168.0.9 Subnet Mask255.255.255.252         //SURABAYA yang mengarah ke BATU
```
2. Pasuruan (Router)
```
IPv4 Address 192.168.0.2 Subnet Mask 255.255.255.252        //PASURUAN yang mengarah ke SURABAYA
IPv4 Address 192.168.20.1 Subnet Mask 255.255.252.0         //PASURUAN yang mengarah ke PC SIDOARJO
IPv4 Address 192.168.0.5 Subnet Mask 255.255.255.252        //PASURUAN yang mengarah ke PROBOLINGGO
```
3. Probolinggo (Router)
```
IPv4 Address 192.168.0.6 Subnet Mask 255.255.255.252       //PROBOLINGGO yang mengarah ke PASURUAN
IPv4 Address 192.168.8.1 Subnet Mask 255.255.248.0         //PROBOLINGGO yang mengarah ke PC JEMBER & BANYUWANGI
IPv4 Address 192.168.0.129 Subnet Mask 255.255.255.128     //PROBOLINGGO yang mengarah ke PC BONDOWOSO
```
4. Batu (Router)
```
IPv4 Address 192.168.0.10 Subnet Mask 255.255.255.252     //BATU yang mengarah ke SURABAYA
IPv4 Address 192.168.2.1 Subnet Mask 255.255.254.0        //BATU yang mengarah ke PC JOMBANG & ROUTER MADIUN
IPv4 Address 192.168.16.1 Subnet Mask 255.255.252.0       //BATU yang mengarah ke PC NGANJUK
IPv4 Address 192.168.0.13 Subnet Mask 255.255.255.252     //BATU yang mengarah ke KEDIRI
```
5. Madiun (Router)
```
IPv4 Address 192.168.2.2 Subnet Mask 255.255.254.0       //MADIUN yang mengarah ke PC JOMBANG & ROUTER BATU
IPv4 Address 192.168.0.17 Subnet Mask 255.255.255.240    //MADIUN yang mengarah ke PC BOJONEGORO
```
6. Kediri (Router)
```
IPv4 Address 192.168.0.14 Subnet Mask 255.255.255.252      //KEDIRI yang mengarah ke BATU
IPv4 Address 192.168.1.1 Subnet Mask 255.255.255.0         //KEDIRI yang mengarah ke PC LUMAJANG & ROUTER BLITAR
IPv4 Address 10.151.73.177 Subnet Mask 255.255.255.248     //KEDIRI yang mengarah ke MALANG (SERVER)
```
7. Blitar (Router)  
```
IPv4 Address 192.168.1.2 Subnet Mask 255.255.255.0       //BLITAR yang mengarah ke PC LUMAJANG & ROUTER KEDIRI
IPv4 Address 192.168.4.1 Subnet Mask 255.255.252.0       //BLITAR yang mengarah ke PC TULUNGAGUNG
```

- Atur IP pada client dan server dengan cara `Pilih tab Desktop > IP Configuration`
8. Sampang (Client)
```
IPv4 Address 192.168.24.2 Subnet Mask 255.255.252.0 Default Gateway 192.168.24.1
```
9. Bondowoso (Client)
```
IPv4 Address 192.168.0.130 Subnet Mask 255.255.255.128 Default Gateway 192.168.0.129
```
10. Jember (Client)
```
IPv4 Address 192.168.8.2 Subnet Mask 255.255.248.0 Default Gateway 192.168.8.1
```
11. Banyuwangi (Client)
```
IPv4 Address 192.168.12.1 Subnet Mask 255.255.248.0 Default Gateway 192.168.8.1
```
12. Sidoarjo (Client)
```
IPv4 Address 192.168.20.2 Subnet Mask 255.255.255.0 Default Gateway 192.168.20.1
```
13. Jombang (Client)
```
IPv4 Address 192.168.2.3 Subnet Mask 255.255.254.0 Default Gateway 192.168.2.1
```
14. Bojonegoro (Client)
```
IPv4 Address 192.168.0.18 Subnet Mask 255.255.255.240 Default Gateway 192.168.0.17
```
15. Nganjuk (Client)
```
IPv4 Address 192.168.16.2 Subnet Mask 255.255.252.0 Default Gateway 192.168.16.1
```
16. Lumajang (Client)
```
IPv4 Address 192.168.1.3 Subnet Mask 255.255.255.0 Default Gateway 192.168.1.1
```
17. Tulungagung (Client)
```
IPv4 Address 192.168.4.2 Subnet Mask 255.255.252.0 Default Gateway 192.168.4.1
```
18. Mojokerto (Server)
```
IPv4 Address 10.151.73.186 Subnet Mask 255.255.255.248 Default Gateway 10.151.73.185
```
19. Malang (Server)
```
IPv4 Address 10.151.73.178 Subnet Mask 255.255.255.248 Default Gateway 10.151.73.177
```

#### Routing
- Routing dilakukan pada menu <b>Config > Routing > Static</b> pada device <b>Router</b>. Lalu isi <i>Static Routes</i> dan tekan tombol Add
- Pada <i>static routing</i> juga dibutuhkan <b>default routing</b> agar router dapat mengirimkan paket sesuai dengan tujuan. Default routing dibutuhkan untuk router yang berada di bawah router utama (router yang terhubung internet).
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
![Pembagian Subnet1](https://user-images.githubusercontent.com/61286109/102002015-01527000-3d2b-11eb-978d-79dd8b60463f.PNG) <br>

#### Konfigurasi Pada Tiap UML
1. Pertama, membuat file `topologi.sh`.<br>
![Konfigurasi UML T6](https://user-images.githubusercontent.com/61286109/102001540-03fe9680-3d26-11eb-8bfe-1762a7c4d335.PNG) <br>
![Konfigurasi2 UML T6](https://user-images.githubusercontent.com/61286109/101959482-fff44b00-3c37-11eb-9ccd-ff1f8017fc9a.PNG) <br>
2. Pada semua UML Router, ke file `nano /etc/sysctl.conf` kemudian uncomment `net.ipv4.ip_forward=1` dan aktifkan dengan syntax `sysctl -p`.
3. Lakukan setting interface pada semua UML di `nano /etc/network/interfaces` dan di restart dengan syntax `service networking restart`. <br>
- ROUTER SURABAYA <br>
![iface sby1](https://user-images.githubusercontent.com/61286109/102002117-f9df9680-3d2b-11eb-91ad-64b28e515c0c.PNG)
![iface sby2](https://user-images.githubusercontent.com/61286109/101999630-892b8080-3d11-11eb-9c52-c72016beb29e.PNG) <br>
- ROUTER PASURUAN <br>
![iface pasuruan](https://user-images.githubusercontent.com/61286109/102002377-930fac80-3d2e-11eb-9169-3666ad9d23d2.PNG) <br>
- ROUTER PROBOLINGGO <br>
![iface probolinggo](https://user-images.githubusercontent.com/61286109/102002307-ca318e00-3d2d-11eb-8ba3-7e120b4a6233.PNG) <br>
- ROUTER BATU <br>
![iface batu1](https://user-images.githubusercontent.com/61286109/102001674-5ee4bd80-3d27-11eb-85d0-4a74e2c45f4c.PNG)
![iface batu2](https://user-images.githubusercontent.com/61286109/102001675-6015ea80-3d27-11eb-9994-6c04b185785f.PNG) <br>
- ROUTER MADIUN <br>
![iface madiun](https://user-images.githubusercontent.com/61286109/102000355-4077c580-3d19-11eb-8a49-a19bf3068ca5.PNG) <br>
- ROUTER KEDIRI <br>
![iface kediri](https://user-images.githubusercontent.com/61286109/102000352-3f469880-3d19-11eb-8db3-b56d67efe068.PNG) <br>
- ROUTER BLITAR <br>
![iface blitar](https://user-images.githubusercontent.com/61286109/102000367-48376a00-3d19-11eb-804b-e3553e99858a.PNG) <br>
- SERVER MOJOKERTO <br>
![iface mojokerto](https://user-images.githubusercontent.com/61286109/102000357-41a8f280-3d19-11eb-8491-c11562930f4f.PNG) <br>
- SERVER MALANG <br>
![iface malang](https://user-images.githubusercontent.com/61286109/102000356-41105c00-3d19-11eb-8c80-9a973ccb0194.PNG) <br>
- KLIEN SAMPANG <br>
![iface sampang](https://user-images.githubusercontent.com/61286109/102000362-440b4c80-3d19-11eb-9412-73590e8fb1f1.PNG) <br>
- KLIEN BONDOWOSO <br>
![iface bondowoso](https://user-images.githubusercontent.com/61286109/102000346-3bb31180-3d19-11eb-9969-e75d60034377.PNG) <br>
- KLIEN JEMBER <br>
![iface jember](https://user-images.githubusercontent.com/61286109/102000350-3d7cd500-3d19-11eb-9a84-f2bb08feb694.PNG) <br>
- KLIEN BANYUWANGI <br>
![iface banyuwangi](https://user-images.githubusercontent.com/61286109/102000366-47063d00-3d19-11eb-9048-aaa393f9f67a.PNG) <br>
- KLIEN SIDOARJO <br>
![iface sidoarjo](https://user-images.githubusercontent.com/61286109/102000363-45d51000-3d19-11eb-86a9-00a6b3cfc818.PNG) <br>
- KLIEN JOMBANG <br>
![iface jombang](https://user-images.githubusercontent.com/61286109/102000351-3e156b80-3d19-11eb-83ea-17ff09d6ad62.PNG) <br>
- KLIEN BOJONEGORO <br>
![iface bojonegoro](https://user-images.githubusercontent.com/61286109/102000368-48376a00-3d19-11eb-9326-46c19509c438.PNG) <br>
- KLIEN NGANJUK <br>
![iface nganjuk](https://user-images.githubusercontent.com/61286109/102000358-42418900-3d19-11eb-95a0-03b7b769a9e7.PNG) <br>
- KLIEN LUMAJANG <br>
![iface lumajang](https://user-images.githubusercontent.com/61286109/102000354-4077c580-3d19-11eb-9cd9-8adca91709c1.PNG) <br>
- KLIEN TULUNGAGUNG <br>
![iface tulungagung](https://user-images.githubusercontent.com/61286109/102000365-466da680-3d19-11eb-9140-ff1f22faef93.PNG) <br>
4. Pada UML SURABAYA jalankan syntax `iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE –s 192.168.0.0/16.` agar semua UML terhubung ke internet.
5. Lakukan Routing terhadap <b>Router Surabaya, Pasuruan, Batu dan Kediri</b> dengan membuat file dengan `nano routing.sh` untuk memudahkan kita karena pada saat setiap UML di restart maka routenya ke reset. Untuk menjalankannya ketik syntax `source routing.sh`.
- ROUTER SURABAYA (ROUTING) <br>
![routing sby](https://user-images.githubusercontent.com/61286109/102002511-c7d03380-3d2f-11eb-951a-08d954f7a36b.PNG)
![route sby](https://user-images.githubusercontent.com/61286109/102002510-c56dd980-3d2f-11eb-9497-0aa15231601b.PNG)<br>
- ROUTER PASURUAN (ROUTING) <br>
![routing pasuruan](https://user-images.githubusercontent.com/61286109/102002514-cacb2400-3d2f-11eb-8d53-96997451670f.PNG)
![route pasuruan](https://user-images.githubusercontent.com/61286109/102002513-ca328d80-3d2f-11eb-963a-45e764edf4d6.PNG)<br>
- ROUTER BATU (ROUTING) <br>
![routing batu](https://user-images.githubusercontent.com/61286109/102002864-64480500-3d33-11eb-87e2-30fbcc273b87.PNG)
![route batu](https://user-images.githubusercontent.com/61286109/102002866-6611c880-3d33-11eb-85cf-cd2e88d4f4e4.PNG)<br>
- ROUTER KEDIRI (ROUTING) <br>
![routing kediri](https://user-images.githubusercontent.com/61286109/102002865-6611c880-3d33-11eb-820f-dcb5762e7577.PNG)
![route kediri](https://user-images.githubusercontent.com/61286109/102002867-6742f580-3d33-11eb-9eb2-46d3281178c3.PNG)<br>

#### Testing
1. 
2.
3.
4.
5.
