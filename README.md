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
2. Isi username dan password email. Pastikan akun email anda bisa diakses dengan web yang tidak aman.

  maka muncullah tampilan seperti berikut.






