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

<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2023/2024</h3>
  <hr><hr>
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

Lalu tambahkan seperti gambar diatas : 



---
