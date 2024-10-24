# Jarkom-Modul-2-IT29-2024

### Anggota Kelompok
| Nama | NRP |
|---------|---------|
| Harwinda | 5027231079   |
| Muhammad Syahmi Ash Shidqi | 5027231085   |

#Laporan Resmi

### Topologi
<img width="653" alt="image" src="https://github.com/user-attachments/assets/a5ac0a6a-4377-4a07-b3ce-1c6f64ba4e2b">


### Prefix
| IT29 | 10.78 |
|---------|---------|


### soal 1

Untuk mempersiapkan peperangan World War MMXXIV (Iya sebanyak itu), Sriwijaya membuat dua kotanya menjadi web server yaitu Tanjungkulai, dan Bedahulu, serta Sriwijaya sendiri akan menjadi DNS Master. Kemudian karena merasa terdesak, Majapahit memberikan bantuan dan menjadikan kerajaannya (Majapahit) menjadi DNS Slave.
### Config
#### Nusantara
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.78.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.78.2.1
	netmask 255.255.255.0
```

#### Sanjaya
```
auto eth0
iface eth0 inet static
	address 10.78.1.2
	netmask 255.255.255.0
	gateway 10.78.1.1
```

#### Sriwijaya
```
auto eth0
iface eth0 inet static
	address 10.78.1.3
	netmask 255.255.255.0
	gateway 10.78.1.1
```

#### Solok
```
auto eth0
iface eth0 inet static
	address 10.78.1.4
	netmask 255.255.255.0
	gateway 10.78.1.1
```

#### Samaratungga
```
auto eth0
iface eth0 inet static
	address 10.78.1.5
	netmask 255.255.255.0
	gateway 10.78.1.1
```

#### KenArok
```
auto eth0
iface eth0 inet static
	address 10.78.1.6
	netmask 255.255.255.0
	gateway 10.78.1.1
```

#### Majapahit
```
auto eth0
iface eth0 inet static
	address 10.78.2.2
	netmask 255.255.255.0
	gateway 10.78.2.1
```

#### Kotalingga
```
auto eth0
iface eth0 inet static
	address 10.78.2.3
	netmask 255.255.255.0
	gateway 10.78.2.1
```

#### Bedahulu
```
auto eth0
iface eth0 inet static
	address 10.78.2.4
	netmask 255.255.255.0
	gateway 10.78.2.1
```

#### Tanjungkulai
```
auto eth0
iface eth0 inet static
	address 10.78.2.5
	netmask 255.255.255.0
	gateway 10.78.2.1
