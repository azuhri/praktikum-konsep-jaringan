## PRAKTIKUM ROUTING STATIC
Pada praktikum kali kita akan melakukan routing static yang menghubungkan antara 2 network

Dan topologynya sebagai berikut :
<br>
<br>
<img src="../assets/prak4-1.png">
<br>
<br>

Keterangan ip address:

- PC 1 : 192.168.1.2
- PC 2 : 192.168.3.3
- ROUTER-1:
  - Gig0/0/0 : 192.168.1.1
  - Gig0/0/1 : 192.168.2.1
- ROUTER-1:
  - Gig0/0/0 : 192.168.2.2
  - Gig0/0/1 : 192.168.3.2

Langkah - Langkah : 
## 1. Konfigurasi IP Address PC 1 
<img src="../assets/prak4-2.png">

## 2. Konfigurasi IP Address PC 2
<img src="../assets/prak4-3.png">

## 3. Konfigurasi IP di Router-1 pada interface Gig0/0/0 dan jangan lupa untuk nyalankan (on) interfacenya
<img src="../assets/prak4-4.png">

## 4. Konfigurasi IP di Router-1 pada interface Gig0/0/1 dan jangan lupa untuk nyalankan (on) interfacenya
<img src="../assets/prak4-5.png">

## 5. Konfigurasi IP di Router-2 pada interface Gig0/0/0 dan jangan lupa untuk nyalankan (on) interfacenya
<img src="../assets/prak4-6.png">

## 6. Konfigurasi IP di Router-2 pada interface Gig0/0/1 dan jangan lupa untuk nyalankan (on) interfacenya
<img src="../assets/prak4-7.png">

## 7. Lakukan routing static pada Router-1
<img src="../assets/prak4-8.png">

## 8. Lakukan routing static pada Router-2
<img src="../assets/prak4-9.png">

## 9. Melihat table routing di Router-1
<img src="../assets/prak4-10.png">
</br>
</br>
Terlihat bahwa Router 1 telah mendapatkan informasi table dari rute ke jaringan 192.168.3.0/24
</br>
</br>

## 10. Melihat table routing di Router-2
<img src="../assets/prak4-11.png">
</br>
</br>
Terlihat bahwa Router 2 telah mendapatkan informasi table dari rute ke jaringan 192.168.1.0/24
</br>
</br>

## 11. Melihat table routing di PC-1
<img src="../assets/prak4-12.png">
Terlihat bahwa network destination dari PC-1 adalah 0.0.0.0 yang artinya semua paket di teruskan ke network any melalui (gateway) 192.168.1.1

## 12. Melihat table routing di PC-2
<img src="../assets/prak4-13.png">
Terlihat bahwa network destination dari PC-2 adalah 0.0.0.0 yang artinya semua paket di teruskan ke network any melalui (gateway) 192.168.3.2

## 13. Melakukan test ping dari PC-1 ke PC-2
<img src="../assets/prak4-14.png">
Terlihat bahwa saat pertama kali PC-1 nge ping PC-1 terjadi 2x request timeout, ini dikarenakan terjadinya 2x broadcast untuk mendapatkan mac address yang pertama dari PC-1 ke Router-1 dan dari Router-1 ke Router-2
<br>
<br>

## 14. Melakukan test ping dari PC-2 ke PC-1
<img src="../assets/prak4-15.png">
<br>
<br>
Terlihat juga pada saat PC-2 melakukan ping sudah tidak terjadi request timeout lagi karena keduanya telah melakukan koneksi sebelumnya





