# SysAdmin

Nama  : Danang Tri Atmaja

NIM   : 22.83.0826

## Membuat Server dengan service Berikut
- WebServer (NginX)
- SSH (cockpit)
- Storage server (NextCloud)
- Monitoring Service

## Operating System
Ubuntu Server 22.04
https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso

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
