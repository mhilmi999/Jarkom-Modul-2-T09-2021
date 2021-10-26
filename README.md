# Jarkom-Modul-2-T09-2021

Nama Anggota | NRP
------------------- | --------------		
Natasya Abygail N | 05111940000020
Muhammad Hilmi Ramadhan | 05311940000044
Sri Puspita Dewi | 05111940000045

## List of Contents :
- [Soal 1](#soal-1)
	- [Jawaban](#jawaban-soal-1)
- [Soal 2](#soal-2)
	- [Jawaban](#jawaban-soal-2)
- [Soal 3](#soal-3)
	- [Jawaban](#jawaban-soal-3)
- [Soal 4](#soal-4)
	- [Jawaban](#jawaban-soal-4)
- [Soal 5](#soal-5)
	- [Jawaban](#jawaban-soal-5)
- [Soal 6](#soal-6)
	- [Jawaban](#jawaban-soal-6)
- [Soal 7](#soal-7)
	- [Jawaban](#jawaban-soal-7)
- [Soal 8](#soal-8)
	- [Jawaban](#jawaban-soal-8)
- [Soal 9](#soal-9)
	- [Jawaban](#jawaban-soal-9)
- [Soal 10](#soal-10)
	- [Jawaban](#jawaban-soal-10)
- [Soal 11](#soal-11)
	- [Jawaban](#jawaban-soal-11)
- [Soal 12](#soal-12)
	- [Jawaban](#jawaban-soal-12)
- [Soal 13](#soal-13)
	- [Jawaban](#jawaban-soal-13)
- [Soal 14](#soal-14)
	- [Jawaban](#jawaban-soal-14)
- [Soal 15](#soal-15)
	- [Jawaban](#jawaban-soal-15)
- [Soal 15](#soal-16)
	- [Jawaban](#jawaban-soal-16)
- [Soal 17](#soal-17)
	- [Jawaban](#jawaban-soal-17)

## Notes: Prefix IP: 10.46
---

## Soal 1 :
---
Buatlah topologi jaringan dengan detil berikut: `EniesLobby` akan dijadikan sebagai `DNS Master`, `Water7` akan dijadikan `DNS Slave`, dan `Skypie` akan digunakan sebagai `Web Server`. Terdapat 2 `Client` yaitu `Loguetown`, dan `Alabasta`. `Semua node terhubung` pada router `Foosha`, sehingga dapat mengakses internet
## Jawaban Soal 1 : 
---
Pertama-tama kami membuat sebuah node yang terhubung dengan internet dengan nama NAT1. Node tersebut kemudian disambungkan dengan router foosha melalui interface `nat0` menuju interface `eth0`. Selanjutnya konfigurasi IP router foosha seperti gambar berikut:

![Foto](./img/no1/fooshaconfig.jpg)
<br>

Selanjutnya lengkapi pembuatan topologi dengan menambahkan` node ethernet switch` dan `ubuntu` **(EniesLobby, Water7, Skypie, Loguetown, dan Alabasta)** seperti gambar berikut:

![Foto](./img/no1/topologiview.jpg)
<br>

Kemudian setting network dari masing-masing node ubuntu dengan fitur Edit network configuration seperti berikut:
- Louguetown (Client)
![Foto](./img/no1/loguetownconfig.jpg)
<br>

- Alabasta (Client)
![Foto](./img/no1/alabastaconfig.jpg)
<br>

- EniesLobby (DNS Master)
![Foto](./img/no1/enieslobbyconfig.jpg)
<br>

- Water7 (DNS Slave)
![Foto](./img/no1/water7config.jpg)
<br>

- Skypie (Web Server)
![Foto](./img/no1/skypieconfig.jpg)
<br>

Lalu `restart` semua node dan ketikan pada router foosha `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.46.0.0/16` .
Kemudian agar setiap node terhubung ke router Foosha **(EniesLobby, Water7, Loguetown, dan Alabasta)**, maka diperlukan untuk `echo 'nameserver 192.168.122.1' > /etc/resolv.conf` yang diletakkan pada `/root/script.sh` . Berikut merupakan salah satu contoh pada `EniesLobby`:

- EniesLobby (DNS Master)
![Foto](./img/no1/enieslobbyconnectfoosha.jpg)
<br>

---