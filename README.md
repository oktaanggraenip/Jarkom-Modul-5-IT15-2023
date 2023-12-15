# Jarkom-Modul-5-IT15-2023

|    Anggota Kelompok     |     NRP     |
| ---                     | ---         |
| Oktavia Anggraeni P.    | 5027211001  |
| Brigita Naraduhita P.P. | 5027211055  |

## Daftar Isi
- [Topologi](#Topologi)
- [VLSM](#VLSM)
- [Konfigurasi GNS](#Konfigurasi)
- [Routing](#Routing)

# <a name="Topologi"></a> Topologi


# <a name="VLSM"></a> VLSM


# <a name="Konfigurasi GNS"></a> Konfigurasi GNS
## Config Router
- Aura
```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp

# eth1 A3-Heiter
auto eth1
iface eth1 inet static
    address 10.71.14.133
    netmask 255.255.255.252

# eth2 A4-Frieren
auto eth2
iface eth2 inet static
    address 10.71.14.137
    netmask 255.255.255.252
```

- Heiter
```
# Aura-A3
auto eth0
iface eth0 inet static
	address 10.71.14.134
	netmask 255.255.255.252
	gateway 10.71.14.133

# TurkRegion-A2
auto eth1
iface eth1 inet static
	address 10.71.0.1
	netmask 255.255.248.0

# Sein, Grobe-A1
auto eth2
iface eth2 inet static
	address 10.71.8.1
	netmask 255.255.252.0
```

- Frieren
```
# Aura-A4
auto eth0
iface eth0 inet static
	address 10.71.14.138
	netmask 255.255.255.252
	gateway 10.71.14.137

# Stark-A5
auto eth1
iface eth1 inet static
	address 10.71.14.141
	netmask 255.255.255.252

# Himmel-A6
auto eth2
iface eth2 inet static
	address 10.71.14.145
	netmask 255.255.255.252
```

- Himmel
```
# Frieren-A6
auto eth0
iface eth0 inet static
	address 10.71.14.146
	netmask 255.255.255.252
	gateway 10.71.14.145

# LaubHils-A7
auto eth1
iface eth1 inet static
	address 10.71.12.1
	netmask 255.255.254.0

# SchwerMountain-A8
auto eth2
iface eth2 inet static
	address 10.71.14.1
	netmask 255.255.255.128
```

- Fern
```
# SchwerMountain-A8
auto eth0
iface eth0 inet static
	address 10.71.14.3
	netmask 255.255.255.128
	gateway 10.71.14.1

# Richter-A9
auto eth1
iface eth1 inet static
	address 10.71.14.149
	netmask 255.255.255.252

# Revolte-A10
auto eth2
iface eth2 inet static
	address 10.71.14.129
	netmask 255.255.255.252
```

## Config Server
- Richter
```
# Fern-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.150
	netmask 255.255.255.252
	gateway 10.71.14.149

```

- Revolte
```
# Switch2-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.130
	netmask 255.255.255.252
    gateway 10.71.14.129
```

- Stark
```
# Frieren-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.142
	netmask 255.255.255.252
    gateway 10.71.14.141
```

- Sein
```
# Switch3-eth0
auto eth0
iface eth2 inet static
	address 10.71.8.2
	netmask 255.255.252.0
    gateway 10.71.8.1
```

Setelah dilakukan konfigurasi pada server, jalankan `echo "nameserver 192.168.122.1" > /etc/resolv.conf` pada masing-masing server

## Config Client/Host
- SchwerMountain
```
# SchwerMountain-A8
auto eth0
iface eth0 inet static
    address 10.71.14.2
    netmask 255.255.255.128
    gateway 10.71.14.1

```

- LaubHills 
```
# LaubHils-A7
auto eth0
iface eth0 inet static
    address 10.71.12.2
    netmask 255.255.254.0
    gateway 10.71.12.1
```

- TurkRegion
```
# Heiter
auto eth0
iface eth0 inet static
    address 10.73.0.2
    netmask 255.255.248.0
    gateway 10.73.0.1
```

- GrobeForest
```
# GrobeForest-A1
auto eth0
iface eth0 inet static
    address 10.71.8.3
    netmask 255.255.252.0
    gateway 10.71.8.1
```


# <a name="Routing"></a> Routing
- Aura
```
route add -net 10.71.14.132 netmask 255.255.255.252 gw 10.71.14.134
route add -net 10.71.14.136 netmask 255.255.255.252 gw 10.71.14.138
route add -net 10.71.0.0 netmask 255.255.248.0 gw 10.71.14.134
route add -net 10.71.8.0 netmask 255.255.252.0 gw 10.71.14.134
route add -net 10.71.14.140 netmask 255.255.255.252 gw 10.71.14.138
route add -net 10.71.14.144 netmask 255.255.255.252 gw 10.71.14.138
route add -net 10.71.12.0 netmask 255.255.254.0 gw 10.71.14.138
route add -net 10.71.14.0 netmask 255.255.255.128 gw 10.71.14.138
route add -net 10.71.14.148 netmask 255.255.255.252 gw 10.71.14.138
route add -net 10.71.14.128 netmask 255.255.255.252 gw 10.71.14.138
```

- Heiter
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.71.14.133
```

- Frieren
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.71.14.137
route add -net 10.71.12.0 netmask 255.255.254.0 gw 10.71.14.146
route add -net 10.71.14.0 netmask 255.255.255.128 gw 10.71.14.146
route add -net 10.71.14.148 netmask 255.255.255.252 gw 10.71.14.146
route add -net 10.71.14.128 netmask 255.255.255.252 gw 10.71.14.146
```

- Himmel
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.71.14.145
route add -net 10.71.14.148 netmask 255.255.255.252 gw 10.71.14.3
route add -net 10.71.14.128 netmask 255.255.255.252 gw 10.71.14.3
```

- Fern
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.71.14.1
```

Masuk kembali ke `Aura` dan jalankan iptables `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.71.0.0/16`

## Config DNS pada Richter
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf

apt-get update
apt-get install bind9 -y

cp /etc/bind/named.conf.options /etc/bind/named.conf.options.backup

echo "options {
    forwarders {
         192.168.122.1;
         8.8.8.8;
    };

    // dnssec-validation auto;
    allow-query{any;};

    directory "/var/cache/bind";

    listen-on-v6 { any; };
};" > /etc/bind/named.conf.options

service bind9 restart
```

## Config DHCP pada Revolte
- Lakukan konfigurasi pada `Aura`, `Heiter`, `Frieren`, `Himmel`, `Fern`

Config dengan memasukkan IP Revolte `10.71.14.130`
```
apt-get install isc-dhcp-relay -y

echo "SERVERS="10.71.14.130"
INTERFACES="eth0 eth1 eth2"
OPTIONS="

## IP forwarding dan acc sumber
echo "net.ipv4.ip_forward=1
net.ipv4.conf.all.accept_source_route=1" >> /etc/sysctl.conf

sysctl -p
```

- Konfigurasi pada `Revolte`
```
apt-get install isc-dhcp-relay -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '
# A1
# A2
# A3
# A4
# A5
# A6
# A7
# A8
# A9
# A10
' > /etc/dhcp/dhcpd.conf
```

Kemudian restart server dhcp dengan command `service isc-dhcp-server restart`
