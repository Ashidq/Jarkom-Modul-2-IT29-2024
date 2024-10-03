# Jarkom-Modul-2-IT29-2024

### Anggota Kelompok
| Nama | NRP |
|---------|---------|
| Harwinda | 5027221079   |
| Muhammad Syahmi Ash Shidqi | 5027211085   |

#Laporan Resmi

- [Konfigurasi](#topologi)
- [Nomor 1](#soal-1)
- [Nomor 2](#soal-2)
- [Nomor 3](#soal-3)
- [Nomor 4](#soal-4)
- [Nomor 5](#soal-5)
- [Nomor 6](#soal-6)
- [Nomor 7](#soal-7)
- [Nomor 8](#soal-8)
- [Nomor 9](#soal-9)
- [Nomor 10](#soal-10)
- [Nomor 11](#soal-11)
- [Nomor 12](#soal-12)
- [Nomor 13](#soal-13)
- [Nomor 14](#soal-14)
- [Nomor 15](#soal-15)
- [Nomor 16](#soal-16)
- [Nomor 17](#soal-17)
- [Nomor 18](#soal-18)
- [Nomor 19](#soal-19)
- [Nomor 20](#soal-20)

<a name="topologi"></a>
### Topologi
<img src="img/topologi.png">

### Prefix
| IT29 | 10.78 |

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
#### Ruins 
```
auto eth0
iface eth0 inet static
	address 10.72.2.2
	netmask 255.255.255.0
	gateway 10.72.2.1
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

<a name="soal-1"></a>

<a name="soal-2"></a>

<a name="soal-3"></a>

<a name="soal-4"></a>

<a name="soal-5"></a>

<a name="soal-6"></a>

<a name="soal-7"></a>

<a name="soal-8"></a>

<a name="soal-9"></a>

<a name="soal-10"></a>

<a name="soal-11"></a>

<a name="soal-12"></a>

<a name="soal-13"></a>

<a name="soal-14"></a>

<a name="soal-15"></a>

<a name="soal-16"></a>

<a name="soal-17"></a>

<a name="soal-18"></a>

<a name="soal-19"></a>

<a name="soal-20"></a>