```


### Inisiasi .bashrc 

#### Nusantara
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.173.0.0/16
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```
#### Sriwijaya & Majapahit
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y      
```
#### KenArok, Sanjaya & Samaratungga
```
echo -e '
nameserver 10.78.1.3 
nameserver 10.78.2.2 
nameserver 192.168.122.1
' > /etc/resolv.conf
```



### soal 2

Karena para pasukan membutuhkan koordinasi untuk melancarkan serangannya, maka buatlah sebuah domain yang mengarah ke Solok dengan alamat sudarsana.xxxx.com dengan alias www.sudarsana.xxxx.com, dimana xxxx merupakan kode kelompok. Contoh: sudarsana.it01.com.
- install bind9 lalu nano /etc/bind/named.conf.local untuk mengkonfigurasi zone sudarsana
<img width="542" alt="image" src="https://github.com/user-attachments/assets/3122219e-f90b-4e7c-a17c-52c96fc62c88">

-lalu buat direktori /etc/bind/jarkom. lalu copy file template file konfigurasi yang berasal dari cp /etc/bind/db.local
<img width="524" alt="image" src="https://github.com/user-attachments/assets/1f22cd59-d87c-4d69-910c-6fc65493d634">

- nano /etc/bind/jarkom/sudarsana.it29.com untuk mengubah konfigurasi sesuai soal
<img width="554" alt="image" src="https://github.com/user-attachments/assets/926dd51f-beb7-4278-85b7-fe2b08a85e38">

- lalu ping sudarsana.it29.com
![WhatsApp Image 2024-10-01 at 19 29 00](https://github.com/user-attachments/assets/57a31ccb-18cd-4251-92ae-c141a3644ba0)



### soal 3

Para pasukan juga perlu mengetahui mana titik yang akan diserang, sehingga dibutuhkan domain lain yaitu pasopati.xxxx.com dengan alias www.pasopati.xxxx.com yang mengarah ke Kotalingga.

- karena sudah mengkonfigurasi zone pada nomor satu, kita langsung meng-copy file yang berasal dari cp /etc/bind/db.local
<img width="538" alt="image" src="https://github.com/user-attachments/assets/505591be-adac-4694-93be-f8d4dc1907ef">

- nano /etc/bind/jarkom/pasopati.it29.com untuk mengubah konfigurasi sesuai soal
<img width="531" alt="image" src="https://github.com/user-attachments/assets/60f773ff-3fd8-47ca-a0f8-a818458a1379">

- lalu ping pasopati.it29.com
![WhatsApp Image 2024-10-01 at 20 35 04](https://github.com/user-attachments/assets/59f9388e-8945-49bb-a752-45535ec4ba21)




### soal 4

Markas pusat meminta dibuatnya domain khusus untuk menaruh informasi persenjataan dan suplai yang tersebar. Informasi dan suplai meme terbaru tersebut mengarah ke Tanjungkulai dan domain yang ingin digunakan adalah rujapala.xxxx.com dengan alias www.rujapala.xxxx.com.

- karena sudah mengkonfigurasi zone pada nomor satu, kita langsung meng-copy file yang berasal dari cp /etc/bind/db.local
<img width="538" alt="image" src="https://github.com/user-attachments/assets/2c119851-a9a0-44c2-9fb7-8af939e522e5">

- nano /etc/bind/jarkom/rujapala.it29.com untuk mengubah konfigurasi sesuai soal
<img width="538" alt="image" src="https://github.com/user-attachments/assets/05acb76d-0e6c-4af4-8366-35d96240e9ca">

- lalu ping rujapala.it29.com
![WhatsApp Image 2024-10-01 at 21 28 45](https://github.com/user-attachments/assets/09e2f75c-a463-4f80-98d9-9cd53e862db8)



### soal 5

Pastikan domain-domain tersebut dapat diakses oleh seluruh komputer (client) yang berada di Nusantara.

#### jalankan script (sriwijaya2.sh) untuk testing ping
-  ini jalankan sriwijaya2.sh di sriwijaya 
![WhatsApp Image 2024-10-01 at 21 51 41](https://github.com/user-attachments/assets/cfe5faa1-1910-4867-a329-3bb73d7ebc28)

- ini ping sudarsana di sanjaya(client)
![WhatsApp Image 2024-10-01 at 21 51 10](https://github.com/user-attachments/assets/b6e44666-8287-426c-a721-2a7db3783389)

- ini ping sudarsana di Samaratungga (client)
![WhatsApp Image 2024-10-01 at 21 54 34](https://github.com/user-attachments/assets/efff7927-8c99-4e27-9915-2f5fff8089e7)

- ini ping sudarsana di KenArok (client)
![WhatsApp Image 2024-10-01 at 21 55 41](https://github.com/user-attachments/assets/49eb9378-5d1d-47fc-b850-baf74948aecb)



#### jalankan script (sriwijaya3.sh) untuk testing ping
![WhatsApp Image 2024-10-03 at 00 56 41](https://github.com/user-attachments/assets/5e54fe26-386f-4c33-ac93-3a947a865ff6)

- ini ping pasopati di Sanjaya (client)
![WhatsApp Image 2024-10-03 at 00 57 39](https://github.com/user-attachments/assets/fe12d3af-c2f6-45a4-8896-ce1e301acf55)

- ini ping pasopati di samaratungga
![WhatsApp Image 2024-10-03 at 00 58 38](https://github.com/user-attachments/assets/a195336f-f58c-492a-a045-b17fe972fdc3)

- ini ping pasopati di KenArok
![WhatsApp Image 2024-10-03 at 00 59 33](https://github.com/user-attachments/assets/de24d8e6-c5ae-4a11-b1d5-ad3861cd2250)


#### jalankan script (sriwijaya4.sh) untuk testing ping
![WhatsApp Image 2024-10-03 at 01 24 58](https://github.com/user-attachments/assets/4184adda-5766-40c5-b358-1994afb77c3c)

- ini ping rujapala di Sanjaya (client)
![WhatsApp Image 2024-10-03 at 01 25 46](https://github.com/user-attachments/assets/bca8a6a7-bc48-4686-bcd6-713a2b0ca5e3)

- ini ping rujapala di samaratungga (client)
![WhatsApp Image 2024-10-03 at 01 27 06](https://github.com/user-attachments/assets/d0422bb2-ae69-441d-a404-3eb093fe432a)

-ini ping rujapala di kenarok (client)
![WhatsApp Image 2024-10-03 at 01 28 24](https://github.com/user-attachments/assets/de3e4540-57f6-45b8-95dd-41dd867e3652)


### soal 6

Beberapa daerah memiliki keterbatasan yang menyebabkan hanya dapat mengakses domain secara langsung melalui alamat IP domain tersebut. Karena daerah tersebut tidak diketahui secara spesifik, pastikan semua komputer (client) dapat mengakses domain pasopati.xxxx.com melalui alamat IP Kotalingga (Notes: menggunakan pointer record).

- buat nano sriwijaya5.sh yang isinya reserve dari kotalingga, lalu jalankan scriptnya
<img width="544" alt="image" src="https://github.com/user-attachments/assets/508b3490-d832-4ef6-8962-efa2d67d3897">

- lalu testing di sanjaya  (client)
![WhatsApp Image 2024-10-03 at 02 01 49](https://github.com/user-attachments/assets/39fe2422-39fd-47fe-a7bf-db7d55e434c6)

- testing juga di samaratungga (client)
![WhatsApp Image 2024-10-03 at 02 03 08](https://github.com/user-attachments/assets/74fff72e-d056-411a-987f-8a6f9b63146b)

-testing juga du kenArok (client)
![WhatsApp Image 2024-10-03 at 02 03 59](https://github.com/user-attachments/assets/411adccc-74bf-47ac-9426-ceadc3d754ee)


### soal 7

Akhir-akhir ini seringkali terjadi serangan brainrot ke DNS Server Utama, sebagai tindakan antisipasi kamu diperintahkan untuk membuat DNS Slave di Majapahit untuk semua domain yang sudah dibuat sebelumnya yang mengarah ke Sriwijaya.

- pada sriwijaya
```
nano /etc/bind/named.conf.local
```

```
notify yes;
allow-transfer { 10.78.2.2; }; # IP majapahit
also-notify { 10.78.2.2; }; # IP majapahit
```

-pada majapahit (slave)
```
echo ‘zone "sudarsana.it29.com" {
	type slave;
	masters {10.78.1.3;}; # IP sriwijaya
	file "/etc/bind/jarkom/sudarsana.it29.com";
};
zone "pasopati.it29.com" {
	type slave;
	masters {10.78.1.3;}; # IP sriwijaya
	file "/etc/bind/jarkom/pasopati.it29.com";
};
zone "rujapala.it29.com" {
	type slave;
	masters {10.78.1.3;}; # IP sriwijaya
	file "/etc/bind/jarkom/rujapala.it29.com";
};’ > /etc/bind/named.conf.local
```

- jalakan semua file sriwijaya kecuali yang reserve
- di sriwijaya `service bind9 stop` untuk ngestop running 
![WhatsApp Image 2024-10-03 at 04 30 05](https://github.com/user-attachments/assets/5ef6a33b-9bea-4033-9967-9ab69546fb41)

- lalu di majapahit nyalakan ` service bind9 start` dan ping client
![WhatsApp Image 2024-10-03 at 04 31 19](https://github.com/user-attachments/assets/04baea21-024f-4ccc-b8dd-710f6af76593)





### soal 8

Kamu juga diperintahkan untuk membuat subdomain khusus melacak kekuatan tersembunyi di Ohio dengan subdomain cakra.sudarsana.xxxx.com yang mengarah ke Bedahulu.

#### Script

```
echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     sudarsana.it29.com. root.sudarsana.it29.com. (
                        2023101001      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      sudarsana.it29.com.
@       IN      A       10.78.1.4   ; 
www     IN      CNAME   sudarsana.it29.com.
cakra  IN      A        10.78.2.4     ;' > /etc/bind/jarkom/sudarsana.it29

service bind9 restart
```

#### Output

<img src="img/cakra_k.png">
<img src="img/cakra_sama.png">
<img src="img/cakra_san.png">


### soal 9

Karena terjadi serangan DDOS oleh shikanoko nokonoko koshitantan (NUN), sehingga sistem komunikasinya terhalang. Untuk melindungi warga, kita diperlukan untuk membuat sistem peringatan dari siren man oleh Frekuensi Freak dan memasukkannya ke subdomain panah.pasopati.xxxx.com dalam folder panah dan pastikan dapat diakses secara mudah dengan menambahkan alias www.panah.pasopati.xxxx.com dan mendelegasikan subdomain tersebut ke Majapahit dengan alamat IP menuju radar di Kotalingga.

#### Script
##### sriwijaya

```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     pasopati.it29.com. root.pasopati.it29.com. (
                        2023101001      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      pasopati.it29.com.
www     IN      CNAME   pasopati.it29.com.
ns1     IN      A       10.78.2.2     ; IP Majapahit
panah   IN      NS      ns1' > /etc/bind/jarkom/pasopati.it29.com


echo "options {
    directory \"/var/cache/bind\";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders.
    // Uncomment the following block, and insert the addresses replacing
    // the all-0's placeholder.  
    // };

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    //dnssec-validation auto;

    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
};" > /etc/bind/named.conf.options

service bind9 restart
```

##### Majapahit

```
echo "
options {
        directory \"/var/cache/bind\";
        allow-query{any;};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
" > /etc/bind/named.conf.options

echo '

zone "panah.pasopati.it29.com"{
        type master;
        file "/etc/bind/panah/panah.pasopati.it29.com";
};
'>> /etc/bind/named.conf.local

mkdir /etc/bind/panah

echo "
\$TTL    604800
@       IN      SOA     panah.pasopati.it29.com. root.panah.pasopati.it29.com. (
                        2021100401      ; Serial
                        604800         ; Refresh
                        86400         ; Retry
                        2419200         ; Expire
                        604800 )       ; Negative Cache TTL
;
@               IN      NS      panah.pasopati.it29.com.
@               IN      A       10.78.2.3       ;ip kalingga
www             IN      CNAME   panah.pasopati.it29.com.
" > /etc/bind/panah/panah.pasopati.it29.com
service bind9 restart
```

#### Output
<img src="img/panah_k.png">
<img src="img/panah_sama.png">
<img src="img/panah_san.png">

### soal 10

Markas juga meminta catatan kapan saja meme brain rot akan dijatuhkan, maka buatlah subdomain baru di subdomain panah yaitu log.panah.pasopati.xxxx.com serta aliasnya www.log.panah.pasopati.xxxx.com yang juga mengarah ke Kotalingga.

#### Script
##### Majapahit

```
echo "
\$TTL    604800
@       IN      SOA     panah.pasopati.it29.com. root.panah.pasopati.it29.com. (
                        2021100401      ; Serial
                        604800         ; Refresh
                        86400         ; Retry
                        2419200         ; Expire
                        604800 )       ; Negative Cache TTL
;
@               IN      NS      panah.pasopati.it29.com.
@               IN      A       10.72.2.3       ;
www             IN      CNAME   panah.pasopati.it29.com.
log             IN      A       10.72.2.3      ; 
www.log         IN      CNAME   log.panah.pasopati.it29.com." > /etc/bind/panah/panah.pasopati.it29.com
service bind9 restart
```

#### Output
<img src="img/log_k.png">
<img src="img/log_sam.png">
<img src="img/log_san.png">

### soal 11

Setelah pertempuran mereda, warga IT dapat kembali mengakses jaringan luar dan menikmati meme brainrot terbaru, tetapi hanya warga Majapahit saja yang dapat mengakses jaringan luar secara langsung. Buatlah konfigurasi agar warga IT yang berada diluar Majapahit dapat mengakses jaringan luar melalui DNS Server Majapahit.

#### Script
##### Majapahit

```
echo 'options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders.
    // Uncomment the following block, and insert the addresses replacing
    // the all-0s placeholder.
    forwarders {
        192.168.122.1;
    };

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    //dnssec-validation auto;

    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
};' > /etc/bind/named.conf.options

service bind9 restart
```

### Testing

Masukkan nameserver IP Sriwijaya (10.78.1.3) pada salah satu client dengan `nano /etc/resolv.conf`, seharusnya bisa akses ke jaringan luar. 

#### Output

<img src="img/no11.png">

### soal 12

Karena pusat ingin sebuah laman web yang ingin digunakan untuk memantau kondisi kota lainnya maka deploy laman web ini (cek resource yg lb) pada Kotalingga menggunakan apache.

### soal 13

Karena Sriwijaya dan Majapahit memenangkan pertempuran ini dan memiliki banyak uang dari hasil penjarahan (sebanyak 35 juta, belum dipotong pajak) maka pusat meminta kita memasang load balancer untuk membagikan uangnya pada web nya, dengan Kotalingga, Bedahulu, Tanjungkulai sebagai worker dan Solok sebagai Load Balancer menggunakan apache sebagai web server nya dan load balancer nya.

### soal 14

Selama melakukan penjarahan mereka melihat bagaimana web server luar negeri, hal ini membuat mereka iri, dengki, sirik dan ingin flexing sehingga meminta agar web server dan load balancer nya diubah menjadi nginx.


### soal 15

Markas pusat meminta laporan hasil benchmark dengan menggunakan apache benchmark dari load balancer dengan 2 web server yang berbeda tersebut dan meminta secara detail dengan ketentuan:

- Nama Algoritma Load Balancer
- Report hasil testing apache benchmark 
- Grafik request per second untuk masing masing algoritma. 
- Analisis
- Meme terbaik kalian (terserah ( ͡° ͜ʖ ͡°)) 🤓


### soal 16

Karena dirasa kurang aman dari brainrot karena masih memakai IP, markas ingin akses ke Solok memakai solok.xxxx.com dengan alias www.solok.xxxx.com (sesuai web server terbaik hasil analisis kalian).

### soal 17

Agar aman, buatlah konfigurasi agar solok.xxx.com hanya dapat diakses melalui port sebesar π x 10^4 = (phi nya desimal) dan 2000 + 2000 log 10 (10) +700 - π = ?.

### soal 18

Apa bila ada yang mencoba mengakses IP solok akan secara otomatis dialihkan ke www.solok.xxxx.com.

### soal 19

Karena probset sudah kehabisan ide masuk ke salah satu worker buatkan akses direktori listing yang mengarah ke resource worker2.

### soal 20

Worker tersebut harus dapat di akses dengan sekiantterimakasih.xxxx.com dengan alias www.sekiantterimakasih.xxxx.com.


