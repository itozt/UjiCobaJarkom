# UjiCobaJarkom

[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Azizah Elok Harvianti | 5025221243 | Jaringan Komputer (D) |
| Christoforus Indra Bagus Pratama | 5025231124 | Jaringan Komputer (D) |

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
  ```
- DHCP Relay
  ```
  apt-get update
  apt install isc-dhcp-relay -y
  ```
- Database Server
  ```
  echo 'nameserver 192.173.1.2' > /etc/resolv.conf
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

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 2

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari [Prefix IP].2.64 - [Prefix IP].2.65 dan [Prefix IP].2.100 - [Prefix IP].2.101

> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari [Prefix IP].5.50 - [Prefix IP].5.51 dan [Prefix IP].5.155 - [Prefix IP].5.156.

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration
  > Jalankan di DHCP Server `ServerusSanpe`
  ```
  echo 'subnet 10.130.1.0 netmask 255.255.255.0 {
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.1;
  }

  subnet 10.130.3.0 netmask 255.255.255.0 {
  }

  subnet 10.130.4.0 netmask 255.255.255.0 {
  }

  subnet 10.130.5.0 netmask 255.255.255.0 {
    range 10.130.5.50 10.130.5.51;
    range 10.130.5.155 10.130.5.156;
    option routers 10.130.5.1;
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
  }' > /etc/dhcp/dhcpd.conf
  ```

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

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration
  > Jalankan di DHCP Server `ServerusSanpe`
  ```
  echo 'subnet 10.130.1.0 netmask 255.255.255.0 {
    range 10.130.1.10 10.130.1.15;
    range 10.130.1.20 10.130.1.25;
    option routers 10.130.1.1;
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.1;
  }

  subnet 10.130.3.0 netmask 255.255.255.0 {
  }

  subnet 10.130.4.0 netmask 255.255.255.0 {
  }

  subnet 10.130.5.0 netmask 255.255.255.0 {
    range 10.130.5.50 10.130.5.51;
    range 10.130.5.155 10.130.5.156;
    option routers 10.130.5.1;
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
    range 10.130.6.10 10.130.6.15;
    range 10.130.6.20 10.130.6.25;
    option routers 10.130.6.1;
  }' > /etc/dhcp/dhcpd.conf
  ```

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

  `Put your screenshot in here`

- Configuration
  > Jalankan di DHCP Server `ServerusSanpe`
  ```
  echo 'subnet 10.130.1.0 netmask 255.255.255.0 {
    range 10.130.1.10 10.130.1.15;
    range 10.130.1.20 10.130.1.25;
    option routers 10.130.1.1;
    default-lease-time 600;  # 10 menit (600 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }

  subnet 10.130.2.0 netmask 255.255.255.0 {
    range 10.130.2.64 10.130.2.65;
    range 10.130.2.100 10.130.2.101;
    option routers 10.130.2.1;
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
    option routers 10.130.5.1;
    default-lease-time 1200; # 20 menit (1200 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }

  subnet 10.130.6.0 netmask 255.255.255.0 {
    range 10.130.6.10 10.130.6.15;
    range 10.130.6.20 10.130.6.25;
    option routers 10.130.6.1;
    default-lease-time 600;  # 10 menit (600 detik)
    max-lease-time 6000;     # 100 menit (6000 detik)
  }' > /etc/dhcp/dhcpd.conf
  ```

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


> _Ensure that all CLIENT, HermioneGranger, and ChoChang use DHCP server configurations, receive DNS from Professor McGonagall, and can access the internet. HermioneGranger and ChoChang must receive static IPs from DHCP with the address [Prefix IP].x.14 (hint: fixed address)._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

> _The Gryffindor house, represented by the PHP workers, must deploy the following website using PHP 7.4._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

> _Voldemort, who is now reformed, becomes the load balancer for the Gryffindor PHP workers. Optimize Voldemort to distribute tasks to the PHP workers. For the initial test, apply the round-robin algorithm and test it to the index.php page using Apache Benchmark with 1,000 requests and 100 requests/second. Do the test 3 times and calculate the mean and standard deviation of time/request._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)


> _For the final assessment, try three different load-balancing algorithms using JMeter with 300 threads and a 3-second ramp-up period. Jmeter have to be able to login, access homepage, and logout. Do the test 3 times for each algorithm, then calculate the mean and standard deviation of response time. (username: wingardium, password: leviosa)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

> _Not all IPs can access Gryffindor's house through Voldemort’s load balancer. Grant access to the Voldemort load balancer. Authentication will require username: “jarkom” and password: “modul3”. Save the authentication file in /etc/nginx/secretchamber._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

> _After adding authentication to Gryffindor, retest using JMeter (round-robin algorithm) with the same scenario, thread, and ramp up period as number 8 (300 thread, 3 sec ramp up period, login-home-logout). This time, test with different numbers of workers: 3 workers, 2 workers, and 1 worker._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

> _Hogwarts has also partnered with ITS for this competition. Any request to Voldemort containing /informatika at the end of the URL should be proxied to the page at https://www.its.ac.id/informatika/id/beranda/._


**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 


> _In addition to requiring authentication for access to Gryffindor through Voldemort’s load balancer, IP restrictions also need to be enforced. Voldemort's load balancer can only be accessed by clients with IPs: [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, and [Prefix IP].5.155. (hint: fixed client IPs first)._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 

> _Database setup for this competition is managed by Hagrid. Ensure that this database can be accessed by LunaLovegood, FiliusFlitwick, and ChoChang using the username: "kelompokyyy" and password: "passwordyyy”_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

> _Additionally, LunaLovegood, FiliusFlitwick, and ChoChang have websites following this GitHub link: Laravel Jarkom Modul 3. Install PHP 8.0 and Composer! Make sure Hagrid's data storage is populated, and the Laravel servers are running on localhost!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

> _Test the /register endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Why did 99 tests fail? Explain!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

> _Test the /login endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Collect the token from the response!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

> _Test the /me endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Check if the response matches the logged-in user!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

> _As the competition nears its end, balance the workload of LunaLovegood, FiliusFlitwick, and ChoChang! Create a Laravel load balancer using Dementor and implement Proxy Bind to link the IPs of the three workers!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _To strengthen the Laravel workers, implement PHP-FPM on LunaLovegood, FiliusFlitwick, and ChoChang. For performance testing, adjust: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Run the tests three times and analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _Finally, Professor Dumbledore suggests that PHP-FPM might not be enough to improve the workers' performance. Implement the Least-Conn algorithm on Dementor. Analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>
  
## Problems

## Revisions (if any)
