# Stratis-Node
Tutorial Stratis Node

## Bahan

VPS



## Tutorial

# 1. Register Link

Buka Browser
https://auroria.launchpad.stratisevm.com/en/overview
centang, next.sampai deposit
(belum lengkap)


masukan command 

```
sudo apt update && sudo apt upgrade
```
Kalau ada perintah [Y/n] ketik Y dan Enter dan jika muncul prompt atau pop up klik OK OK aja


Jika sudah selesai atur firewallnya

```
sudo ufw allow 30303/tcp
sudo ufw allow 30303/udp
sudo ufw deny 8545/tcp
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow out 13000/tcp
sudo ufw allow out 13000/udp
sudo ufw allow out 12000/tcp
sudo ufw allow out 12000/udp
sudo ufw allow 13000/tcp
sudo ufw allow 13000/udp
sudo ufw allow 12000/tcp
sudo ufw allow 12000/udp
sudo ufw deny 3500/tcp
sudo ufw deny 8551/tcp
sudo ufw deny 4000/tcp
sudo ufw enable
sudo ufw allow 22
sudo ufw enable
```







