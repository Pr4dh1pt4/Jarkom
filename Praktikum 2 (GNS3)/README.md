[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1niUih_B)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Pradhipta Raja Mahendra | 5025241055 | B |



## Put your topology config image here!

<img width="1896" height="906" alt="Screenshot 2025-10-03 210515" src="https://github.com/user-attachments/assets/5e1a1618-19d8-4d30-9054-791ea9ad5805" />

## Put your GNS3 Project file here!

https://drive.google.com/file/d/1la01nE4THumq4-a0MoN86VFInQa_WCSS/view?usp=sharing

<br>

## Soal 1

> Dokumentasikan hasil pengelompokan subnet yang telah dibuat.

> _Document the results of the subnet grouping that has been created._

**Answer:**

- Screenshot


  <img width="1896" height="906" alt="Desain tanpa judul" src="https://github.com/user-attachments/assets/bf303e02-e3b5-482e-b139-c987fd85d4ec" />


- Explanation

  - Subnet 3 dihubungkan oleh Router BlackPanther eth1 dan berisi switch 1 yang menghubungkan CaptainAmerica dan Falcon.
  - Subnet 4 dihubungkan oleh BlackPanther eth2 dan berisi switch 2 yang menghubungkan WinterSoldier dan Hawkeye.
  - Subnet 5 dihubungkan oleh Router BlackWidow eth2 dan berisi switch 3 yang menghubungkan Thor dan ScarletWitch.
  - Subnet 6 dihubungkan oleh Router BlackWidow eth1 dan berisi switch 4 yang menghubungkan Hulk.
  - Subnet 7 dihubungkan oleh Router Vision sebagai gateway subnet dan berisi switch 5 yang menghubungkan SpiderMan dan DoctorStrange.

<br>

## Soal 2

> Lakukan konfigurasi routing agar setiap node dapat saling berkomunikasi. Pastikan setiap router dapat mengirimkan paket ke jaringan lain melalui tabel routing yang sesuai. Sertakan bukti bahwa Falcon bisa melakukan ping ke SpiderMan, DoctorStrange, dan ScarletWitch.

> _Configure routing so that each node can communicate with each other. Ensure each router can forward packets to other networks through the appropriate routing table. Include proof that Falcon can ping SpiderMan, Doctor Strange, and ScarletWitch._

**Answer:**

- Screenshot

  <img width="824" height="561" alt="Screenshot 2025-10-03 005038" src="https://github.com/user-attachments/assets/1d374f31-62ca-4368-b518-32df3eb9421b" />

- Explanation

    Pertama kita harus pastikan setiap router sudah memiliki static route ke router utama. Setiap router perlu dikonfigurasi routing agar paket dari satu subnet bisa mencapai subnet lain. Untuk itu digunakan static route dengan perintah ip route add 'SUBNET TUJUAN'/'NETMASK' via 'GATEWAY'
  - Falcon berhasil ping ke SpiderMan (ip 10.103.7.3)
  - Falcon berhasil ping ke Doctor Strange (ip 10.103.7.2)
  - Falcon berhasil ping ke Scarlett Witch (ip 10.103.5.3)

<br>

## Soal 3

> Lakukan konfigurasi agar semua node dapat terhubung ke internet. Sertakan hasil uji coba dengan melakukan ping ke google.com dari node Falcon, CaptainAmerica, SpiderMan, dan Thor.

> _Configure all nodes to connect to the internet. Include test results by pinging google.com from the Falcon, CaptainAmerica, SpiderMan, and Thor nodes._

**Answer:**

- Screenshot

  - Falcon
    <br>
    <br>
    <img width="828" height="558" alt="Screenshot 2025-10-03 005300" src="https://github.com/user-attachments/assets/736d270d-aee4-446a-a9ca-8a5b785dae5d" />
    <br>
    
  - CaptainAmerica
    <br>
    <br>
    <img width="822" height="561" alt="Screenshot 2025-10-03 005330" src="https://github.com/user-attachments/assets/9836360a-9cf3-4040-aa6c-cb0fd01b1868" />
    <br>
    
  - SpiderMan
    <br>
    <br>
    <img width="824" height="555" alt="Screenshot 2025-10-03 005403" src="https://github.com/user-attachments/assets/6692cb98-091e-4d0f-a023-3192d46758dd" />
    <br>
    
  - Thor
    <br>
    <br>
    <img width="820" height="560" alt="Screenshot 2025-10-03 005436" src="https://github.com/user-attachments/assets/3ae4dfa8-ec40-489a-adf0-bd7a3ae9ed98" />

