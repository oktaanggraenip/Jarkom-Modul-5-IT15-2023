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


# <a name="Konfigurasi"></a> Konfigurasi GNS
## Config Router
- Aura
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1' > /etc/resolv.conf`
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
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
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
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
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
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
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
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
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
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1' > /etc/resolv.conf`
```
# Fern-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.150
	netmask 255.255.255.252
	gateway 10.71.14.149

```

- Revolte
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
```
# Switch2-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.130
	netmask 255.255.255.252
    gateway 10.71.14.129
```

- Stark
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
```
# Frieren-eth0
auto eth0
iface eth0 inet static
	address 10.71.14.142
	netmask 255.255.255.252
    gateway 10.71.14.141
```

- Sein
Tambahkan nameserver sebagai berikut `echo 'nameserver 192.168.122.1 nameserver 10.71.14.150' > /etc/resolv.conf`
```
# Switch3-eth0
auto eth0
iface eth2 inet static
	address 10.71.8.2
	netmask 255.255.252.0
    gateway 10.71.8.1
```

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
apt-get update
apt-get install bind9 -y

echo 'options {
    directory "/var/cache/bind";
    forwarders {
         192.168.122.1;
    };
    // dnssec-validation auto;
    allow-query { any; };
    listen-on-v6 { any; };
};' > /etc/bind/named.conf.options
```

Tambahkan command berikut pada `etc/bind/named.conf` dan `etc/bind/named.conf.local`
```
echo 'controls {
    inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
};

include "/etc/bind/rndc.key";' > /etc/bind/named.conf

echo 'controls {
    inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
};

include "/etc/bind/rndc.key";' > /etc/bind/named.conf.local
```
Kemudian restart bind9 dengan command
`service bind9 restart`

## Config DHCP pada Revolte
- Lakukan konfigurasi pada `Aura`, `Heiter`, `Frieren`, `Himmel`, `Fern`

Config dengan memasukkan IP Richter `10.71.14.150` ke `/etc/default/isc-dhcp-relay`
```
apt-get update
apt-get install isc-dhcp-relay -y

echo 'SERVERS="10.71.14.150"
INTERFACES="eth0 eth1 eth2"
OPTIONS=' > /etc/default/isc-dhcp-relay

## IP forwarding dan acc sumber
echo 'net.ipv4.ip_forward=1
net.ipv4.conf.all.accept_source_route=1' > /etc/sysctl.conf
```
Kemudian jalankan dhcp dengan `service isc-dhcp-relay restart`


- Konfigurasi pada `Revolte`
```
apt-get update
apt-get install isc-dhcp-server -y

echo 'INTERFACESv4="eth0"
INTERFACESv6="" ' > /etc/default/isc-dhcp-server

echo 'ddns-update-style none;
option domain-name "example.org";
option domain-name-servers 10.71.14.150;

default-lease-time 600;
max-lease-time 7200;

authoritative;
log-facility local7;

# A1
subnet 10.71.8.0 netmask 255.255.252.0 {
    range 10.71.8.1 10.71.11.254;
    option routers 10.71.8.1;
    option broadcast-address 10.71.11.255;
    option domain-name-servers 10.71.14.150;
}

# A2
subnet 10.71.0.0 netmask 255.255.248.0 {
    range 10.71.0.1 10.71.7.254;
    option routers 10.71.0.1;
    option broadcast-address 10.71.7.255;
    option domain-name-servers 10.71.14.150;
}

# A3
subnet 10.71.14.132 netmask 255.255.255.252 {
    option routers 10.71.14.134;
}

# A4
subnet 10.71.14.136 netmask 255.255.255.252 {
    option routers 10.71.14.138;
}

# A5
subnet 10.71.14.140 netmask 255.255.255.252 {
    option routers 10.71.14.142;
}

# A6
subnet 10.71.14.144 netmask 255.255.255.252 {
    option routers 10.71.14.138;
}

# A7
subnet 10.71.12.0 netmask 255.255.254.0 {
    range 10.71.12.1 10.71.13.254;
    option routers 10.71.12.2;
    option broadcast-address 10.71.13.255;
    option domain-name-servers 10.71.14.150;
}

# A8
subnet 10.71.14.0 netmask 255.255.255.128 {
    range 10.71.14.1 10.71.14.126;
    option routers 10.71.14.2;
    option broadcast-address 10.71.14.127;
    option domain-name-servers 192.223.14.134;
}

# A9
subnet 10.71.14.148 netmask 255.255.255.252 {
    option routers 10.71.14.150;
}

# A10
subnet 10.71.14.128 netmask 255.255.255.252 {
    option routers 10.71.14.130;
}' > /etc/dhcp/dhcpd.conf
```
Kemudian restart dhcp server dengan command `service isc-dhcp-server restart`
