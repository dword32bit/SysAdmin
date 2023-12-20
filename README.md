# SysAdmin

Nama  : Danang Tri Atmaja

NIM   : 22.83.0826

## Membuat Server dengan service Berikut
- WebServer (NginX) + SSL + Domain
- SSH
- Monitoring + Console Service (cockpit)

## Operating System
Ubuntu Server 22.04

## Install SSH di Ubuntu 22.04
```bash

sudo apt-get update
sudo apt-get install openssh-server

# konfigurasi sshd.conf
# hilangkan tanda (#) pada :

Port 22
PermitRootLogin prohibit-password

# izinkan SSH untuk melewati firewall
sudo ufw allow ssh
```
SSH sudah terinstall, anda bisa menggunakan nya pada cmd/terminal
menggunakan command :

> ssh user@ip_address
contoh

> ssh and@103.82.92.91

karena menggunakan konfigurasi default, maka port ssh adalah 22

## Install cockpit
```bash
# Installasi 
sudo apt install cockpit

# izinkan port 9090 untuk melewati firewall
sudo ufw allow 9090/tcp
```
## Install NginX + SSL (Let's Encrypt)
![download](https://github.com/dword32bit/SysAdmin/assets/114817148/e3318239-a3a4-449d-bd86-79edc65c4b7f)
Saya menggunakan NginX untuk mengelola Web saya

```bash
#Installasi NginX
sudo apt install nginx

#Periksa status NginX
sudo systemctl status nginx
```
![image](https://github.com/dword32bit/SysAdmin/assets/114817148/4640fe36-9040-4bf5-ad76-410252ad6855)

### Install Certbot
certbot adalah sebuah aplikasi linux untuk mendapatkan sertifikat let's encrypt dengan cepat

berikut cara installasi nya
```bash
sudo apt install certbot python3-certbot-nginx
certbot --version
```
### Konfigurasi NginX
untuk melakukan konfigurasi menggunakan nano
```bash
sudo nano /etc/nginx/sites-available/danangtri.my.id.conf
```
```bash
server {
        listen 80;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name danangtri.my.id www.danangtri.my.id;

        location / {
                try_files $uri $uri/ =404;
        }

        error_log /var/log/nginx/danangtri.my.id.error;
        access_log /var/log/nginx/danangtri.my.id.access;

}
```
simpan konfigurasi dan jalankan konfigurasi tersebut
```bash
sudo ln -s /etc/nginx/sites-available/danangtri.my.id.conf /etc/nginx/sites-enabled/danangtri.my.id.conf

#Verifikasi konfigurasi nginx
sudo nginx -t

#jika muncul test is successful berarti tidak ada kendala dalam konfigurasi nginx

#restart nginx
sudo systemctl restart nginx
```
