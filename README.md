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



<hr/>
  
## CIDR
  
  
