[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)

| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Azizah Elok Harvianti | 5025221243 | Jaringan Komputer (D) |
| Christoforus Indra Bagus Pratama | 5025231124 | Jaringan Komputer (D) |
# Daftar isi
- [Soal 0](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-0)
- [Soal 1](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-1)
- [Soal 2](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-2)
- [Soal 3](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-3)
- [Soal 4](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-4)
- [Soal 5](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-5)
- [Soal 6](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-6)
- [Soal 7](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-7)
- [Soal 8](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-8)
- [Soal 9](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-9)
- [Soal 10](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-10)
- [Soal 11](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-11)
- [Soal 12](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-12)
- [Soal 13](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-13)
- [Soal 14](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-14)
- [Soal 15](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-15)
- [Soal 16](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-16)
- [Soal 17](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-17)
- [Soal 18](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-18)
- [Soal 19](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-19)
- [Soal 20](https://github.com/itozt/UjiCobaJarkom/blob/main/README.md#soal-20)
  
# Topologi
![image](https://github.com/user-attachments/assets/d246bd39-4cb9-413b-9094-c973d37d1ed8)

<br>

> Template testing report: https://docs.google.com/document/d/17T0fsnh_4zZTrG-lELDJ88intrc9mkwCzZ_s-23JLCc/edit?usp=sharing

## Put your testing report here! 
> The report is sent in PDF format, uploaded to Drive, and set to public view.

`put the link here`

## Soal 0

> Pada perlombaan akhir tahun kali ini, semua worker dan client ikut serta di dalamnya sebagai perwakilan dari masing-masing asrama. Persiapan yang dilakukan untuk perlombaan ini adalah dengan setup semua network configuration yang sesuai dengan tabel peran diatas. Khusus untuk client menggunakan konfigurasi dari DHCP Server.

**Answer**

- Dumbledore (Router) :

```
auto eth0
iface eth0 inet dhcp
up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.130.0.0/16

auto eth1
iface eth1 inet static
    address 10.130.1.0
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 10.130.2.0
    netmask 255.255.255.0

auto eth3
iface eth3 inet static
    address 10.130.3.0
    netmask 255.255.255.0

auto eth4
iface eth4 inet static
    address 10.130.4.0
    netmask 255.255.255.0

auto eth5
iface eth5 inet static
    address 10.130.5.0
    netmask 255.255.255.0

auto eth6
iface eth6 inet static
    address 10.130.6.0
    netmask 255.255.255.0
```
- HarryPotter (PHP Worker) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.1.1
	  netmask 255.255.255.0
	  gateway 10.130.1.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- RonWeasley (PHP Worker) :

  ```
  auto eth0
  iface eth0 inet static
	   address 10.130.1.2
           netmask 255.255.255.0
	   gateway 10.130.1.0
	   up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- HermioneGranger (PHP Worker) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.1.3
          netmask 255.255.255.0
	  gateway 10.130.1.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- SeverusSnape (DHCP Server) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.3.1
	  netmask 255.255.255.0
	  gateway 10.130.3.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- McGonagall (DNS Server) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.3.2
	  netmask 255.255.255.0
	  gateway 10.130.3.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Hagrid (Database Server) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.4.1
	  netmask 255.255.255.0
	  gateway 10.130.4.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Voldemort (Load Balancer) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.4.2
	  netmask 255.255.255.0
	  gateway 10.130.4.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- Dementor (Load Balancer) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.4.3
	  netmask 255.255.255.0
	  gateway 10.130.4.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- LunaLovegood (Laravel Worker) :

  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.6.3
	  netmask 255.255.255.0
	  gateway 10.130.6.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- FiliusFlitwick (Laravel Worker) :
  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.6.2
	  netmask 255.255.255.0
	  gateway 10.130.6.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- ChoChang (Laravel Worker) :
  ```
  auto eth0
  iface eth0 inet static
	  address 10.130.6.1
	  netmask 255.255.255.0
	  gateway 10.130.6.0
	  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

- DracoMalfoy (Client) :
  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- AstoriaGreengrass (Client) :
  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- SusanBones (Client) :
  ```
  auto eth0
  iface eth0 inet dhcp
  ```

- HannahAbbott (Client) :
  ```
  auto eth0
  iface eth0 inet dhcp
  ```
## Command Setup Awal
Sebelum memulai, praktikan memberikan command berikut ke setiap node :
- DNS Server
  ```
  apt-get update
  apt-get install bind9 -y  
  ```
- DHCP Server<br>
  > DNS Server harus sudah berjalan terlebih dahulu
  ```
  apt-get update
  apt install isc-dhcp-server -y

  echo 'INTERFACESv4="eth0" ' > /etc/default/isc-dhcp-server 
  ```
- DHCP Relay (Router)
  ```
  apt-get update
  apt install isc-dhcp-relay -y

  echo '
  SERVERS="10.130.3.1"  
  INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
  OPTIONS=
  ' > /etc/default/isc-dhcp-relay

  echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf
  ```
- Database Server
  ```
  apt-get update
  apt-get install mariadb-server -y
  service mysql start

  # Ganti [bind-address] pada file /etc/mysql/mariadb.conf.d/50-server.cnf menjadi 0.0.0.0
  # Lakukan restart mysql kembali
  service mysql restart
  ```
- Load Balancer
  ```
  apt-get update
  apt-get install apache2-utils -y
  apt-get install nginx -y
  apt-get install lynx -y
  service nginx start
  ```
- PHP Worker
  ```
  apt-get update
  apt-get install nginx -y
  apt-get install wget -y
  apt-get install unzip -y
  apt-get install lynx -y
  apt-get install htop -y
  apt-get install apache2-utils -y
  apt-get install php7.3-fpm php7.3-common php7.3-mysql php7.3-gmp php7.3-curl php7.3-intl php7.3-mbstring php7.3-xmlrpc php7.3-gd php7.3-xml php7.3-cli php7.3-zip -y

  service nginx start
  service php7.3-fpm start
  ```
- Laravel Worker
  ```
  apt-get update
  apt-get install lynx -y
  apt-get install mariadb-client -y
  	 # Tes Koneksi worker ke database dengan :
  	 # mariadb --host=10.130.4.1 --port=3306   --user=kelompokd31 --password=passwordd31 dbkelompokd31 -e "SHOW DATABASES;"
  apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
  curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
  sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
  apt-get update
  apt-get install php8.0-mbstring php8.0-xml php8.0-cli   php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
  apt-get install nginx -y

  service nginx start
  service php8.0-fpm start
  ```
- Client
  ```
  apt-get update
  apt-get install lynx -y
  apt-get install htop -y
  apt-get install apache2-utils -y
  apt-get install jq -y
  ```
  
## Soal 1

> Melakukan registrasi subdomain untuk PHP worker bernama gryffindor.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Voldemort dan untuk laravel worker bernama ravenclaw.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Dementor. Seluruh domain ini berkumpul dalam suatu ruang atau folder bernama hogwarts

> _Registering subdomains for the PHP workers named gryffindor.hogwarts.yyy.com, pointing to the IP Voldemort load balancer, and for the Laravel workers named ravenclaw.hogwarts.yyy.com, pointing to the IP Dementor load balancer. All domains are gathered in a folder named "hogwarts."_

**Answer:**

- Screenshot
  > Cek di client AstroriaGreengrass dengan nameserver yang sudah `10.130.3.2`
 ![Screenshot 2024-10-23 140021](https://github.com/user-attachments/assets/970f9ec3-4335-4858-8203-bf4a65524492)

- Configuration
  > Konfigurasi berikut dijalankan di DNS Server (McGonagall)
  ```  
  mkdir -p /etc/bind/hogwarts

  echo '
  zone "hogwarts.d31.com" {
    type master;
    file "/etc/bind/hogwarts/hogwarts.d31.com";
  };

  zone "ravenclaw.hogwarts.d31.com" {
    type master;
    file "/etc/bind/hogwarts/ravenclaw.hogwarts.d31.com";
  };

  zone "gryffindor.hogwarts.d31.com" {
    type master;
    file "/etc/bind/hogwarts/gryffindor.hogwarts.d31.com";
  };

  zone "1.130.10.in-addr.arpa" {
    type master;
    file "/etc/bind/hogwarts/1.130.10.in-addr.arpa";
  };

  zone "6.130.10.in-addr.arpa" {
    type master;
    file "/etc/bind/hogwarts/6.130.10.in-addr.arpa";
  };' > /etc/bind/named.conf.local

  cp /etc/bind/db.local /etc/bind/hogwarts/hogwarts.d31.com
  cp /etc/bind/db.local /etc/bind/hogwarts/ravenclaw.hogwarts.d31.com
  cp /etc/bind/db.local /etc/bind/hogwarts/gryffindor.hogwarts.d31.com
  cp /etc/bind/db.local /etc/bind/hogwarts/1.130.10.in-addr.arpa
  cp /etc/bind/db.local /etc/bind/hogwarts/6.130.10.in-addr.arpa

  echo '
  $TTL    604800
  @       IN      SOA     hogwarts.d31.com. root.hogwarts.d31.com. (
                          2024102201    ; Serial
                          604800        ; Refresh
                          86400         ; Retry
                          2419200       ; Expire
                          604800 )      ; Negative Cache TTL
  ;
  @               IN      NS      hogwarts.d31.com.
  @               IN      A       10.130.3.2 ; MasterDNS
  www             IN      CNAME   hogwarts.d31.com.
  ' > /etc/bind/hogwarts/hogwarts.d31.com

  echo ';
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     ravenclaw.hogwarts.d31.com. root.ravenclaw.hogwarts.d31.com. (
                          2024102201      ; Serial
                           604800         ; Refresh
                            86400         ; Retry
                          2419200         ; Expire
                           604800 )       ; Negative Cache TTL
  ;
  @       IN      A       10.130.3.2; Master DNS
  @       IN      NS      ravenclaw.hogwarts.d31.com.
  @       IN      A       10.130.4.2    ; IP Voldemort (Load Balancer untuk Laravel)
  www     IN      CNAME   ravenclaw.hogwarts.d31.com.' > /etc/bind/hogwarts/ravenclaw.hogwarts.d31.com

  echo '
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     gryffindor.hogwarts.d31.com. root.gryffindor.hogwarts.d31.com. (
                          2024102201      ; Serial
                           604800         ; Refresh
                            86400         ; Retry
                          2419200         ; Expire
                           604800 )       ; Negative Cache TTL
  ;  
  @       IN      A       10.130.3.2; Master DNS
  @       IN      NS      gryffindor.hogwarts.d31.com.
  @       IN      A       10.130.4.3     ; IP Dementor (Load Balancer untuk PHP)
  www     IN      CNAME   gryffindor.hogwarts.d31.com.' > /etc/bind/hogwarts/gryffindor.hogwarts.d31.com

  service bind9 start
  ```

- Explanation
  1. `mkdir -p /etc/bind/hogwarts`<br>
      Membuat direktori /etc/bind/hogwarts untuk menyimpan file konfigurasi zona DNS yang spesifik untuk domain hogwarts.d31.com dan subdomainnya.<br>
  2. `echo '...' > /etc/bind/named.conf.local`<br>
      Menulis konfigurasi zona untuk DNS server ke dalam file /etc/bind/named.conf.local<br>
      a. `zone "hogwarts.d31.com" { ... }`<br>
         Mendefinisikan zona DNS untuk hogwarts.d31.com sebagai zona utama (type master), dan file zona tersimpan di /etc/bind/hogwarts/hogwarts.d31.com.<br>
      b. `zone "ravenclaw.hogwarts.d31.com" { .. }`<br>
         Mendefinisikan zona utama untuk subdomain ravenclaw.hogwarts.d31.com.<br>
      c. `zone "gryffindor.hogwarts.d31.com" { ... }`<br>
         Mendefinisikan zona utama untuk subdomain gryffindor.hogwarts.d31.com.<br>
      d. `zone "1.130.10.in-addr.arpa" { .. }`<br>
      Mendefinisikan zona balik untuk IP pada subnet 10.130.1.0 untuk resolusi reverse DNS.<br>
   3. `cp /etc/bind/db.local /etc/bind/hogwarts/...`<br>
      Menyalin file template /etc/bind/db.local ke dalam direktori /etc/bind/Hogwarts sebagai dasar untuk membuat file zona spesifik.<br>
   4. `echo '...' > /etc/bind/hogwarts/hogwarts.d31.com`<br>
      Menambahkan data ke dalam file zona /etc/bind/hogwarts/hogwarts.d31.com<br>
   5. `echo '...' > /etc/bind/hogwarts/ravenclaw.hogwarts.d31.com`<br>
      Menambahkan data ke dalam file zona /etc/bind/hogwarts/ravenclaw.hogwarts.d31.com<br>
   6. `echo '...' > /etc/bind/hogwarts/gryffindor.hogwarts.d31.com`<br>
      Menambahkan data ke dalam file zona /etc/bind/hogwarts/gryffindor.hogwarts.d31.com<br>
   7. `service bind9 start`<br>
      DNS server menjalankan permintaan sesuai konfigurasi zona yang telah ditambahkan.<br>

<br>

## Soal 2

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari [Prefix IP].2.64 - [Prefix IP].2.65 dan [Prefix IP].2.100 - [Prefix IP].2.101
> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari [Prefix IP].5.50 - [Prefix IP].5.51 dan [Prefix IP].5.155 - [Prefix IP].5.156.

**Answer:**

- Screenshot
  Hasil dari DracoMalfoy menunjukkan IP 10.130.2.100. <br>
![Screenshot 2024-10-23 115805](https://github.com/user-attachments/assets/e4d250c7-98f3-496a-8c3b-9c24ea43be3c)<br>
Hasil dari AstoriaGreengrass menunjukkan IP 10.130.2.64<br>
![Screenshot 2024-10-23 120221](https://github.com/user-attachments/assets/2b3d4d5c-c747-49ae-9890-d1fe3bb29f41)<br>
Hasil dari HannahAbbott menunjukkan IP 10.130.5.50<br>
![Screenshot 2024-10-23 125930](https://github.com/user-attachments/assets/9635e921-ef3a-4b88-adc4-a6e75af87b58)<br>
Hasil dari SusanBones menunjukkan IP 10.130.5.51<br>
![image](https://github.com/user-attachments/assets/325b8f3d-0d8e-4e54-98a7-52d862e6e1da)<br>

- Configuration
  > Jalankan di DHCP Server (ServerusSnape)
  ```
  echo 'subnet 10.130.1.0 netmask 255.255.255.0 {
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.0;
  }

  subnet 10.130.3.0 netmask 255.255.255.0 {
  }

  subnet 10.130.4.0 netmask 255.255.255.0 {
  }

  subnet 10.130.5.0 netmask 255.255.255.0 {
    range 10.130.5.50 10.130.5.51;
    range 10.130.5.155 10.130.5.156;
    option routers 10.130.5.0;
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
  }' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  # Lakukan restart di DNS Server, DHCP server, dan Router 
  # DNS Server McGonagall : service bind9 restart
  # Router Dumbledore : service isc-dhcp-relay restart
  ```
  - Kemudian cek IP Address di DracoMalfoy, AstoriaGreenGrass, SusanBones, dan HannahAbbott menggunakan command `ip a`

- Explanation
  1. Subnet untuk DracoMalfoy dan AstoriaGreengrass (Switch 2)
      - Subnet : 10.130.2.0/24 dengan rentang IP 10.130.2.64 - 10.130.2.65 dan 10.130.2.100 - 10.130.2.101.
      - Opsi Router : Mengatur gateway ke 10.130.2.1.
  2. Subnet untuk NevilleLongbottom (Switch 5)
      - Subnet : 10.130.5.0/24 dengan rentang IP 10.130.5.50 - 10.130.5.51 dan 10.130.5.155 - 10.130.5.156.
      - Opsi Router : Mengatur gateway ke 10.130.5.1.
  3. Subnet untuk Switch 1, 3, 4, 6
      - Subnet : 10.130.1.0/24 tanpa rentang IP yang ditentukan. (contoh switch 1)
      - Opsi Router : Tidak ada pengaturan router yang ditetapkan.

<br>

## Soal 3

> Khusus untuk HermioneGranger yang berada di switch 1 mendapat range IP dari
[Prefix IP].1.10 - [Prefix IP].1.15 dan [Prefix IP].1.20 - [Prefix IP].1.25

> Khusus untuk ChoChang yang berada di switch 6 mendapat range IP dari 
[Prefix IP].6.10 - [Prefix IP].6.15 dan [Prefix IP].6.20 - [Prefix IP].6.25

**Answer :**

- Screenshot
  Hasil dari HermioneGranger menunjukkan IP 10.130.1.10<br>
  ![image](https://github.com/user-attachments/assets/7fd60dae-2ee4-45aa-9860-78bc689b43cf)<br>
  Hasil dari Chochang menunjukkan IP 10.130.6.10<br>
  ![image](https://github.com/user-attachments/assets/fdc46ebf-f094-41b6-a620-b6246d5a5237)<br>


- Configuration
  > Jalankan di DHCP Server ServerusSnape
    - Ubah konfigurasi HermioneGarnger menjadi dinamis
	```
 	auto eth0
	iface eth0 inet dhcp
  	hwaddress ether [berubah-ubah]
  	```
    - Ubah konfigurasi Chochang menjadi dinamis
	```
 	auto eth0
	iface eth0 inet dhcp
  	hwaddress ether [berubah-ubah]
  	```
    Cek hwaddrees ether dengan menjalankan command ```ip a``` di HermioneGarnger dan Chochang
    - Ubah ```/etc/resolv.conf``` yang awalnya ```nameserver 192.168.122.1``` menjadi ```nameserver 10.130.3.2```
    - Jalankan command berikut di DHCP Server (ServerusSnape) :
  ```
  echo '
  subnet 10.130.1.0 netmask 255.255.255.0 {
    range 10.130.1.10 10.130.1.15;
    range 10.130.1.20 10.130.1.25;
    option routers 10.130.1.0;
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.0;
  }

  subnet 10.130.3.0 netmask 255.255.255.0 {
  }

  subnet 10.130.4.0 netmask 255.255.255.0 {
  }

  subnet 10.130.5.0 netmask 255.255.255.0 {
    range 10.130.5.50 10.130.5.51;
    range 10.130.5.155 10.130.5.156;
    option routers 10.130.5.0;
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
    range 10.130.6.10 10.130.6.15;
    range 10.130.6.20 10.130.6.25;
    option routers 10.130.6.0;
  }
  ' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  # Lakukan restart di DNS Server, DHCP server, dan Router 
  # DNS Server McGonagall : service bind9 restart
  # Router Dumbledore : service isc-dhcp-relay restart
  ```
  - Kemudian cek IP Address di HermioneGranger dan ChoChang menggunakan command `ip a`

- Explanation
  1. Subnet untuk HermioneGranger (Switch 1)
     - Subnet : 10.130.1.0/24 dengan rentang IP 10.130.1.10 - 10.130.1.15 dan 10.130.1.20 - 10.130.1.25.
     - Opsi Router : Mengatur gateway ke 10.130.1.1.
  2. Subnet untuk ChoChang (Switch 6)
     - Subnet : 10.130.6.0/24 dengan rentang IP 10.130.6.10 - 10.130.6.15 dan 10.130.6.20 - 10.130.6.25.
     - Opsi Router : Mengatur gateway ke 10.130.6.1.

<br>

## Soal 4

> Menetapkan batasan waktu untuk DHCP server dalam peminjaman alamat IP untuk client melalui switch 2 selama 5 menit sedangkan client yang melalui switch 5 selama 20 menit. Untuk switch 1 dan switch 6 memiliki batas waktu 10 menit. Alokasi waktu maksimal peminjaman alamat IP selama 100 menit. 

**Answer:**

- Screenshot
  Hasil screenshoot dari AstoriaGreengrass yang terhubung dengan switch 2, muncul `lease time 300` sama dengan 5 menit<br>
  ![image](https://github.com/user-attachments/assets/78bfcf11-8f0e-40bd-8142-2106eec37b65)<br>
  Hasil screenshoot dari SusanBones yang terhubung dengan switch 5, muncul `lease time 1200` sama dengan 20 menit<br>
  ![image](https://github.com/user-attachments/assets/81419d01-fa5d-4a61-923a-d9cc2c9173c1)<br>
  Hasil dari HermioneGranger switch 1, muncul `lease time 600` sama dengan 10 menit.<br>
  ![image](https://github.com/user-attachments/assets/dc8a3dda-5864-4a1f-a163-42884d94ccc0)<br>
  Hasil dari ChoChang switch 6, muncul `lease time 600` sama dengan 10 menit.<br>
  ![image](https://github.com/user-attachments/assets/131b7271-0231-4be6-8684-ee8ce4c2f30d)




- Configuration
  > Jalankan di DHCP Server `ServerusSanpe`
  ```
  echo 'subnet 10.130.1.0 netmask 255.255.255.0 {
    range 10.130.1.10 10.130.1.15;
    range 10.130.1.20 10.130.1.25;
    option routers 10.130.1.0;
    option broadcast-address 10.130.1.255;
    option domain-name-servers 10.130.3.2;
    default-lease-time 600;  # 10 menit (600 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.0;
    option broadcast-address 10.130.2.255;
    option domain-name-servers 10.130.3.2;
    default-lease-time 300;  # 5 menit (300 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }

  subnet 10.130.3.0 netmask 255.255.255.0 {
  }

  subnet 10.130.4.0 netmask 255.255.255.0 {
  }

  subnet 10.130.5.0 netmask 255.255.255.0 {
    range 10.130.5.50 10.130.5.51;
    range 10.130.5.155 10.130.5.156;
    option routers 10.130.5.0;
    option broadcast-address 10.130.5.255;
    option domain-name-servers 10.130.3.2;
    default-lease-time 1200; # 20 menit (1200 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
    range 10.130.6.10 10.130.6.15;
    range 10.130.6.20 10.130.6.25;
    option routers 10.130.6.0;
    option broadcast-address 10.130.6.255;
    option domain-name-servers 10.130.3.2;
    default-lease-time 600;  # 10 menit (600 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  # DNS Server McGonagall : service bind9 restart
  # Router Dumbledore : service isc-dhcp-relay restart
  ```
  - Stop salah satu device client yang terhubung di switch 2 dan switch 5. Kemudian, `Start` lagi.
  - Stop device HermioneGranger yang terhubung di switch 1 dan ChoChang switch 6. Kemudian, `Start` lagi.
  - Jalankan command `telnet 192.168.0.3 [xxxx]` di terminal ubuntu sesuai node
  - Kemudian cek lease time dari IP address device tersebut
  
- Explanation
   1. Switch 1 (Subnet 10.130.1.0) 
      - default-lease-time : 10 menit (600 detik) - IP akan dipinjam selama 10 menit secara default jika tidak ada permintaan khusus.
      - max-lease-time : 100 menit (6000 detik) - IP dapat dipinjam hingga maks 100 menit jika diperpanjang.
   2. Switch 2 (Subnet 10.130.2.0)
      - default-lease-time : 5 menit (300 detik) - IP dipinjam selama 5 menit secara default.
      - max-lease-time : 100 menit (6000 detik) - IP dapat dipinjam hingga maks 100 menit.
   3. Switch 5 (Subnet 10.130.5.0)
      - default-lease-time : 20 menit (1200 detik) - IP dipinjam selama 20 menit secara default.
      - max-lease-time : 100 menit (6000 detik) - IP dapat dipinjam hingga maks 100 menit.
   4. Switch 6 (Subnet 10.130.6.0)
      - default-lease-time : 10 menit (600 detik) - IP dipinjam selama 10 menit secara default.
      - max-lease-time : 100 menit (6000 detik) - IP dapat dipinjam hingga maks 100 menit.

<br>

## Soal 5

> Memastikan bahwa semua CLIENT, HermioneGranger, dan ChoChang harus menggunakan konfigurasi dari DHCP server, menerima DNS dari Professor McGonagall dan dapat akses internet. Khusus untuk HermioneGranger dan ChoChang mendapatkan IP Statis dari DHCP dengan [Prefix IP].x.14. hint: fixed address

**Answer:**

- Screenshot<br>
  Hasil dari HermioneGranger <br>
![Screenshot 2024-10-24 143755](https://github.com/user-attachments/assets/beb7c756-f6d1-489d-9850-48ff55b53366)<br>
  Hasil dari ChoChang <br>
![Screenshot 2024-10-24 143719](https://github.com/user-attachments/assets/768f7368-480b-41b0-bbb0-fa85e8ee95c7)<br>

- Configuration
   - Jalankan di DNS Sever (ServerusSnape)
     ```
     echo '
        host HermioneGranger {
        hardware ethernet 9a:88:76:e5:4f:0b;
        fixed-address 10.130.1.14;
     }
     host ChoChang {
        hardware ethernet f6:57:38:0d:f3:8f;
        fixed-address 10.130.6.14;
     }' >> /etc/dhcp/dhcpd.conf

     service isc-dhcp-server restart
     ```
   - Kemudian restart DHCP Relay dengan `service isc-dhcp-relay restart`
   - Stop dan Start device HermioneGranger dan ChoChang di GNS3
   - Cek IP HermioneGranger dan ChoChang dengan `ip a`

- Explanation
  1. Konfigurasi untuk host HermioneGranger :
   - `hardware ethernet 9a:88:76:e5:4f:0b;` menentukan hwaddress perangkat HermioneGranger.
   - `fixed-address 10.130.1.14;` menetapkan alamat IP statis `10.130.1.14` untuk HermioneGranger.
   - Artinya, setiap kali perangkat dengan hwaddress `9a:88:76:e5:4f:0b` terhubung ke jaringan, DHCP Server akan memberikan alamat IP `10.130.1.14` kepada perangkat tersebut.
  2. Konfigurasi untuk host ChoChang :
   - `hardware ethernet f6:57:38:0d:f3:8f;` menentukan hwaddress perangkat yang bernama ChoChang.
   - `fixed-address 10.130.6.14;` menetapkan alamat IP statis `10.130.6.14` untuk perangkat ini.
   - Artinya, setiap kali perangkat dengan hwaddress `f6:57:38:0d:f3:8f` terhubung ke jaringan, DHCP Server akan memberikan alamat IP `10.130.6.14` kepada perangkat tersebut.

<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

**Answer:**

- Screenshot<br>
  **Di 3 PHP Worker**
  ![NOMOR 6 (1)](https://github.com/user-attachments/assets/b27bf391-e42c-4451-bfdf-c23d9b8a81d6)
  ![NOMOR 6 (2)](https://github.com/user-attachments/assets/42880e9e-123c-46f9-8cee-986601e3bf4a)
  ![NOMOR 6 (3)](https://github.com/user-attachments/assets/b03cd5c0-4c83-4a93-a001-7dd334b66cd7)

- Configuration
> Jalankan konfigurasi berikut di setiap PHP worker
  ```
   
service nginx start
service php7.4-fpm start

wget -O '/var/www/gryffindor.zip' 'https://drive.google.com/uc?export=download&id=17R4Zcxm3emHq21WdMJzSfCxO8FHqvATM'
unzip -o /var/www/gryffindor.zip -d /var/www/gryffindor.hogwarts.d31.com
rm /var/www/gryffindor.zip

chown -R www-data:www-data /var/www/gryffindor.hogwarts.d31.com
chmod -R 755 /var/www/gryffindor.hogwarts.d31.com

cp /etc/nginx/sites-available/default /etc/nginx/sites-available/gryffindor.hogwarts.d31.com
ln -s /etc/nginx/sites-available/gryffindor.hogwarts.d31.com /etc/nginx/sites-enabled/gryffindor.hogwarts.d31.com
rm /etc/nginx/sites-enabled/default


echo '
server {
    listen 80;
    root /var/www/gryffindor.hogwarts.d31.com;
    index index.php index.html index.htm;
    server_name gryffindor.hogwarts.d31.com www.gryffindor.hogwarts.d31.com;
 
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }

    error_log /var/log/nginx/jarkom_error.log;
    access_log /var/log/nginx/jarkom_access.log;
}' > /etc/nginx/sites-available/gryffindor.hogwarts.d31.com



echo '
127.0.0.1 gryffindor.hogwarts.d31.com
127.0.0.1 www.gryffindor.hogwarts.d31.com
# 127.0.1.1 HarryPotter
# 127.0.0.1 localhost
# ::1     localhost ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters

# hostname 
# HarryPotter
' > /etc/hosts

service nginx restart
service php7.4-fpm restart

  ```

- Explanation

Worker PHP di Gryffindor melakukan proses pengunduhan dan ekstraksi website ke direktori server, kemudian mengatur izin akses yang diperlukan. Setelah itu, mereka menyesuaikan konfigurasi Nginx untuk mendukung PHP versi 7.4. Tahap selanjutnya adalah melakukan deployment website ke server agar dapat diakses oleh klien. Setelah menambahkan entri domain pada file /etc/hosts, layanan direstart, dan akses website diverifikasi menggunakan lynx.

<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

**Answer:**

- Screenshot
![NOMOR 7 (1)](https://github.com/user-attachments/assets/180a3efe-1f7d-43be-b693-0f5e4a691329)
![NOMOR 7 (2)](https://github.com/user-attachments/assets/7bfd3714-a1b9-4c4d-83cb-01031af66dfa)
![NOMOR 7 (3)](https://github.com/user-attachments/assets/4cad5df9-9bd8-4ced-9009-81de780a4a0c)
![NOMOR 7 (4)](https://github.com/user-attachments/assets/f7c99036-19b5-4118-8e0f-1d42f6f98674)
![NOMOR 7 (5)](https://github.com/user-attachments/assets/3865475d-def6-4545-924b-2b75fded9a00)

- Configuration <br>
Konfigurasi ini dirancang agar Voldemort dapat mendistribusikan beban kerja secara optimal kepada worker PHP. Sebagai langkah awal pengujian, implementasikan algoritma round robin dan uji file index.php dengan mengonfigurasi upstream backend dan memasukkan nama server dari ketiga PHP worker. Untuk pengujian, gunakan ab di sisi klien dan htop pada Load Balancer untuk memantau beban kerja.
Pastikan juga untuk melakukan proses instalasi dan setup terlebih dahulu. <br>

**Load Balancer :** <br>
```
	cp /etc/nginx/sites-available/default /etc/nginx/sites-available/libray_php

	echo ' 
	upstream backend {
	    server 10.130.1.1;
	    server 10.130.1.2;
	    server 10.130.1.3;
	}

	server {
	    listen 80;
	    server_name gryffindor.hogwarts.d31.com;

             location / {
 	            proxy_pass http://backend;
 	            proxy_set_header    X-Real-IP $remote_addr;
	            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
	            proxy_set_header    Host $http_host;
	    }


	    error_log /var/log/nginx/error.log;
	    access_log /var/log/nginx/access.log;

	}' >/etc/nginx/sites-available/libray_php

	ln -s /etc/nginx/sites-available/libray_php /etc/nginx/sites-enabled/libray_php
	rm /etc/nginx/sites-enabled/default

	service nginx restart

	htop
```
**Client :** <br>
   ```
   ab -n 1000 -c 100 http://www.gryffindor.hogwarts.d31.com/index.php
   ```

- Explanation
1. Hitung mean dengan rumus :
   ```
     T1 + T2 + T3 / 3
     = 3.9 + 5.0 + 8.0 / 3
     = 31.333333333333332 
     = 31.33 m/s
   ```
2. Hitung nilai standar dengan rumus :
   ```
     SD = √ (T1 - Mean)^2 + (T2 - Mean)^2 + (T3 - Mean)^2 / 3
        = √ (3.9 - 31.333333333333332)^2 + (5.0 - 31.333333333333332)^2 + (8.0 - 31.333333333333332)^2 / 3
        = √663.5174999999999
        = 25.75
    ```
Load balancer yang menangani para PHP worker di Gryffindor telah dikonfigurasi dengan algoritma round robin, memungkinkan Voldemort membagi setiap permintaan secara merata ke setiap PHP worker. Pengujian awal dilakukan pada halaman index.php menggunakan Apache Benchmark, dengan total 1.000 permintaan pada kecepatan 100 permintaan per detik, dan diuji sebanyak tiga kali. Rata-rata waktu permintaan mencapai 31,33 ms dengan standar deviasi 25,75 ms, menunjukkan bahwa konfigurasi ini mampu mendistribusikan beban secara optimal dan seimbang di seluruh worker.
<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)

**Answer:**

- Screenshot
![NOMOR 8-1](https://github.com/user-attachments/assets/6f1d1677-6c6d-4fa6-aee9-f8d5ce88e473)
![NOMOR 8-2](https://github.com/user-attachments/assets/84c653ea-0fb2-4817-97dd-5c7c5ab09148)
![NOMOR 8-3](https://github.com/user-attachments/assets/35d692a8-f283-474d-a4cb-dcd43e36425f)

- Configuration<br>
**Load Balancer :** <br>
```
  cp /etc/nginx/sites-available/default /etc/nginx/sites-available/libray_php

echo ' 
upstream backend {
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.d31.com;

    location / {
            proxy_pass http://backend;
            proxy_set_header    X-Real-IP $remote_addr;
            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header    Host $http_host;
    }


    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;

}' >/etc/nginx/sites-available/libray_php

ln -s /etc/nginx/sites-available/libray_php /etc/nginx/sites-enabled/libray_php
rm /etc/nginx/sites-enabled/default

service nginx restart

htop
```
Algoritma bisa diubah sesuai kondisi yang diinginkan
```
echo '
upstream backend {
    # Round Robin
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}
upstream backend {
    # Least-connection
    least_conn;
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}
upstream backend {
    # ip_hash
    ip_hash;
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}
' >/etc/nginx/sites-available/libray_php
```
Inilah konfigurasi untuk melakukan monitoring menggunakan JMeter, yang nantinya diunduh dalam bentuk UI website. Pastikan menyesuaikan format file output yang dihasilkan.<br>
**Client** : <br>
```
echo 'nameserver 192.168.122.1 ' > /etc/resolv.conf
apt-get update
java -version
apt-get install openjdk-11-jre
wget https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.6.3.zip
unzip apache-jmeter-5.6.3.zip
cd apache-jmeter-5.6.3/bin
nano test1.jmx

mkdir ../../TEST-1JMX
./jmeter -n -t Test-1.jmx -l Test-1.jmx.csv -e -o ../../TEST-1JMX


echo 'nameserver 8.8.8.8 ' > /etc/resolv.conf
curl -X POST -F "file=@./nomor8.zip" https://webhook.site/857529be-99b6-4296-803a-3358f513e529
```

- Explanation<br>
Dalam penilaian akhir tahun ini, konfigurasi load balancer Nginx disusun untuk mengimplementasikan tiga algoritma yang berbeda: round-robin, least connections, dan IP hash, dengan tujuan untuk menentukan algoritma mana yang paling efektif dalam menangani permintaan pengguna. Pengujian dilakukan menggunakan JMeter dengan 300 thread dan periode ramp-up selama 3 detik untuk mengakses halaman login, home, dan logout. Setiap algoritma diuji sebanyak tiga kali, dan kemudian rata-rata serta standar deviasi waktu respons dihitung untuk mengevaluasi kinerja masing-masing algoritma.

<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

**Answer:**

- Screenshot
![NOMOR 9 (1)](https://github.com/user-attachments/assets/576c80c0-bd9f-46ed-968b-c427cd0551c2)
![NOMOR 9 (2)](https://github.com/user-attachments/assets/b8aadd8c-3aaf-43c3-8f90-3024c7c38726)
![NOMOR 9-3](https://github.com/user-attachments/assets/01866e4f-50a1-4145-b076-9762297f0864)
![NOMOR 9-4](https://github.com/user-attachments/assets/c5f659f6-1006-4248-adfa-be973d66fbd0)

- Configuration<br>
Konfigurasi untuk memberikan akses kepada user agar mereka login terlebih dahulu  ke server sehingga dapat mengakses website.<br>
**PHP Worker** : <br> 
```
nano /etc/nginx/sites-available/default
location / {
       auth_basic "Restricted Area";
       auth_basic_user_file /etc/nginx/secretchamber/htpasswd;
}

service nginx restart
```
**Load Balancer : ** <br>
```
mkdir -p /etc/nginx/secretchamber
htpasswd -c /etc/nginx/secretchamber/htpasswd jarkom

# inputkan password modul3
# ini di client
nginx -t

service nginx restart
```
**Client** : <br>
```
# lynx ke salah satu PHP worker
lynx gryffindor.hogwarts.d31.com
# masukan username dan password
```
- Explanation<br>
Untuk membatasi akses ke Gryffindor melalui Voldemort, konfigurasi ini menerapkan autentikasi dengan menggunakan username “jarkom” dan password “modul3.” File autentikasi disimpan di /etc/nginx/secretchamber/htpasswd. Di sisi PHP worker, konfigurasi dalam /etc/nginx/sites-available/default menggunakan auth_basic untuk mengaktifkan autentikasi dasar, yang mengharuskan pengguna memasukkan kredensial sebelum dapat mengakses. Setelah semua pengaturan dilakukan, Nginx perlu direstart agar perubahan pada pengaturan autentikasi dapat diterapkan.

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

**Answer:**

- Screenshot
1 Worker
![NOMOR 10-3](https://github.com/user-attachments/assets/d7b1ccf7-d100-4ee6-9654-018726dab663)
![NOMOR 10-4](https://github.com/user-attachments/assets/1380a32c-0085-41cd-9b9c-bd47ac9cb57a)<br>
2 Worker
![NOMOR 10-1](https://github.com/user-attachments/assets/0fd88ac4-a300-4a43-9fe4-8a44054db78e)
![NOMOR 10-6](https://github.com/user-attachments/assets/c2ce30c8-ac39-450b-a453-edacbb4d1fa2)<br>
3 Worker
![NOMOR 10-2](https://github.com/user-attachments/assets/98cc4ae2-d2c6-4923-ac62-9861a70d1510)
![NOMOR 10-5](https://github.com/user-attachments/assets/8bdb3630-bf6e-4d5f-b8d3-38cc5230e2b3)


- Configuration <br>
Selalu pastikan untuk mengonfigurasi instalasi terlebih dahulu. Ini adalah implementasi algoritma Round Robin dengan jumlah worker yang berbeda. Pastikan untuk menyesuaikan jumlah worker yang ingin diaktifkan sesuai dengan kebutuhan yang diinginkan.<br>
**Load Balancer :** <br>
```
  echo '
	upstream backend {
	    # Round Robin
	    server 10.130.1.1;
	    server 10.130.1.2;
	    server 10.130.1.3;
	}
	upstream backend  {
    	   # Round Robin
           server 10.130.1.1;
        server 10.130.1.2;
        }
        upstream backend  {
           # Round Robin
           server 10.130.1.1;
        }' >/etc/nginx/sites-available/libray_php

   service nginx restart
```
**Client :** <br>
```
ab -n 300 -c 100 http://www.gryffindor.hogwarts.d31.com/index.php
```
Seperti nomor 8 
```
echo 'nameserver 192.168.122.1 ' > /etc/resolv.conf
apt-get update
java -version
apt-get install openjdk-11-jre
wget https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.6.3.zip
unzip apache-jmeter-5.6.3.zip
cd apache-jmeter-5.6.3/bin
nano test1.jmx

mkdir ../../TEST-1JMX
./jmeter -n -t Test-1.jmx -l Test-1.jmx.csv -e -o ../../TEST-1JMX


echo 'nameserver 8.8.8.8 ' > /etc/resolv.conf
curl -X POST -F "file=@./nomor8.zip" https://webhook.site/857529be-99b6-4296-803a-3358f513e529
```
- Explanation<br>
Setelah menambahkan autentikasi, pengujian ulang dilakukan menggunakan algoritma round-robin di JMeter dengan skenario dan konfigurasi yang sama (300 thread, ramp-up 3 detik, serta alur login-home-logout). Pengujian dilakukan dengan berbagai jumlah worker: 3, 2, dan 1 worker, untuk mengevaluasi kinerja masing-masing konfigurasi worker dalam menghadapi autentikasi dan beban sistem. Konfigurasi load balancer diperbarui dalam file Nginx untuk setiap pengujian sesuai dengan jumlah worker yang aktif, dan hasil dari JMeter mencatat waktu respons serta kinerja secara keseluruhan pada setiap pengujian.

<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

**Answer:**

- Screenshot
![NOMOR 11](https://github.com/user-attachments/assets/964a81a8-5d02-4d0e-addb-89397ee7917a)

- Configuration
**Load Balancer :** <br>
```
echo ' 
upstream backend {
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.d31.com;

    location ~ /informatika {
        rewrite ^/informatika(.*)$ /informatika/id/beranda$1 break;
        proxy_pass https://www.its.ac.id;
        proxy_set_header Host www.its.ac.id;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    auth_basic "Restricted Content";
    auth_basic_user_file /etc/nginx/secretchamber/htpasswd;

    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
}' >/etc/nginx/sites-available/libray_php

service nginx restart
nginx -t
```
**Client :** <br>
```
lynx gryffindor.hogwarts.d31.com/informatika
```

- Explanation
Kolaborasi antara Hogwarts dan ITS memungkinkan setiap permintaan yang diarahkan ke Voldemort dengan akhiran /informatika untuk segera diarahkan ke halaman ITS melalui URL https://www.its.ac.id/informatika/id/beranda/. Dalam konfigurasi ini, Nginx memanfaatkan proxy pass untuk meneruskan permintaan tersebut ke server ITS. Selain itu, header HTTP seperti Host, X-Real-IP, dan X-Forwarded-For juga disertakan untuk memastikan bahwa permintaan tetap teridentifikasi dengan akurat di server tujuan.

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 


**Answer:**

- Screenshot<br>
  HannahAbbott dengan IP `10.130.5.50` diberikan ijin oleh Voldemort<br>
![NOMOR 12-1](https://github.com/user-attachments/assets/143846bc-e94c-4bc5-96b6-b5c8003804f8)
![NOMOR 12-2](https://github.com/user-attachments/assets/bde37bf2-f999-4303-bf35-56f1d3b83710)<br>
  DracoMalfoy dengan IP `10.130.5.65` tidak diberikan ijin oleh Voldemort<br>
  ![NOMOR 12-3](https://github.com/user-attachments/assets/3b282468-a113-4629-bfa6-ec0446cdbe90)
![NOMOR 12-4](https://github.com/user-attachments/assets/e21f0c04-2f4a-4518-ac0f-23d602fe842a)


- Configuration <br>
**Load Balancer :** <br>
```
echo '
upstream backend {
    server 10.130.1.1;
    server 10.130.1.2;
    server 10.130.1.3;
}

server {
    listen 80;
    server_name gryffindor.hogwarts.d31.com www.gryffindor.hogwarts.d31.com;

    location / {
        allow 10.130.2.64;
        allow 10.130.2.100;
        allow 10.130.5.50;
        allow 10.130.5.155;
        deny all; 

        proxy_pass http://backend;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
    }

    auth_basic "Restricted Content";
    auth_basic_user_file /etc/nginx/secretchamber/htpasswd;

    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
}
' >/etc/nginx/sites-available/libray_php

service nginx restart
```
**Client :** <br>
```
lynx gryffindor.hogwarts.d31.com
```

- Explanation <br>
Konfigurasi Nginx disusun untuk mengizinkan akses ke Voldemort hanya dari alamat IP 10.130.2.64, 10.130.2.100, 10.130.5.50, dan 10.130.5.155. Di dalam blok location /, perintah allow digunakan untuk memberikan izin akses kepada IP-IP tersebut, sementara perintah deny all membatasi akses dari alamat IP lainnya.

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 


**Answer:**

- Screenshot<br>
  **Database Server (Hagrid):** <br>
![NOMOR 13-1](https://github.com/user-attachments/assets/b1d7dd31-156c-4797-a11f-4e0ada58993b)
  **Laravel Worker :** <br>
![NOMOR 13-2](https://github.com/user-attachments/assets/8a69f5f5-5de0-4c11-902c-fb46813aae50)

- Configuration <br>
Pastikan untuk melakukan instalasi konfigurasi di Database Server terlebih dahulu. Selanjutnya, jangan lupa untuk mengganti [bind-address] pada file /etc/mysql/mariadb.conf.d/50-server.cnf menjadi 0.0.0.0. Setelah itu, ingat untuk merestart MySQL agar perubahan dapat diterapkan.<br>
  **Database Server (Hagrid):** <br>
```
echo '# This group is read both by the client and the server
# use it for options that affect everything
[client-server]

# Import all .cnf files from configuration directory
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

# Options affecting the MySQL server (mysqld)
[mysqld]
skip-networking=0
skip-bind-address
' > /etc/mysql/my.cnf
```
```
nano /etc/mysql/mariadb.conf.d/50-server.cnf

# Scroll, lalu ganti
bind-address            = 0.0.0.0

service mysql start
```
```
mysql -u root -p
# Enter password: 

CREATE USER 'kelompokd31'@'%' IDENTIFIED BY 'passwordd31';
CREATE USER 'kelompokd31'@'localhost' IDENTIFIED BY 'passwordd31';
CREATE DATABASE dbkelompokd31;
GRANT ALL PRIVILEGES ON *.* TO 'kelompokd31'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'kelompokd31'@'localhost';
FLUSH PRIVILEGES;

exit

service mysql restart
```
Untuk mengakses database, gunakan Laravel Worker dan pastikan untuk selalu memeriksa nameserver DNS.<br>
**Laravel Worker :** <br>
```
mariadb --host=10.130.4.1 --port=3306 --user=kelompokd31 --password=passwordd31 dbkelompokd31 -e "SHOW DATABASES;"
```

- Explanation <br>
Pengaturan database untuk perlombaan ini dilakukan di server Hagrid, memungkinkan Lunalovegood, Filius Flitwick, dan Cho Chang untuk mengaksesnya dengan menggunakan username "kelompokd31" dan password "passwordd31." Pertama, konfigurasi MySQL diubah dengan mengatur bind-address di file 50-server.cnf menjadi 0.0.0.0, yang memungkinkan akses dari semua alamat IP, lalu MySQL di-restart. Selanjutnya, pengguna baru bernama kelompokd31 dibuat dengan hak akses penuh ke database dbkelompokd31, dan hak akses ini diterapkan menggunakan perintah SQL. Setelah semua konfigurasi selesai, pengguna dapat mengakses database melalui Laravel Worker dengan perintah yang sesuai.

<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

**Answer:**

- Screenshot
![NOMOR 14](https://github.com/user-attachments/assets/69bf6cc0-5d8d-40d5-957b-fadd8f56edec)


- Configuration <br>
  **Laravel Worker :** <br>
    - Install Composer
      ```
      wget https://getcomposer.org/download/2.0.13/composer.phar
      chmod +x composer.phar
      mv composer.phar /usr/bin/composer
      ```
    - Konfigurasi Composer package manager untuk mengelola dependensi menggunakan Composer.
      ```
      apt-get install git -y
      cd /var/www && git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
      cd /var/www/laravel-jarkom-modul-3 && composer update
      ```
   - Konfigurasi Environment (kredensial tersembunyi) berfungsi untuk mengatur backend Laravel dan mengakses port yang akan dieksekusi di server yang telah di-setup.
     ```
     cd /var/www/laravel-jarkom-modul-3 && cp .env.example .env
     echo '
     APP_NAME=Laravel
     APP_ENV=local
     APP_KEY=
     APP_DEBUG=true
     APP_URL=http://localhost

     LOG_CHANNEL=stack
     LOG_DEPRECATIONS_CHANNEL=null
     LOG_LEVEL=debug

     DB_CONNECTION=mysql
     DB_HOST=10.130.4.1
     DB_PORT=3306
     DB_DATABASE=dbkelompokd31
     DB_USERNAME=kelompokd31
     DB_PASSWORD=passwordd31

     BROADCAST_DRIVER=log
     CACHE_DRIVER=file
     FILESYSTEM_DISK=local
     QUEUE_CONNECTION=sync
     SESSION_DRIVER=file
     SESSION_LIFETIME=120
     
     MEMCACHED_HOST=127.0.0.1

     REDIS_HOST=127.0.0.1
     REDIS_PASSWORD=null
     REDIS_PORT=6379
     
     MAIL_MAILER=smtp
     MAIL_HOST=mailpit
     MAIL_PORT=1025
     MAIL_USERNAME=null
     MAIL_PASSWORD=null
     MAIL_ENCRYPTION=null
     MAIL_FROM_ADDRESS="hello@example.com"
     MAIL_FROM_NAME="${APP_NAME}"

     AWS_ACCESS_KEY_ID=
     AWS_SECRET_ACCESS_KEY=
     AWS_DEFAULT_REGION=us-east-1
     AWS_BUCKET=
     AWS_USE_PATH_STYLE_ENDPOINT=false

     PUSHER_APP_ID=
     PUSHER_APP_KEY=
     PUSHER_APP_SECRET=
     PUSHER_HOST=
     PUSHER_PORT=443
     PUSHER_SCHEME=https
     PUSHER_APP_CLUSTER=mt1

     VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
     VITE_PUSHER_HOST="${PUSHER_HOST}"
     VITE_PUSHER_PORT="${PUSHER_PORT}"
     VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
     VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"' > /var/www/laravel-jarkom-modul-3/.env
     ```
   - Command Akses Laravel untuk menjalankan semua konfigurasi dalam laravel
     ```
     cd /var/www/laravel-jarkom-modul-3 && php artisan key:generate
     cd /var/www/laravel-jarkom-modul-3 && php artisan config:cache
     cd /var/www/laravel-jarkom-modul-3 && php artisan migrate
     cd /var/www/laravel-jarkom-modul-3 && php artisan db:seed
     cd /var/www/laravel-jarkom-modul-3 && php artisan storage:link
     cd /var/www/laravel-jarkom-modul-3 && php artisan jwt:secret
     cd /var/www/laravel-jarkom-modul-3 && php artisan config:clear
     chown -R www-data.www-data /var/www/laravel-jarkom-modul-3/storage
     ```
   - Konfigurasi untuk Setup Server
     ```
     echo -e '
     server {
     listen 8003;

     root /var/www/laravel-jarkom-modul-3/public;

     index index.php index.html index.htm;
     server_name _;

     location / {
            try_files $uri $uri/ /index.php?$query_string;
     }

     # pass PHP scripts to FastCGI server
     location ~ \.php$ {
      include snippets/fastcgi-php.conf;
      fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
     }

     location ~ /\.ht {
             deny all;
     }

     error_log /var/log/nginx/implementasi_error.log;
     access_log /var/log/nginx/implementasi_access.log;
     }' > /etc/nginx/sites-available/laravel-worker
 
     cp /etc/nginx/sites-available/default /etc/nginx/sites-available/laravel-worker
     rm /etc/nginx/sites-enable/default
     ln -s /etc/nginx/sites-available/laravel-worker /etc/nginx/sites-enabled/laravel-worker

     service nginx restart
     service php8.0-fpm restart
     lynx localhost:8003
     ```

**Client :** <br>
```
lynx localhost:8003
```

- Explanation <br>
Untuk memastikan Lunalovegood, Filius Flitwick, dan Cho Chang memiliki website yang sesuai dengan repositori di GitHub, langkah pertama adalah menginstal PHP 8.0 dan Composer di Laravel Worker. Setelah itu, repositori diunduh menggunakan Git, dan dependensi diperbarui menggunakan Composer. File .env dikonfigurasi untuk menghubungkan aplikasi Laravel dengan database di Hagrid, menggunakan username kelompokd31 dan password passwordd31. Setelah konfigurasi selesai, beberapa perintah Artisan dijalankan untuk menghasilkan kunci aplikasi, melakukan migrasi, dan mengisi database. Terakhir, konfigurasi Nginx disesuaikan untuk menjalankan aplikasi Laravel pada port 8003, dan semua layanan (Nginx dan PHP-FPM) di-restart untuk menerapkan perubahan. Pengguna dapat mengakses website dengan membuka localhost:8003.
<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

**Answer:**

- Screenshot
  ![NOMOR 15-1](https://github.com/user-attachments/assets/26a647ef-4bec-49cb-a96b-3613a7ea1c98)
  ![NOMOR 15-2](https://github.com/user-attachments/assets/b87e2905-a683-49d1-9e6e-653b34e2f756)


- Configuration <br>
  Untuk memungkinkan monitoring langsung menggunakan Apache Benchmark, username dan password dapat dimasukkan ke dalam file .json. Ini memungkinkan akses otomatis terhadap data autentikasi selama pengujian.<br>
  **Client :** <br>
  ```
  apt-get install apache2-utils -y

  echo '
  {
    "username": "kelompokd31",
    "password": "passwordd31"
  }' > register.json
  ```
  Mengakses dengan apache Benchmark<br>
  ```
  ab -n 100 -c 10 -p register.json -T application/json http://10.130.6.2:8003/api/auth/register
  ```
  
- Explanation <br>
  Ketika menguji endpoint `/register` dengan 100 permintaan menggunakan Apache Benchmark, hanya satu permintaan yang berhasil sementara 99 lainnya gagal. Penyebabnya bisa beragam, seperti batasan jumlah permintaan yang mampu ditangani server secara bersamaan, pengaturan konfigurasi yang belum optimal, format permintaan yang mungkin salah, atau autentikasi yang tidak dikonfigurasi dengan benar. Menganalisis log server dan memeriksa pengaturan aplikasi lebih lanjut akan membantu mengidentifikasi alasan pasti dari kegagalan ini.

<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

**Answer:**

- Screenshot
![NOMOR 16-1](https://github.com/user-attachments/assets/d98d6649-090a-4567-814a-72278172c350)
![NOMOR 16-2](https://github.com/user-attachments/assets/1821b221-d23a-405c-8d8a-41068b8f604a)
![NOMOR 16-3](https://github.com/user-attachments/assets/f5eeaabc-77a7-4858-886c-fa0fb9606692)

- Configuration <br>
  **Client :**  <br>
  - Menambahkan username dan password ke dalam file .json memungkinkan monitoring langsung dengan Apache Benchmark.
    ```
    echo '
    {
       "username": "kelompokd31",
       "password": "passwordd31"
    }' > login.json
    ```
  - Mengakses dengan apache Benchmark
    ```
    ab -n 100 -c 10 -p login.json -T application/json http://10.130.6.2:8003/api/auth/login
    ```
  - Memasukkan history login untuk mengakses token
    ```
    curl -X POST -H "Content-Type: application/json" -d @login.json http://10.6.6.2:8003/api/auth/login > historyLogin.txt
    cat historyLogin.txt
    ```

- Explanation <br>
  Pengujian dilakukan pada endpoint `/login` di salah satu server worker menggunakan Apache Benchmark dari klien SusanBones. Sebanyak 100 permintaan dikirim dengan kecepatan 10 permintaan per detik, menggunakan file `login.json` yang berisi data login untuk proses otentikasi. Hasil pengujian mencakup respons token yang diperoleh, yang disimpan dalam file `historyLogin.txt` sebagai referensi untuk analisis lebih lanjut.

<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

**Answer:**

- Screenshot
  ![NOMOR 17-1](https://github.com/user-attachments/assets/7866d6f3-5451-44d8-a42b-4ac2aa94e9d8)
  ![NOMOR 17-2](https://github.com/user-attachments/assets/6da59602-d6a2-44c9-984a-c6f9d07a69dd)
  ![NOMOR 17-3](https://github.com/user-attachments/assets/03d54ede-3976-445a-8431-215bbbdafbe4)

- Configuration <br>
  **Client :** <br>
  ```
  echo "nameserver 8.8.8.8" > /etc/resolv.conf
  apt-get install jq -y
 
  token=$(cat historyLogin.txt | jq -r '.token')

  ab -n 100 -c 10 -p login.json -T application/json http://10.130.6.2:8003/api/me
  ```
  **Load Balancer :** <br>
  ```
  cat /var/log/nginx/access.log
  ```
  
- Explanation <br>
  Untuk menguji endpoint /me dengan 100 permintaan menggunakan Apache Benchmark, sistem dikonfigurasi untuk mengirim 10 permintaan per detik. Respons server kemudian diperiksa untuk memastikan data pengguna yang sedang login sesuai. Token autentikasi diambil dari file historyLogin.txt dan digunakan dalam setiap permintaan. Jika respons menunjukkan detail pengguna yang benar, sistem berfungsi dengan baik. Namun, respons yang tidak sesuai bisa menunjukkan masalah autentikasi atau penanganan permintaan di backend.

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

**Answer:**

- Screenshot
  ![NOMOR 18-1](https://github.com/user-attachments/assets/809ce96a-0be0-4a66-8a08-9d5373b03e11)
  ![NOMOR 18-2](https://github.com/user-attachments/assets/31fde9e6-1fa9-40ec-b7d9-8a91f526de04)

- Configuration <br>
  **Load Balancer :** <br>
  Setup Server
  ```
  echo '
  worker {
    server 10.130.6.1:8004;
    server 10.130.6.2:8005;
    server 10.130.6.3:8006;
  }

  server {
    listen 80;
    server_name gryffindor.hogwarts.d31.com www.gryffindor.hogwarts.d31.com;

    location / {
        proxy_pass http://worker;
    }
    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
  } 
  ' > /etc/nginx/sites-available/laravel-worker

  ln -s /etc/nginx/sites-available/laravel-worker /etc/nginx/sites-enabled/laravel-worker

  service nginx restart

  htop
  ```
  **Client :** <br>
  ```
  ab -n 100 -c 10 -p login.json -T application/json http://www.gryffindor.hogwarts.d31.com/api/auth/login
  ```

- Explanation <br>
  Dengan menggunakan konfigurasi Proxy Bind, setiap worker dihubungkan ke load balancer melalui IP masing-masing, memungkinkan distribusi permintaan pengguna secara merata ke setiap worker. Konfigurasi ini dimulai dengan menambahkan blok worker dalam file Nginx untuk mendefinisikan ketiga worker beserta IP dan port mereka. Selanjutnya, blok server ditambahkan untuk mengarahkan `proxy_pass` ke grup worker yang telah disiapkan, sehingga semua permintaan ke domain `gryffindor.hogwarts.d31.com` dialihkan melalui load balancer. Setelah konfigurasi selesai, pengujian load balancer dilakukan menggunakan Apache Benchmark dari sisi klien guna memastikan bahwa distribusi beban berjalan optimal.

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

**Answer:**

- Screenshot
  ![NOMOR 19-1](https://github.com/user-attachments/assets/c474d33c-9cfe-493c-9110-a4fed01f9ef7)
  ![NOMOR 19-2](https://github.com/user-attachments/assets/31145d9d-860a-4427-a58d-c88779bb6fc8)
  ![NOMOR 19-3](https://github.com/user-attachments/assets/ece02216-1949-4432-84bc-5c7b9c06fee6)

- Configuration
  Karena diminta 3 percobaan, maka ada 3 script berbeda. <br>
  - _Script 1_
  ```
  echo '[www]
  user = www-data
  group = www-data
  listen = /run/php/php8.0-fpm.sock
  listen.owner = www-data
  listen.group = www-data
  php_admin_value[disable_functions] = exec,passthru,shell_exec,system
  php_admin_flag[allow_url_fopen] = off

  ; Choose how the process manager will control the number of child processes.

  pm = dynamic
  pm.max_children = 5
  pm.start_servers = 2
  pm.min_spare_servers = 1
  pm.max_spare_servers = 3' > /etc/php/8.0/fpm/pool.d/www.conf

  service php8.0-fpm restart
  ```
  **Client :** <br>
  ```
  ab -n 100 -c 10 -p login.json -T application/json http://www.gryffindor.hogwarts.d31.com/api/auth/login
  ```
  - _Script 2_
  ```
  echo '[www]
  user = www-data
  group = www-data
  listen = /run/php/php8.0-fpm.sock
  listen.owner = www-data
  listen.group = www-data
  php_admin_value[disable_functions] = exec,passthru,shell_exec,system
  php_admin_flag[allow_url_fopen] = off

  ; Choose how the process manager will control the number of child processes.

  pm = dynamic
  pm.max_children = 25
  pm.start_servers = 5
  pm.min_spare_servers = 3
  pm.max_spare_servers = 10' > /etc/php/8.0/fpm/pool.d/www.conf

  service php8.0-fpm restart
  ```
  **Client :** <br>
  ```
  ab -n 100 -c 10 -p login.json -T application/json http://www.gryffindor.hogwarts.d31.com/api/auth/login
  ```
  - _Script 3_
  ```
  echo '[www]
  user = www-data
  group = www-data
  listen = /run/php/php8.0-fpm.sock
  listen.owner = www-data
  listen.group = www-data
  php_admin_value[disable_functions] = exec,passthru,shell_exec,system
  php_admin_flag[allow_url_fopen] = off

  ; Choose how the process manager will control the number of child processes.

  pm = dynamic
  pm.max_children = 50
  pm.start_servers = 8
  pm.min_spare_servers = 5
  pm.max_spare_servers = 15' > /etc/php/8.0/fpm/pool.d/www.conf

  service php8.0-fpm restart
  ```
  **Client :** <br>
  ```
  ab -n 100 -c 10 -p login.json -T application/json http://www.gryffindor.hogwarts.d31.com/api/auth/login
  ```
- Explanation <br>
  Untuk meningkatkan kinerja server Laravel, PHP-FPM diimplementasikan pada server LunaLovegood, FiliusFlitwick, dan ChoChang. Dalam uji kinerja ini, parameter seperti `pm.max_children`, `pm.start_servers`, `pm.min_spare_servers`, dan `pm.max_spare_servers` disesuaikan dalam tiga skenario berbeda. Setiap skenario dilakukan dengan mengubah nilai parameter tersebut untuk mengamati pengaruhnya terhadap respons sistem. Setelahnya, Apache Benchmark digunakan untuk mengukur performa dengan mengirimkan 100 permintaan pada kecepatan 10 permintaan per detik. Hasil pengujian ini memberikan wawasan mengenai kemampuan sistem dalam menangani beban dan membantu menentukan konfigurasi yang paling efisien untuk kebutuhan saat ini.

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

**Answer:**

- Screenshot
  ![NOMOR 20](https://github.com/user-attachments/assets/312a7163-c27d-4de0-9edf-056694a24f34)
  ![NOMOR 20-2](https://github.com/user-attachments/assets/d9569dc0-b195-4f68-b30c-cbac7c8187b7)
- Configuration
  **Laravel Worker :** <br>
  ```
  echo '[www]
  user = www-data
  group = www-data
  listen = /run/php/php8.0-fpm.sock
  listen.owner = www-data
  listen.group = www-data
  php_admin_value[disable_functions] = exec,passthru,shell_exec,system
  php_admin_flag[allow_url_fopen] = off

  ; Choose how the process manager will control the number of child processes.

  pm = dynamic
  pm.max_children = 100
  pm.start_servers = 20
  pm.min_spare_servers = 15
  pm.max_spare_servers = 30' > /etc/php/8.0/fpm/pool.d/www.conf
  ```
  **Load Balancer :** <br>
  ```
  echo '
  upstream worker {
    server 10.130.6.1:8004;
    server 10.130.6.2:8005;
    server 10.130.6.3:8006;
  }

  server {
    listen 80;
    server_name gryffindor.hogwarts.d31.com www.gryffindor.hogwarts.d31.com;

    location / {
        proxy_pass http://worker;
    }
    error_log /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
  } 
  ' > /etc/nginx/sites-available/laravel-worker

  ln -s /etc/nginx/sites-available/laravel-worker /etc/nginx/sites-enabled/laravel-worker

  service nginx restart
  ```
  **Client :** <br>
  ```
  ab -n 100 -c 10 http://www.gryffindor.hogwarts.d31.com/index.php
  ```
 
- Explanation <br>
  Untuk meningkatkan performa server Laravel, Dumbledore merekomendasikan penerapan algoritma Least-Connections pada load balancer bernama Dementor. Konfigurasi ini dilakukan dengan menyesuaikan parameter PHP-FPM pada server worker Laravel, termasuk meningkatkan nilai `pm.max_children`, `pm.start_servers`, `pm.min_spare_servers`, dan `pm.max_spare_servers` untuk memungkinkan lebih banyak koneksi simultan. Setelah penyesuaian server, kinerja diuji menggunakan Apache Benchmark, yang mengirimkan 100 permintaan dengan laju 10 permintaan per detik. Pengujian ini bertujuan untuk mengevaluasi efektivitas algoritma Least-Connections dalam mengelola beban serta menilai apakah perubahan ini berhasil meningkatkan responsivitas dan stabilitas sistem secara signifikan.

<br>
  
## Problems
- nameserver sering hilang sehingga beberapa kali failed/error/
- Jmeter cukup lama prosesnya di bagian unzip, zip, download, dan lainnya.
- Soal praktikum dan materi terlalu banyak sehingga sedikit sulit menjalani saat praktikum. Namun tetap berusaha sampai bisa. :sunglasses: :sunglasses: :sunglasses:

## Revisions (if any)
- Revisi nomer 6 -20
