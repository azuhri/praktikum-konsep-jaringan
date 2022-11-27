# Laporan Praktikum Konsep Jaringan

### Nama : Achmad Zahir Wajdi

### NRP : 3121600012

### Kelas : 2 D4 Teknik Informatika A

# Praktikum 10 Implementasi BGP pada Mikrotik

## 1. Topologi

![Topologi](assets/Topologi.png)

Topologi di atas terdiri dari 10 Router. R1 sebagai router utama yang akan terhubung ke AS Number yang lain. Area R2 menggunakan routing protocol RIP, area R3 menggunakan OSPF, area R4 menggunakan Static Routing, sementara untuk menghubungkan area R2, R3, dan R4 menggunakan routing protocol BGP yang terhubung ke router pusat yakni R1.

| Devices |   IP Address    | CIDR |     Network     | Interface |
| :-----: | :-------------: | :--: | :-------------: | :-------: |
|   R1    |   14.14.14.1    |  24  |   14.14.14.0    |  ether2   |
|         |   13.13.13.1    |  24  |   13.13.13.0    |  ether3   |
|         |   12.12.12.1    |  24  |   12.12.12.0    |  ether4   |
|   R2    |   12.12.12.2    |  24  |   12.12.12.0    |  ether1   |
|         |   27.27.27.2    |  24  |   27.27.27.0    |  ether2   |
|         |   28.28.28.2    |  24  |   28.28.28.0    |  ether3   |
|   R3    |   13.13.13.3    |  24  |   13.13.13.0    |  ether1   |
|         |   36.36.36.3    |  24  |   36.36.36.0    |  ether2   |
|         |   35.35.35.3    |  24  |   35.35.35.0    |  ether3   |
|   R4    |   14.14.14.4    |  24  |   14.14.14.0    |  ether1   |
|         |   41.41.41.4    |  24  |   41.41.41.0    |  ether2   |
|         |   49.49.49.4    |  24  |   49.49.49.0    |  ether3   |
|   R5    |   35.35.35.5    |  24  |   35.35.35.0    |  ether1   |
|         |   50.50.50.50   |  -   |   50.50.50.50   |    lo0    |
|   R6    |   36.36.36.6    |  24  |   36.36.36.0    |  ether1   |
|         |   60.60.60.60   |  -   |   60.60.60.60   |    lo0    |
|   R7    |   27.27.27.7    |  24  |   27.27.27.0    |  ether1   |
|         |   70.70.70.70   |  -   |   70.70.70.70   |    lo0    |
|   R8    |   28.28.28.8    |  24  |   28.28.28.0    |  ether1   |
|         |   80.80.80.80   |  -   |   80.80.80.80   |    lo0    |
|   R9    |   49.49.49.9    |  24  |   49.49.49.0    |  ether1   |
|         |   90.90.90.90   |  -   |   90.90.90.90   |    lo0    |
|   R10   |   41.41.41.10   |  24  |   41.41.41.0    |  ether1   |
|         | 100.100.100.100 |  -   | 100.100.100.100 |    lo0    |

## 2. Ruang Lingkup Kerja

Dalam pratikum kali ini kelompok kami terdiri dari Azis Zuhri Pratomo (3121600002), Achmad Zahir Wajdi (3121600012), dan Fazaa Hanifan Hidayatullah (3121600015) bertugas untuk mengatur router R2 yng menggunakan routing protocol RIP dan BGP AS1234 sesuai area yang telah ditentukan. Kami melakukan konfigurasi routing RIP dengan perintah sebagai berikut:

    /ip address
    add address=12.12.12.2/24 interface=ether1 network=12.12.12.0
    add address=27.27.27.2/24 interface=ether2 network=27.27.27.0
    add address=28.28.28.2/24 interface=ether3 network=28.28.28.0
    /routing rip
    set redistribute-bgp=yes redistribute-connected=yes
    /routing rip network
    add network=27.27.27.0/24
    add network=28.28.28.0/24

untuk konfigurasi routing BGP AS1234 dengan perintah sebagai berikut:

    /routing filter
    add chain=bgp-scope-in set-scope=30 set-target-scope=40
    /routing bgp instance
    set default disabled=yes
    add as=1234 name=lab-bgp redistribute-connected=yes redistribute-rip=yes \
        router-id=2.2.2.2
    /routing bgp network
    add network=12.12.12.0/24
    /routing bgp peer
    add in-filter=bgp-scope-in instance=lab-bgp name=peer1 remote-address=\
        12.12.12.1 remote-as=1234

## 3. Table Routing

![TableRouting](assets/tabel-routing.jpeg)

Terlihat dengan perintah ip route print untuk melihat isi tabel routing,
bahwa router R2 sudah terhubung dengan router R7 dan R8 yang menggunakan routing protocol RIP. Selain itu, router R2 juga terhubung dengan router R1, R3, dan R4 melalui protocol BGP AS1234. Router R2 dapat menerimah tabel routing dari setiap router karena sudah terhunung dengan R1.

## 3. Table Routing

Test Ping R10

![Ping R10](assets/ping%2041.41.41.10.jpeg)

Test Ping R1

![Ping R1](assets/ping%2014.14.14.4.jpeg)

Tracert R10

![Tracert R10](assets/tracert%2041.41.41.10.jpeg)

Tracert R1

![Tracert R1](assets/tracert%2014.14.14.4.jpeg)

Gambar-gambar diatas merupakan test koneksi dengan perintah ping ke IP Address yang telah ditentukan.

- Berhasil melakukan ping ke IP Address pada router R1 (14.14.14.4), dan R10 (41.41.41.10) karena 2 router tersebut sudah masuk dalam tabel routing.
- Untuk Router selain dua router diatas belum dapat kami test karena adanya kendala pada device yang sulit untuk terhubung kedalam app winbox.