- Explanation

  Setelah berhasil ping antar node di nomor 2, kita perlu untuk bisa mengeping google.com dengan install tool iptables terlebih dahulu
  ```
  apt update
  apt install iptables
  ```
  Setelah itu, kita perlu untuk menambah `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s [Prefix IP].0.0/16` di dalam config setiap router agar semua node di jaringan bisa mengakses internet melalui router. Lalu tambahkan `'echo nameserver 192.168.122.1 > /etc/resolv.conf'` di config setiap client / node untuk mengatur DNS resolver agar sistem bisa melakukan resolusi nama domain.
  - Falcon berhasil ping ke google.com dengan merubah configure dari node falcon 
  - CaptainAmerica berhasil ping ke google.com dengan merubah configure dari node CaptainAmerica
  - SpiderMan berhasil ping ke google.com dengan merubah configure dari node SpiderMan
  - Thor berhasil ping ke google.com dengan merubah configure dari node SpiderMan 

<br>

## Soal 4

> Berikan Falcon alamat IP dalam rentang [Prefix IP].3.20 - [Prefix IP].3.25
> <br> </br>
> Berikan Hawkeye alamat IP dalam rentang [Prefix IP].4.30 - [Prefix IP].4.35
> <br> </br>
> Berikan Hulk alamat IP dalam rentang [Prefix IP].6.50 - [Prefix IP].6.55

<br>

> _Give Falcon an IP address in the range [IP Prefix].3.20 - [IP Prefix].4.35_
> <br> </br>
> _Give Hawkeye an IP address in the range [IP Prefix].4.30 - [IP Prefix].4.35_
> <br> </br>
> _Give Hulk an IP address in the range [IP Prefix].6.50 - [IP Prefix].6.55_

**Answer:**

- Screenshot

  - IP address Falcon
    <br>
    <br>
    <img width="651" height="158" alt="Screenshot 2025-10-03 142437" src="https://github.com/user-attachments/assets/0d68ba19-859b-41bb-84c0-24b43030cfeb" />

  - IP address Hawkeye
    <br>
    <br>
    <img width="654" height="153" alt="Screenshot 2025-10-03 142456" src="https://github.com/user-attachments/assets/93849f66-56a4-4953-a18d-8f6d60acbc1a" />

  - IP address Hulk
    <br>
    <br>
    <img width="653" height="153" alt="Screenshot 2025-10-03 142524" src="https://github.com/user-attachments/assets/6125c792-170d-4265-89f4-5a5cb633204c" />


- Explanation

  Install ISC-DHCPD-Server menggunakan command apt-get install isc-dhcp-server pada node server yaitu CaptainAmerica. Setelah itu buka config menggunakan command nano /etc/dhcp/dhcpd.conf dan tambah config seperti di screenshot.
  - Falcon antara IP 10.103.3.20 - 10.103.3.25
  - Hawkeye antara IP 10.103.4.30 - 10.103.4.35
  - Hulk antara IP 10.103.6.50 - 10.103.6.55
 
  Penjelasan tentang config :
  - `Range` berisi rentang IP Address yang akan didistribusikan dan digunakan secara dinamis
  - `option routers` berisi IP gateway dari router menuju client sesuai konfigurasi subnet
  - `option broadcast-address` berisi IP broadcast pada subnet
  - `option domain-name-servers` berisi DNS yang ingin diberikan pada client
  - `Lease time` berisi Waktu yang dialokasikan ketika sebuah IP dipinjamkan kepada komputer client.
  - `default-lease-time` Lama waktu DHCP server meminjamkan IP Address kepada client, dalam satuan detik. Default 600 detik
  - `max-lease-time` Waktu maksimal yang di alokasikan untuk peminjaman IP oleh DHCP server ke client dalam satuan detik. Default 7200 detik

<br>

## Soal 5

> Berikan ScarletWitch dan Thor alamat IP dalam rentang [Prefix IP].5.40 - [Prefix IP].5.45 dan [Prefix IP].5.100 - [Prefix IP].5.105

> _Give ScarletWitch and Thor IP addresses in the range [IP Prefix].5.40 - [IP Prefix].5.45 and [IP Prefix].5.100 - [IP Prefix].5.105_

**Answer:**

- Screenshot

  <img width="653" height="170" alt="Screenshot 2025-10-03 142904" src="https://github.com/user-attachments/assets/f26c4944-ad98-4e29-802c-2ed8277b52c6" />

