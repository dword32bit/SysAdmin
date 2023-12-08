# SysAdmin

Nama  : Danang Tri Atmaja

NIM   : 22.83.0826

## Membuat Server dengan service Berikut
- WebServer (NginX) + SSL + Domain
- SSH
- Monitoring Service (cockpit)

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
