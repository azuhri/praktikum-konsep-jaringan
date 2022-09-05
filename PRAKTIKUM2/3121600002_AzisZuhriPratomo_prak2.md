## CATATAN PRAKTIKUM MENGGUNAKAN WIRESHARK

Wireshark adalah tool network analyzer yang dapat penganalisis paket bebas dan sumber terbuka. Perangkat ini digunakan untuk pemecahan masalah jaringan, analisis, perangkat lunak dan pengembangan protokol komunikasi, dan pendidikan. Awalnya bernama Ethereal, pada Mei 2006 proyek ini berganti nama menjadi Wireshark karena masalah merek dagang

### PENGERTIAN COLOR RULES PADA WIRESHARK
Label warna pada wireshark berguna untuk mengidentifikasi jenis protokol jaringan apa yang ter-capture secara sekilas. Berikut adalah default color rules pada wireshark
<br>
<br>
<img src="../assets/prak2-ss1.png">
<br>
Secara default, label warna hitam menandakan paket TCP yang yang bermasalah seperti lost packet , label warna hijau menandakan lalu lintas TCP, label warna biru muda menandakan lalu lintas UDP
<br>
<table width="100%" border="2" cellpadding="0" style="border-collapse: collapse;">
   <tr style="border: 2px solid black"> 
        <td style="text-align: center; font-weight:bold ">
            LABEL WARNA
        </td>
        <td style="text-align: center; font-weight:bold ">
            TIPE PAKET
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Light Purple	
        </td>
        <td style="text-align: center">
            TCP 
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Light Blue	
        </td>
        <td style="text-align: center">
            UDP
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Black
        </td>
        <td style="text-align: center">
            Packets with errors
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Light Green	
        </td>
        <td style="text-align: center">
            HTTP Traffic
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Light Yellow	
        </td>
        <td style="text-align: center">
            Windows-specific traffic, including Server Message Blocks (SMB) and NetBIOS
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Dark Yellow	
        </td>
        <td style="text-align: center">
            Routing
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Dark Gray
        </td>
        <td style="text-align: center">
            TCP SYN, FIN and ACK traffic
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Red
        </td>
        <td style="text-align: center">
            Invalid Display Filter
        </td>
   </tr>
   <tr style="border: 2px solid black"> 
        <td style="text-align: center">
            Black Color	
        </td>
        <td style="text-align: center">
        </td>
   </tr>
</table>

## MENCOBA METRACKING JALUR ICMP (PACKET ANALYZER)

### - MENGECHECK IP ADDRESS LAPTOP 
<img src="../assets/prak2-ss-2.png">

### - MENGECHECK DEFAULT GATEWAY 
<img src="../assets/prak2-ss-3.png">

### - MELAKUKAN PING KE DEFAULT GATEWAY
<img src="../assets/prak2-ss-4.png">

### - MELIHAT LALU LINTAS JARINGAN PADA WIRESHART DAN MELAKUKAN FILTER UNTUK PROTOKOL ICMP SAJA
<img src="../assets/prak2-ss-5.png">
<br>
<br>
Note: Disini kita melakukan ping ke default gateway sebanyak 5 kali, dan terekam di wireshark. disini terdapat proses ping request yang dilakukan oleh komputer saya (10.252.128.2) lalu dibalas oleh default gateway (ping reply).