- Explanation

  Buka config seperti nomor 4 menggunakan command /etc/dhcp/dhcpd.conf dan tambah config Scarlet Witch antara IP dalam range 10.103.5.40 - 10.103.5.45 dan Thor antara IP dalam range 10.103.5.100 - 10.103.5.105 seperti di screenshot.

  Penjelasan tentang config :
  - `Range` berisi rentang IP Address yang akan didistribusikan dan digunakan secara dinamis
  - `option routers` berisi IP gateway dari router menuju client sesuai konfigurasi subnet
  - `option broadcast-address` berisi IP broadcast pada subnet
  - `option domain-name-servers` berisi DNS yang ingin diberikan pada client
  - `Lease time` berisi Waktu yang dialokasikan ketika sebuah IP dipinjamkan kepada komputer client.
  - `default-lease-time` Lama waktu DHCP server meminjamkan IP Address kepada client, dalam satuan detik. Default 600 detik
  - `max-lease-time` Waktu maksimal yang di alokasikan untuk peminjaman IP oleh DHCP server ke client dalam satuan detik. Default 7200 detik

<br>

## Soal 6

> Berikan SpiderMan dan DoctorStrange alamat IP dalam rentang [Prefix IP].7.60 - [Prefix IP].7.65  dan [Prefix IP].7.110 - [Prefix IP].7.115

> _Give SpiderMan and DoctorStrange IP addresses in the ranges [IP Prefix].7.60 - [IP Prefix].7.65 and [IP Prefix].7.110 - [IP Prefix].7.115_

**Answer:**

- Screenshot

  <img width="650" height="162" alt="Screenshot 2025-10-03 143100" src="https://github.com/user-attachments/assets/d6bd2006-fdbd-4407-9f3c-54f3f2a1a5f6" />

- Explanation

  Buka config seperti nomor 5 menggunakan command /etc/dhcp/dhcpd.conf dan tambah config SpiderMan dengan IP dalam range 10.103.7.60 - 10.103.7.65 dan Doctor Strange dengan IP dalam range 10.103.7.110 - 10.103.5.115 seperti di screenshot.

  Penjelasan tentang config :
  - `Range` berisi rentang IP Address yang akan didistribusikan dan digunakan secara dinamis
  - `option routers` berisi IP gateway dari router menuju client sesuai konfigurasi subnet
  - `option broadcast-address` berisi IP broadcast pada subnet
  - `option domain-name-servers` berisi DNS yang ingin diberikan pada client
  - `Lease time` berisi Waktu yang dialokasikan ketika sebuah IP dipinjamkan kepada komputer client.
  - `default-lease-time` Lama waktu DHCP server meminjamkan IP Address kepada client, dalam satuan detik. Default 600 detik
  - `max-lease-time` Waktu maksimal yang di alokasikan untuk peminjaman IP oleh DHCP server ke client dalam satuan detik. Default 7200 detik

<br>

## Soal 7

> Tetapkan waktu peminjaman alamat IP pada DHCP server untuk client yang terhubung melalui Switch 2 selama 5 menit (Default), dan untuk client melalui Switch 5 selama 10 menit (Default). Tetapkan juga batas waktu peminjaman maksimal selama 2 jam.
> <br> </br>
> Tetapkan waktu peminjaman alamat IP pada DHCP server untuk client yang terhubung melalui Switch 1 dan Switch 3 selama 2 menit (Default). Tetapkan juga batas waktu peminjaman maksimal selama 100 menit.

<br>

> _Set the IP address lease period on the DHCP server for clients connected through Switch 2 to 5 minutes (default), and for clients connected through Switch 5 to 10 minutes (default). Also, set the maximum lease period to 2 hours._
> <br> </br>
> _Set the IP address lease time on the DHCP server for clients connected via Switch 1 and Switch 3 to 2 minutes (default). Also set the maximum lease time limit to 100 minutes._

**Answer:**

