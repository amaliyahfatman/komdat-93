## WEBMAIL LITE

### Sekilas Tentang
  Webmail lite adalah sebuah web based IMAP untuk webmail client kategori open source. Webmail lite dapat digunakan untuk mengakses email pada hampir semua IMAP diaktifkan mail server. Panel administrasi web yang terintegrasi memungkinkan anda untuk mengelola pengaturan sistem tanpa manual mengedit file konfigurasi.
  
### Instalasi
Tahap instalasi untuk Webmail lite adalah sebagai berikut

Install ssh

```sh
$ ssh apt update
$ ssh apt install ssh
```
Akses remote dari host
```sh
$ ssh adam@localhost -p 22 atau ssh adam@172.18.88.93 -p 22
```
Install apk yang  berkaitan
```sh
$ sudo apt install apache2
$ sudo apt install mysql-server
$ sudo apt install php
$ sudo apt install libapache2-mod-php
$ sudo apt install php-mysql
$ sudo apt install php-gd-php-mcrypt php-mbstring php-xml php-ssh2
$ sudo service apache2 restart
```

Install webmail lite
```sh
$ sudo nano/etc/apt/source.list
```
notes: sudo nano untuk text editor di terminal. Nanti kita mengisi "deb http://apt.afterlogic.com" 

Masuk ke sudo su, lalu
```sh
$ wget -qO - http://apt.afterlogic.com/pubkey.asc | apt-key add -
$ apt-get update
$ apt-get install afterlogic-webmail
```

### Konfigurasi
1.Pengaturan pada bagian admin, yaitu ganti username dan passw admin dengan yang baru
```sh
buka browser http://172.18.88.93/afterlogic/adminpanel/
login dengan mail "mailadm" pass "12345"
pilih tab "system --> security"
Ganti username pada bagian "AdminPanel login" dengan username baru
Masukkan password lama pada "Old Password"
Masukkan password baru pada "New Password"
Kemudian konfirmasi password dan save
```
2.Mengatur database
Sebelum mengatur database sebaiknya kita cek dulu database kita sudah ada atau tidak, dengan cara:
cek database pada root
```sh
$ mysql -u root -p
$ show database;
$ use webmail;  
$ show tables;
```
Jika belum ada database maka lakukan pengaturan database pada Webmail lite
```sh
- buka di browser http://172.18.88.93/afterlogic/adminpanel/
- login
- pilih tab "system --> Database Setting"
- pilih "MySQL" pada "SQL type"
- pada bagian "SQl login" masukkan nama tempat penyimpanan database webmail, karena database afterlogic terdapat pada root maka bagian ini kita isi dengan "root"
- masukkan password database pada SQl password
- masukkan nama database yang digunakan pada "Database name", untuk database yang kami gunakan adalah "webmail"
- pada bagian "Host" masukkan host yang digunakan. Pada bagian ini kita isi localhost.
- Selanjutnya "test connection"
- Kemudian save
```
3.Pengaturan login dengan gmail
```sh
- pada adminpanel pilih tab "Domains --> ceklis Name --> Default Setting"
- pada bagian "Incoming mail" ganti dengan "imap.gmail.com" dan pada bagian "Port" diganti dengan "993", kemudian ceklis pada Use SSL
- pada bagian "Outgoing mail" ganti dengan "smtp.gmail.com" dan pada bagian "Port" diganti dengan "465", kemudian ceklis pada Use SSL
- Kemudian save
```

4.Pengaturan Dropbox 
```sh
- Masuk ke akun dropbox dengan akun email anda
- pilih "Developers" pada bagian footer dropbox atau pada tools
- pilih "My Apps"
- Klik button "Create App"
- Pilih "Dropbox API"
- Pilih "Full Dropbox-Access to all files and folders in a user's dropbox"
- Isi nama app yang akan digunakan
- Klik button "Create"
- Isi kolom  Redirect URIs pada OAuth2, dengan format 	http://yourdomain.com/webmail/?external-services=dropbox 
	 http://yourdomain.com/webmail/ .  Lalu Klik Add.
	Contoh :http://localhost:8888/afterlogic/?external-services=dropbox
- Klik "Apply"
```

