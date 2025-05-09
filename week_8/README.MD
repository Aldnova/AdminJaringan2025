<div align="center">
  <h1 class="text-align: center;font-weight: bold"><h1>Workshop Administrasi Jaringan</h1>
  <h3 class="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h3>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <div align="center">
  <h3 style="text-align: center;">Disusun Oleh :</h3>
 <p style="text-align: center;">
    <em>Muhammad Rasyid Rafif (3122500030)</em>
  </p>
</div>

## Topologi

<img src="./img/topo.jpg" alt="gambar" width="800">

## Setting IP STATIS
Setting ip dan dns sesuai gambar dibawah :
IP `192.168.8.10` Untuk server
DNS : 192.168.8.1, 10.252.108.10, 10.10.10.1, 202,9,85,3

<img src="./img/IP.jpg" alt="gambar" width="800">

## Instalasi Bind9
### 1. Instalasi
Instalasi BIND menggunakan perintah `sudo apt -y install bind9 bind9utils`.

<img src="./img/b1.png" alt="gambar" width="800">
untuk contoh seperti diatas. saya lupa foto untuk instalasi bind9 saat di lab. karena itu saya pakai foto ini


### 2. Setting named.conf
Gunakan Perintah `sudo nano /etc/bind/named.conf`

<img src="./img/1.jpg" alt="gambar" width="800">

Tambahkan `include "/etc/bind/named.conf.internal-zones";` dibawahnya `include "/etc/bind/named.conf.default-zones"`

<img src="./img/1.1.jpg" alt="gambar" width="800">


### 3. Setting named.conf.options
Gunakan perintah ini `sudo nano /etc/bind/named.conf.options`

<img src="./img/2.jpg" alt="gambar" width="800">
Lalu tambahkan 

```bash
        acl internal-network {
                192.168.8.0/24;
        };
```

ini ditaruh diatas 

```bash 
option { 
    directory "var/cache/bind";
}
```
dan tambahkan ini 
```bash
        allow-query { localhost; internal-network; };
        allow-transfer { localhost; };
        listen-on port 53 { any; };
```
tambahkan ini dibawah 
```bash
// uncomment dan atur forwarders jika perlu.
// forwarders{
//      0.0.0.0;
// };
```
<img src="./img/2.1.jpg" alt="gambar" width="800">

### 4. Setting named.conf.internal-zones


### 5. Setting /etc/default/named
Gunakan perintah `sudo nano /etc/default/named`

<img src="./img/4.jpg" alt="gambar" width="800">

Tambahkan
```bash 
OPTIONS="-u bind -4"
``` 
Dibawah `# startup option for the server` seperti gambar dibawah :

<img src="./img/4.1.jpg" alt="gambar" width="800">

### 6. Setting /etc/bind/kelompok8.home.lan

Gunakan perintah `sudo nano /etc/bind/kelompok8.home.lan`

<img src="./img/5.jpg" alt="gambar" width="800">

Lalu tambahkan Seperti gambar dibawah : 

<img src="./img/5.1.jpg" alt="gambar" width="800">

### 7. Setting /etc/bind/8.168.192.db

Gunakan perintah `sudo nano /etc/bind/8.168.192.db`
<img src="./img/6.jpg" alt="gambar" width="800">

Lalu tambahkan seperti gambar dibawah : 

<img src="./img/6.1.jpg" alt="gambar" width="800">

### 8. Restart named
Gunakan `sudo systemctl restart named` untuk merestart

<img src="./img/7.jpg" alt="gambar" width="800">

### 9. Setting /etc/resolv.conf
Gunakan perintah `sudo nano /etc/resolv.conf`

<img src="./img/8.jpg" alt="gambar" width="800">

Lalu tambahkan seperti gambar dibawah : 



---
## Instalasi Apache2

### 1. Instalasi Apache2
Gunakan perintah `sudo apt -y install apache2` untuk menginstall apache2

<img src="./img/a1.jpg" alt="gambar" width="800">

### 2. Setting /etc/apache2/conf-enabled/security.conf
Gunakan perintah `sudo nano /etc/apache2/conf-enabled/security.conf` seperti gambar dibawah : 

<img src="./img/a2.jpg" alt="gambar" width="800">

Tambahkan dibawah ini sesuai foto yang saya berikan dibawah:
```bash

ServerTokens OS
ServerTokens Prod

```
<img src="./img/a2.1.jpg" alt="gambar" width="800">

### 3. Setting /etc/apache/mods-enabled/dir.conf
Gunakan perintah `sudo nano /etc/apache/mods-enabled/dir.conf` untuk membuka /etc/apache/mods-enabled/dir.conf

<img src="./img/a3.jpg" alt="gambar" width="800">

Lalu ketik sesuai gambar dibawah ini : 

<img src="./img/a3.1.jpg" alt="gambar" width="800">

### 4. Setting /etc/apache2/apache2.conf
Gunakan perintah `sudo nano /etc/apache2/apache2.conf` 

<img src="./img/a4.jpg" alt="gambar" width="800">

Lalu ketik seperti contoh dibawah sesuai contoh gambar : 

```bash

ServerName www.kelompok8.home

```

<img src="./img/a4.1.jpg" alt="gambar" width="800">


### 5. Setting /etc/apache2/sites-enabled/000-default.conf
Gunakan perintah `sudo nano /etc/apache2/sites-enabled/000-default.conf` untuk konfigurasi virtual host default Apache untuk port HTTP 

<img src="./img/a5.jpg" alt="gambar" width="800">

Lalu ketik perintah ini sesuai dari contoh gambar dibawah : 

```bash 

ServerAdmin webmaster@kelompok8.home
DocumentRoot /var/www/html

```
<img src="./img/a5.1.jpg" alt="gambar" width="800">


### 6. Reload apache2 service

Gunakan perintah `systemctl reload apache2.service`  untuk memuat ulang (reload) konfigurasi Apache tanpa menghentikan layanan Apache yang sedang berjalan 

<img src="./img/a6.jpg" alt="gambar" width="800">

### 7. Hasil dari Web Server
Gunakan IP `192.168.8.10` di browser untuk melihat apache2 web server sudah berfungsi atau belum. jika muncul seperti gambar dibawah maka web server-nya sudah aktif dan berjalan dengan baik.

<img src="./img/a7.jpg" alt="gambar" width="800">

----





`KomowDO`