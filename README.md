{Tahap Pembuatan}

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
Dan jika muncul perintah ketik y dan Enter saja


# 2 Download File via vps

geth
```
wget https://github.com/stratisproject/go-stratis/releases/download/0.1.1/geth-linux-amd64-5c4504c.tar.gz
```

beacon
```
wget https://github.com/stratisproject/prysm-stratis/releases/download/0.1.1/beacon-chain-linux-amd64-0ebd251.tar.gz
```

validator
```
wget https://github.com/stratisproject/prysm-stratis/releases/download/0.1.1/validator-linux-amd64-0ebd251.tar.gz
```

staking
```
wget https://github.com/stratisproject/staking-deposit-cli/releases/download/0.1.0/staking-deposit-cli-linux-amd64.zip
```

# 3 Extract semua filenya

Memakai unzip dan jika belum punya bisa install dulu melalui command

```
apt install unzip
```

Setelah usai lanjut extract

```
tar -xf geth-linux-amd64-5c4504c.tar.gz
rm -rf geth-linux-amd64-5c4504c.tar.gz
tar -xf beacon-chain-linux-amd64-0ebd251.tar.gz
rm -rf beacon-chain-linux-amd64-0ebd251.tar.gz
tar -xf validator-linux-amd64-0ebd251.tar.gz
rm -rf validator-linux-amd64-0ebd251.tar.gz
unzip staking-deposit-cli-linux-amd64.zip
```