- Screenshot

  - Switch 1
    <br>
    <br>
    <img width="651" height="158" alt="Screenshot 2025-10-03 142437" src="https://github.com/user-attachments/assets/71d3e781-18a0-4b89-b502-b25030451b03" />
    <br>
    <br>
    Test lease time
    <br>
    <br>
    <img width="825" height="564" alt="Screenshot 2025-10-03 111823" src="https://github.com/user-attachments/assets/d0833d18-3851-4954-9eb1-d83b314c6642" />

  - Switch 2
    <br>
    <br>
    <img width="800" height="163" alt="Screenshot 2025-10-03 115032" src="https://github.com/user-attachments/assets/73dbe23f-1b5d-46c2-8c92-b545f2c365e3" />
    <br>
    <br>
    Test lease time
    <br>
    <br>
    <img width="822" height="557" alt="Screenshot 2025-10-03 112033" src="https://github.com/user-attachments/assets/d5a00b85-713b-478a-a5f3-4caf98051f00" />

  - Switch 3
    <br>
    <br>
    <img width="653" height="170" alt="Screenshot 2025-10-03 142904" src="https://github.com/user-attachments/assets/b52a7b19-daa9-4309-8a63-a9f553fd0357" />
    <br>
    <br>
    Test lease time
    <br>
    <br>
    <img width="831" height="573" alt="Screenshot 2025-10-03 112257" src="https://github.com/user-attachments/assets/6f413e12-8d38-4796-accf-a51248f322e8" />

  - Switch 5
    <br>
    <br>
    <img width="650" height="162" alt="Screenshot 2025-10-03 143100" src="https://github.com/user-attachments/assets/a5e2e6e0-20de-49d1-bd89-8308d6e99623" />
    <br>
    <br>
    Test lease time
    <br>
    <br>
    <img width="830" height="563" alt="Screenshot 2025-10-03 112435" src="https://github.com/user-attachments/assets/57cf7e1b-5282-42f4-af56-0e490a86fa14" />


- Explanation

  Test lease time menggunakan command udhcpc -i eth0.
  - Switch 1 melakukan pengetesan menggunakan client Falcon dengan lease-time 2 menit atau 120 detik. Pada pengecekan lease time sudah muncul 120 detik sesuai yang ada di config.
  - Switch 2 melakukan pengetesan menggunakan client Hawkeye dengan lease-time 5 menit atau 300 detik. Pada pengecekan lease time sudah muncul 300 detik sesuai yang ada di config.
  - Switch 3 melakukan pengetesan menggunakan client Thor dengan lease-time 2 menit atau 120 detik. Pada pengecekan lease time sudah muncul 120 detik sesuai yang ada di config.
  - Switch 5 melakukan pengetesan menggunakan client SpiderMan dengan lease-time 10 menit atau 600 detik. Pada pengecekan lease time sudah muncul 600 detik sesuai yang ada di config.

<br>

## Soal 8

> Ubah konfigurasi DHCP Server agar Hawkeye, Thor, dan SpiderMan mendapatkan IP statis dengan [Prefix IP].x.5, namun masih menggunakan DHCP.

> _Change the DHCP Server configuration so that Hawkeye, Thor, and SpiderMan get static IPs with [Prefix IP].x.5, but still use DHCP._

**Answer:**

- Screenshot

  - Hawkeye
    <br>
    <br>
    <img width="832" height="567" alt="Screenshot 2025-10-03 105953" src="https://github.com/user-attachments/assets/97378ff3-8875-4e44-bff3-77a004386081" />

  - Thor
    <br>
    <br>
    <img width="828" height="555" alt="Screenshot 2025-10-03 105753" src="https://github.com/user-attachments/assets/a414fa7b-b09d-4c5a-836b-10c675f83a88" />

  - SpiderMan
    <br>
    <br>
    <img width="837" height="569" alt="Screenshot 2025-10-03 105817" src="https://github.com/user-attachments/assets/17e0af3c-942d-47cf-80a5-0acb1544815c" />


- Explanation

  Cek hardware ethernet dengan command ip a pada setiap node Hawkeye, Thor, dan SpiderMan. Setelah mengetahui hardware ethernet dari setiap client tambahkan config di dalam server CaptainAmerica dengan fixed-address sesuai dengan subnet dan juga ketentuan yang ada di soal yaitu '10.103.subnet.5'

  <img width="654" height="257" alt="Screenshot 2025-10-03 165222" src="https://github.com/user-attachments/assets/d2ee6897-e0c0-42b4-8168-15e1963fd9d4" />

  Penjelasan:

  - host <Nama> berisi nama node yang ingin dijadikan fixed address.

  - hardware ethernet diisi dengan MAC address dari interface node tersebut dengan cara seperti yg ada di penjelasan saya di atas.

  - fixed-address berisi alamat IP statis yang diberikan DHCP server. Pada soal ini, setiap node diminta dapat IP[Prefix IP].x.5 (x diisi sesuai subnet untuk tiap node).

<br>

## Soal 9

> Buatlah konfigurasi DHCP Failover dengan WinterSoldier sebagai DHCP server backup untuk CaptainAmerica.

> _Create a DHCP Failover configuration with WinterSoldier as the backup DHCP server for CaptainAmerica._

