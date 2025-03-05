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

Tugas 2 : Instalasi Virtual Box Pada Komputer Lab

1. Unduh paket VirtualBox dari laman https://www.virtualbox.org/wiki/Linux_Downloads, lalu pilih distribusi Linux yang sesuai. Pada lab komputer, distribusi yang digunakan adalah Debian 12.
   <img src="assets/1.png" alt="gambar 1">



2. Buka folder Download dan buka terminal pada direktori tersebut dan jalankan perintah untuk instalasi Virtual Box 
   `sudo dpkg -i [nama-paket-VirtualBox]` 
   <img src="assets/2.png" alt="gambar 2">
   Bila ada kendala berupa adanya dependency yang belum terinstal, gunakan perintah ini dan jalankan ulang perintah sebelumnya setelah selesai
   `sudo apt --fix-broken install`
   <img src="assets/3.png" alt="gambar 3">
   
4. Unduh image distro Debian yang akan digunakan dalam VirtualBox pada laman http://www.debian.org/download.
   <img src="assets/4.png" alt="gambar 4">
   
6. Bila pada proses pembuatan Virtual Machine ada masalah berupa bahwa user belum tergabung dalam vboxusers, maka gunakan perintah
   `sudo usermod -a -G vboxusers $USER`
   <img src="assets/5.png" alt="gambar 5">
   Dan bila ada error berupa "VirtualBox Kernel driver not installed (rc=1908)", jalankan perintah
   `sudo /sbin/vboxconfig`
   <img src="assets/6.png" alt="gambar 6">
   Bila bertemu masalah yang menyatakan tidak adanya Linux Headers, dapat diselesaikan dengan perintah ini dan mengulang lagi perintah sebelumnya
   `sudo apt --fix-broken install`
   <img src="assets/7.png" alt="gambar 7">
   <img src="assets/8.png" alt="gambar 8">
8. Bila semua masalah telah terselesaikan, dilanjutkan dengan pembuatan Virtual Machine dengan konfigurasi :
     * Memory: 2048 MB
     * CPU: 2 core
     * Penyimpanan: 10 GB

9. Biarkan proses pembuatan Virtual Machine berjalan sebelum dapat digunakan
   <img src="assets/9.png" alt="gambar 9">
