# Jarkom-Modul-4-E12-2021

<hr/>

#### Anggota Kelompok :
 * Rahadian Adjie Mahesa &nbsp;(05111940000221)
 * Ahmad Luthfi Hanif &nbsp; (05111940000179)
 * Afifan Syafaqi Yahya &nbsp; (05111940000234)  

#### Prefix IP 
Address untuk Prefix IP Kelompok kami adalah `10.35`

<hr/>

## Topologi dan Persiapan
  
  
<hr/>
  
## VLSM - GNS3
Langkah pertama yang kita lakukan adalah untuk membagi topologi yang sudah diberikan pada soal seperti berikut

![Subnet fix](https://user-images.githubusercontent.com/55140514/143681917-dadbc166-3b4b-4ba4-a602-0a8ea236660d.png)

Setelah terbagi kita menghitung jumlah IP yang diperlukan dengan menghitung tiap-tiap bagian subnet. Selain jumlah IP kita juga menghitung netmask nya. Hasil yang kami dapatkan adalah sebagai berikut

| subnet | alias                     | jumlah ip | netmask |
|--------|---------------------------|-----------|---------|
| A1     | foosha-water7             | 2         | /30     |
| A2     | Water7-cipher             | 701       | /22     |
| A3     | water7-pucci              | 2         | /30     |
| A4     | pucci-jipangu             | 101       | /25     |
| A5     | pucci-courtyard-calmbelt  | 2021      | /21     |
| A6     | foosha-blueno             | 1001      | /22     |
| A7     | foosha-doriki             | 2         | /30     |
| A8     | foosha-guanhao            | 2         | /30     |
| A9     | guanhao-jabra             | 521       | /22     |
| A10    | guanhao-maingate-alabasta | 502       | /23     |
| A11    | alabasta-jorge            | 13        | /28     |
| A12    | guanhao-oimo              | 2         | /30     |
| A13    | oimo-enieslobby-seastone  | 252       | /24     |
| A14    | oimo-fukurou              | 2         | /30     |
| A15    | seastone-elena            | 721       | /22     |
| total  |                           | 5845      | /19     |

Berdasarkan perhitungan kami di table tersebut, jumlah ip yang didapatkan adalah `5845` dan root menggunakan netmask `/19`. Setelah kita menentukan itu, kita menyusun pohon subnet seperti berikut

![10 35 0 0-19](https://user-images.githubusercontent.com/55140514/143682331-c6c5f36d-4d19-4bb9-8014-f921a6b136c5.png)

Dengan sudah tersusunnya pohon tersebut maka kita bisa mendapatkan **NID** masing-masing subnet seperti berikut

| Subnet | Alias                     | Jumlah IP | Netmask | NID          |
|--------|---------------------------|-----------|---------|--------------|
| A1     | foosha-water7             | 2         | /30     | 10.35.27.144 |
| A2     | Water7-cipher             | 701       | /22     | 10.35.8.0    |
| A3     | water7-pucci              | 2         | /30     | 10.35.27.148 |
| A4     | pucci-jipangu             | 101       | /25     | 10.35.27.0   |
| A5     | pucci-courtyard-calmbelt  | 2021      | /21     | 10.35.0.0    |
| A6     | foosha-blueno             | 1001      | /22     | 10.35.12.0   |
| A7     | foosha-doriki             | 2         | /30     | 10.35.27.152 |
| A8     | foosha-guanhao            | 2         | /30     | 10.35.27.156 |
| A9     | guanhao-jabra             | 521       | /22     | 10.35.16.0   |
| A10    | guanhao-maingate-alabasta | 502       | /23     | 10.35.24.0   |
| A11    | alabasta-jorge            | 13        | /28     | 10.35.27.128 |
| A12    | guanhao-oimo              | 2         | /30     | 10.35.27.160 |
| A13    | oimo-enieslobby-seastone  | 252       | /24     | 10.35.26.0   |
| A14    | oimo-fukurou              | 2         | /30     | 10.35.27.165 |
| A15    | seastone-elena            | 721       | /22     | 10.35.20.0   |
| Total  |                           | 5845      | /19     |              |

Langkah selanjutnya adalah kita membuat topologi pada **GNS3** sesuai dengan keinginan soal. Untuk Topologi pada **GNS3** berbeda dimana diantara semua node akan digunakan *Switch*. Hasil topologi seperti berikut

![image](https://user-images.githubusercontent.com/55140514/143682652-b2c36d19-1551-40c9-b8ed-507b5c14734b.png)

Setelah terbuat topologi nya, kita lanjut dengan melakukan konfigurasi setiap node. Sebelum itu, kita melakukan `Pembagian IP` lagi untuk IP tiap Node seperti berikut

| Subnet | Node       | IP           | Subnet Mask     | Length |
|--------|------------|--------------|-----------------|--------|
| A1     | Foosha     | 10.35.27.145 | 255.255.255.252 | /30    |
|        | Water7     | 10.35.27.146 | 255.255.255.252 |        |
| A2     | Water7     | 10.35.8.1    | 255.255.252.0   | /22    |
|        | Cipher     | 10.35.8.2    | 255.255.252.0   |        |
| A3     | Water7     | 10.35.27.149 | 255.255.255.252 | /30    |
|        | Pucci      | 10.35.27.150 | 255.255.255.252 |        |
| A4     | Pucci      | 10.35.27.1   | 255.255.255.128 | /25    |
|        | Jipanggu   | 10.35.27.2   | 255.255.255.128 |        |
| A5     | Pucci      | 10.35.0.1    | 255.255.248.0   | /21    |
|        | Courtyard  | 10.35.0.2    | 255.255.248.0   |        |
|        | Calmbelt   | 10.35.0.3    | 255.255.248.0   |        |
| A6     | Foosha     | 10.35.12.1   | 255.255.252.0   | /22    |
|        | Blueno     | 10.35.12.2   | 255.255.252.0   |        |
| A7     | Foosha     | 10.35.27.153 | 255.255.255.252 | /30    |
|        | Doriki     | 10.35.27.154 | 255.255.255.252 |        |
| A8     | Foosha     | 10.35.27.157 | 255.255.255.252 | /30    |
|        | Guanhao    | 10.35.27.158 | 255.255.255.252 |        |
| A9     | Guanhao    | 10.35.16.1   | 255.255.252.0   | /22    |
|        | Jabra      | 10.35.16.2   | 255.255.252.0   |        |
| A10    | Guanhao    | 10.35.24.1   | 255.255.254.0   | /23    |
|        | Maingate   | 10.35.24.2   | 255.255.254.0   |        |
|        | Alabasta   | 10.35.24.3   | 255.255.254.0   |        |
| A11    | Alabasta   | 10.35.27.129 | 255.255.255.240 | /28    |
|        | Jorge      | 10.35.27.130 | 255.255.255.240 |        |
| A12    | Guanhao    | 10.35.27.161 | 255.255.255.252 | /30    |
|        | Oimo       | 10.35.27.162 | 255.255.255.252 |        |
| A13    | Oimo       | 10.35.26.1   | 255.255.255.0   | /24    |
|        | EniesLobby | 10.35.26.2   | 255.255.255.0   |        |
|        | Seastone   | 10.35.26.3   | 255.255.255.0   |        |
| A14    | Oimo       | 10.35.27.165 | 255.255.255.252 | /30    |
|        | Fukurou    | 10.35.27.166 | 255.255.255.252 |        |
| A15    | Seastone   | 10.35.20.1   | 255.255.252.0   | /22    |
|        | Elena      | 10.35.20.2   | 255.255.252.0   |        |

Lalu untuk konfigurasi tiap node seperti berikut
* Foosha
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.35.12.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.35.27.145
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.35.27.153
	netmask 255.255.255.252

auto eth4
iface eth4 inet static
	address 10.35.27.157
	netmask 255.255.255.252
```
  
* Water7
```
auto eth0
iface eth0 inet static
	address 10.35.27.146
	netmask 255.255.255.252
	gateway 10.35.27.145

auto eth1
iface eth1 inet static
	address 10.35.8.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.35.27.149
	netmask 255.255.255.252
```
  
* Pucci
```
auto eth0
iface eth0 inet static
	address 10.35.27.150
	netmask 255.255.255.252
	gateway 10.35.27.149

auto eth1
iface eth1 inet static
	address 10.35.27.1
	netmask 255.255.252.128

auto eth2
iface eth2 inet static
	address 10.35.0.1
	netmask 255.255.248.0
```
* Jipanggu
```
auto eth0
iface eth0 inet static
	address 10.35.27.2
	netmask 255.255.252.128
	gateway 10.35.27.1
```  
* Courtyard
```
auto eth0
iface eth0 inet static
	address 10.35.0.2
	netmask 255.255.248.0
	gateway 10.35.0.1
```  
* Calmbelt
```
auto eth0
iface eth0 inet static
	address 10.35.0.3
	netmask 255.255.248.0
	gateway 10.35.0.1
 ``` 
* Cipher
```
auto eth0
iface eth0 inet static
	address 10.35.8.2
	netmask 255.255.252.0
	gateway 10.35.8.1
```  
* Blueno
```
auto eth0
iface eth0 inet static
	address 10.35.12.2
	netmask 255.255.252.0
	gateway 10.35.12.1
```  
* Doriki
```
auto eth0
iface eth0 inet static
	address 10.35.27.154
	netmask 255.255.255.252
	gateway 10.35.27.153
```
* Guanhao
```
auto eth0
iface eth0 inet static
	address 10.35.27.158
	netmask 255.255.255.252
	gateway 10.35.27.157

auto eth1
iface eth1 inet static
	address 10.35.16.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.35.10.1
	netmask 255.255.254.0

auto eth3
iface eth3 inet static
	address 10.35.27.161
	netmask 255.255.255.252
```
* Jabra
```
auto eth0
iface eth0 inet static
	address 10.35.16.2
	netmask 255.255.252.0
	gateway 10.35.16.1
```
* Maingate
```
auto eth0
iface eth0 inet static
	address 10.35.24.2
	netmask 255.255.254.0
	gateway 10.35.24.1
```
* Alabasta
```
auto eth0
iface eth0 inet static
	address 10.35.24.3
	netmask 255.255.254.0
	gateway 10.35.24.1

auto eth1
iface eth1 inet static
	address 10.35.27.129
	netmask 255.255.255.240
```
* Jorge
```
auto eth0
iface eth0 inet static
	address 10.35.27.130
	netmask 255.255.255.240
	gateway 10.35.27.129
```
* Oimo
```
auto eth0
iface eth0 inet static
	address 10.35.27.162
	netmask 255.255.255.252
	gateway 10.35.27.161

auto eth1
iface eth1 inet static
	address 10.35.26.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.35.27.165
	netmask 255.255.255.252
```
* Fukurou
```
auto eth0
iface eth0 inet static
	address 10.35.27.166
	netmask 255.255.255.252
	gateway 10.35.27.165
```
* EnniesLobby
```
auto eth0
iface eth0 inet static
	address 10.35.26.2
	netmask 255.255.255.0
	gateway 10.35.26.1
```
* Seastone
```
auto eth0
iface eth0 inet static
	address 10.35.26.3
	netmask 255.255.255.0
	gateway 10.35.26.1

auto eth1
iface eth1 inet static
	address 10.35.20.1
	netmask 255.255.252.0
```
* Elena
```
auto eth0
iface eth0 inet static
	address 10.35.20.2
	netmask 255.255.252.0
	gateway 10.35.20.1
```
### Routing 
Setelah kita melakukan konfigurasi kita melakukan Routing pada tiap-tiap router seperti berikut

* Foosha
```
Subnet sebelah kiri topologi arah ke Water7
route add -net 10.35.8.0 netmask 255.255.252.0 gw 10.35.27.146
route add -net 10.35.27.0 netmask 255.255.255.128 gw 10.35.27.146
route add -net 10.35.0.0 netmask 255.255.248.0 gw 10.35.27.146
route add -net 10.35.27.148 netmask 255.255.255.252 gw 10.35.27.146

Subnet sebelah bawah topologi arah ke Guanhao
route add -net 10.35.16.0 netmask 255.255.252.0 gw 10.35.27.158
route add -net 10.35.27.128 netmask 255.255.255.240 gw 10.35.27.158
route add -net 10.35.27.164 netmask 255.255.255.252 gw 10.35.27.158
route add -net 10.35.24.0 netmask 255.255.252.0 gw 10.35.27.158
route add -net 10.35.20.0 netmask 255.255.252.0 gw 10.35.27.158
route add -net 10.35.26.0 netmask 255.255.255.0 gw 10.35.27.158
route add -net 10.35.27.160 netmask 255.255.255.252 gw 10.35.27.158
```
* Water7
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.27.145
route add -net 10.35.27.0 netmask 255.255.255.128 gw 10.35.27.150
route add -net 10.35.0.0 netmask 255.255.248.0 gw 10.35.27.150
route add -net 10.35.27.148 netmask 255.255.255.252 gw 10.35.27.150
```
* Pucci
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.27.149
```
* Guanhao
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.27.157
route add -net 10.35.26.0 netmask 255.255.255.0 gw 10.35.27.162
route add -net 10.35.20.0 netmask 255.255.252.0 gw 10.35.27.162
route add -net 10.35.27.164 netmask 255.255.255.252 gw 10.35.27.162
route add -net 10.35.27.128 netmask 255.255.255.240 gw 10.35.24.3
route add -net 10.35.27.160 netmask 255.255.255.252 gw 10.35.27.162
```
* Alabasta
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.24.1
```
* Oimo
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.27.161
route add -net 10.35.20.0 netmask 255.255.252.0 gw 10.35.26.3
```
* Seastone
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.35.26.1
```


### Testing
Disini kita melakukan 2 testing. Satu untuk antar node dan satu lagi untuk ke jaringan luar. 
* Yang pertama kita melakukan `ping` node `Elena` dari node `Jipanggu`.  Untuk melakukannya ping tersebut mengarah ke IP Elena yaitu `10.35.20.2`

![image](https://user-images.githubusercontent.com/55140514/143684279-7ff4e4be-d3a1-4cc4-a8ce-de22986c5261.png)

Bisa dilihat bahwa node Jipanggu berhasil melakukan ping ke node Elena

* Yang kedua kita lakukan `ping` ke `youtube.com` dari node `Elena` seperti berikut

![image](https://user-images.githubusercontent.com/55140514/143684375-b2212c68-f690-4caf-a3f2-4d51ef7c9eff.png)
 
Bisa dilihat bahwa node berhasil ping ke youtube.com

### Notes
* Pastikan bahwa semua node sudah terhubung dengan internet dengan perintah `echo nameserver 192.168.122.1 > /etc/resolv.conf`
* Pastikan pada testing bahwa semua node berhasil melakukan testing seperti testing sebelumnya

<hr/>
  
## CIDR (Cisco Packet Tracer)
  
### Menentukan masing-masing Subnet dari Topologi yang Sudah Ditentukan  
  
Pertama-tama menentukan inisialisai nama subnet dari Topologi yang sudah ada, lalu melakukan pengelompokan mulai dari subnet yang paling jauh dari router pusat(pengakses internet), pengelompokan hingga membentuk 1 kelompok dalam seluruh topology. urutan sebagai berikut:  
![frame1](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%201.png)
![frame2](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%202.png)
![frame3](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%203.png)
![frame4](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%204.png)
![frame5](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%205.png)
![frame6](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%206.png)
![frame8](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%208.png)
![frame10](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%2010.png)  
  
### Menghitung NID Menggunakan Pohon Faktor
  
Setelah itu menghitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon faktor lalu kita dapat melakukan subnetting sehinggan pembagian nama IP dapat diambil sesuai dengan kebutuhan masing-masing client. gambar sebagai berikut:  
![frame10](https://raw.githubusercontent.com/ALuthfiH/Jarkom-Modul-4-E12-2021/main/CIDR/Frame%209.png)  
akan didapatkan pembagian IP sebagai berikut:  
![image](https://user-images.githubusercontent.com/75328763/143684474-79b08418-1559-408f-b6fb-e74573c319f1.png)  
![image](https://user-images.githubusercontent.com/75328763/143684589-bd482295-0dee-4132-b390-eeaac2275bb9.png)  
  
### Routing CIDR pada CPT  
  
Berikut adalah setting route pada router menggnuakan CPT:  
* Foosha:  
* WATER7:  
* PUCCI:  
* GUANHAO:  
* OIMO: 
* ALABASTA:
* SEASTONE: 
  
### Kesimpulan  
Kesimpulan yang kami dapat terkait perbedaan teknik CIDR dan teknik VLSM adalah teknik CIDR lebih mudah untuk melakukan pe-routing-an karena penamaan NID sudah saling dikelompokkan pada masing masing router sehingga cukup melakukan routing pada router level bawah(child). Sedangkan teknik VLSM lebih baik dikarenakan ke efesiansi dan kehematan penggunaan NID sesuai dengan jumlah kuota nama IP yang hasanya dibutuhkan saja, sehingga tidak mengakibatkan keborosan nama IP.
  