**Answer:**

- Screenshot

  - Start Server WinterSoldier
    <br>
    <br> 
    <img width="825" height="549" alt="Screenshot 2025-10-03 105339" src="https://github.com/user-attachments/assets/3a59fb79-82bd-41f8-aa8d-a3b18803bc18" />
    <br>
    <br>
  - Stop Server utama CaptainAmerica
    <br>
    <br>
    <img width="833" height="568" alt="Screenshot 2025-10-03 105410" src="https://github.com/user-attachments/assets/88342462-e925-41e0-adac-c421b6201937" />
    <br>
    <br>
  - Cek Server yang meminjamkan IP ke client
    <br>
    <br>
    <img width="859" height="592" alt="Screenshot 2025-10-03 105227" src="https://github.com/user-attachments/assets/260e90a0-0108-401c-b2c6-ed7975039a28" />


- Explanation

  Untuk mengecek apakah server dari WinterSoldier bisa menjadi backup dari server CaptainAmerica yang pertama harus config terlebih dulu menggunakan /etc/dhcp/dhcpd.conf pada kedua server. Set CaptainAmerica sebagai primary server dan WinterSoldier sebagai secondary.

  Config CaptainAmerica :
  ```
  failover peer "dhcp-failover" {
      primary;
      address 10.103.3.2;
      peer address 10.103.4.2;
      max-response-delay 60;
      max-unacked-updates 10;
      mclt 3600;
      split 255;
      load balance max seconds 0;
  }
  ```

  Config WinterSoldier :
  ```
  failover peer "dhcp-failover" {
     secondary;
     address 10.103.4.2;
     peer address 10.103.3.2;
     max-response-delay 60;
     max-unacked-updates 10;
     load balance max seconds 0;
  }
  ```

  Tambahkan pool dalam setiap subnet :
  ```
  pool {
        failover peer "dhcp-failover";
        range 'IP AWAL' 'IP AKHIR';
  }
  ```


  Setelah itu menyalakan terlebih dahulu kedua server yang telah diconfig. Setelah server WinterSoldier sudah nyala, lalu matikan server CaptainAmerica. Setelah itu, coba jalankan command udhcpc -i eth0 dan cek server mana yang memberikan IP address ke client tersebut. Pada screenshot di atas server yang meminjamkan IP adalah 10.103.4.2 atauu IP dari WinterSoldier, artinya WinterSoldier sudah berhasil untuk membackup server utama yaitu CaptainAmerica

<br>

## Soal 10

> Buatlah konfigurasi agar CaptainAmerica dan WinterSoldier berjalan dengan mode Load Balancing.

> _Create a configuration so that CaptainAmerica and WinterSoldier run in Load Balancing mode._

**Answer:**

- Screenshot

  - Ubah Config loadbalancing di server CaptainAmerica
    <br>
    <br>
    <img width="671" height="318" alt="Screenshot 2025-10-03 184030" src="https://github.com/user-attachments/assets/48168d04-c4bf-457e-8b33-1eb394d03e62" />

  - Samakan Config loadbalancing di server WinterSoldier dengan  CaptainAmerica
    <br>
    <br>
    <img width="673" height="279" alt="Screenshot 2025-10-03 183958" src="https://github.com/user-attachments/assets/cf66e4e1-4bf7-4c6d-a50a-e54c7aff953a" />

  - Test menggunakan command udhcpc -i eth0
    <br>
    <br>
    <img width="832" height="557" alt="Screenshot 2025-10-03 110700" src="https://github.com/user-attachments/assets/14de55a3-2918-4e92-924e-19f0e88a7e20" />
    <br>
    <br>
    <img width="832" height="559" alt="Screenshot 2025-10-03 110713" src="https://github.com/user-attachments/assets/40c259d7-d036-43d4-a763-c22222127e70" />

    
- Explanation

  Parameter load balance max seconds menentukan berapa lama server akan menunda sebelum merespons permintaan DHCPDISCOVER, agar memberi kesempatan server lainnya ikut merespons. Ketika sebuah client broadcast DHCPDISCOVER server primary dan secondary dua-duanya mendengar. Untuk mencegah bentrokan, maka server akan menunggu max 3 detik untuk memastikan pasangan / server lain tidak memberi jawaban lebih dulu. Dapat dilihat dari hasil screenshot tersebut, pengetesan dilakukan di dua client berbeda dan server yang meminjamkan IP berbeda antara satu client dengan client lainnya.

<br>
  
## Problems

## Revisions (if any)