5.Pengaturan akun afterlogic
```sh
- Pilih "Manage Folder" pada akun afterlogic
- Pilih "Eksternal Service"
- Ceklist "Authentication" dan "File Storage"
- Klik "Apply"
```


### Cara Pemakaian
Masuk akun:
1. Buka diweb browser http://172.18.88.93/afterlogic/

![N|Soild](https://4.bp.blogspot.com/-wjQ3l7HQkYU/WP_-cJZhwjI/AAAAAAAAAAQ/PLPpvenfnZkTpiGQlTbQeYmUNKkxTw9-QCEw/s1600/masukgm.png)

2. Isi username dan password email. Pastikan akun email anda bisa diakses dengan web yang tidak aman.

![N|Soild](https://4.bp.blogspot.com/-5eJ4Y1bZXsg/WP_-hMm3AeI/AAAAAAAAABE/aWaAaUH2FfYFTkwH13dsUJyM2QJ6Hr1-wCEw/s1600/Screenshot%2Bfrom%2B2017-04-02%2B13-26-32.png)

  maka muncullah tampilan seperti berikut.
![N|Soild](https://4.bp.blogspot.com/-EPgJ7kyd-L0/WP_-gCQFXUI/AAAAAAAAAA4/F-6RFzrdwBULByT_2ibw3DEjHGXYm5GyQCEw/s1600/pilih%2Bmanage%2Bal.png)


Mengirim file  dengan webmail:
1. Klik "New Message"
![N|Soild](https://4.bp.blogspot.com/-EPgJ7kyd-L0/WP_-gCQFXUI/AAAAAAAAAA4/F-6RFzrdwBULByT_2ibw3DEjHGXYm5GyQCEw/s1600/pilih%2Bmanage%2Bal.png)
2. Isi tujuan, subjeknya pada To dan Subject
![N|Soild](https://1.bp.blogspot.com/-Y1WzFssPUT8/WP_-uKX406I/AAAAAAAAADQ/UkbGazK_b9o3U-GBjiZ9MRhzKyT0RJpiACEw/s1600/kirim.png)
3. pilih file yang akan dikirim 
![N|Soild](https://1.bp.blogspot.com/-PvQmp9I33Lc/WP_-giD2neI/AAAAAAAAAA8/iFODRWBvKt0TKneCxKlE7fvDOIhO2_LawCEw/s1600/pilih%2Bfile.png)
4. kirim dengan klik "SEND"
![N|Soild](https://2.bp.blogspot.com/-WjccjbaixYo/WP_-kEFcIpI/AAAAAAAAABg/sPDxUOcgu04fFEF9II4_SFatiDT6MhxWwCEw/s1600/tampilan.png)

Mengirim email dari file drobox:
1. Klik "New Message"
![N|Soild](https://4.bp.blogspot.com/-EPgJ7kyd-L0/WP_-gCQFXUI/AAAAAAAAAA4/F-6RFzrdwBULByT_2ibw3DEjHGXYm5GyQCEw/s1600/pilih%2Bmanage%2Bal.png)
2. Isi tujuan, subjeknya pada To dan Subject
3. pilih file yang akan dikirim
![N|Soild](https://4.bp.blogspot.com/-TUXfR8Wcp9Y/WP_-n2i5u1I/AAAAAAAAACQ/G7wdpObgQpIoDb_JK1687_b0Bj0XaFV6ACEw/s1600/dropbox1.png) 
4. Kirim dengan klik "SEND"
![N|Soild](https://2.bp.blogspot.com/-1on6AtL92EA/WP_-cATfqQI/AAAAAAAAAAU/Z_SNcP2xD_EhS_vylDJB8z9a60ZsFFnfACEw/s1600/mau%2Bkirim%2Bdrop%2Bfile.png)

### Kekurangan dan Kelebihan 
Kelebihan :
1. Dapat melakukan attachment file dalam keadaan offline
2. Bebas dari spam dan iklan
3. Dapat mengembalikan email yang telah dihapus

Kekurangan :
1. Tidak dapat melakukan sign up
2. Harus melakukan setting terlebih dahulu pada server email yang digunakan

### Referensi
https://afterlogic.org/webmail-lite



