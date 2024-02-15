
# Stratis-Node
Tutorial Stratis Node

## Bahan

- VPS
- Termius (HP) ataupun yang lainnya
- Mobaterm X (PC) ataupun yang lainnya

## RPC

Network Name 
```
Auroria
```
RPC URL 
```
https://auroria.rpc.stratisevm.com
```
CID 
```
205205
```
Symbol 
```
STRAX
```
Explorer 
```
https://auroria.explorer.stratisevm.com
```


## Tutorial

# 1. Setting vps

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

# 4 Running NODE

Pertama buat screen dulu untuk bisa jalankan secara background geth

```
screen -Rd geth
```
Setelah muncul tampilan baru copas kode dibawah untuk run node nya
```
./geth --auroria --http --http.api eth,net,engine,admin --datadir=data\testnet\geth --authrpc.addr=127.0.0.1 --authrpc.jwtsecret=jwtsecret --syncmode=full
```
Setelah run tekan pada keyboard CTRL + A + D untuk minimize screen biar masih berjalan secara background

Selanjutnya untuk RUN Beacon buat screen dulu
```
screen -Rd beacon
```
Copas 
```
./beacon-chain --auroria --datadir=data\testnet\beacon --execution-endpoint=http://localhost:8551 --jwt-secret=jwtsecret
```
Jika muncul prompt untuk "accept" ketikan accept dan Enter

Setelah run tekan pada keyboard CTRL + A + D untuk minimize screen biar masih berjalan secara background

# 5 Setting Wallet

Masuk ke folder
```
cd staking-deposit-cli-linux-amd64/
```
Extract
```
tar -xf staking-deposit-cli-linux-amd64.tar.gz
```
Edit Address Masukan Address EVM kalian
```
./deposit new-mnemonic --num_validators=1 --mnemonic_language=english --chain=auroria --eth1_withdrawal_address=ADDRESS KALIAN
```

```env
Pilih bahasa ketikan angka dan Enter
Masukan addres yang sama 
Buat password minimal 8
Konfirmasi Password
Simpan mnemonicnya yang muncul
Jika sudah tekan keyboard bebas
Masukan mnemonic yang telah disimpan
Done
```

Masuk ke folder
```
cd validator_keys
```
- Download file deposit_dataxxxx.json ke hp atau pc
- Done

# 6 Register di Web dan Upload file deposit data

Fuaucet terlebih dahulu
```
https://auroria.faucet.stratisevm.com/
```

Buka Browser
```
https://auroria.launchpad.stratisevm.com/en/overview
```
- Centang, next.sampai deposit
- Upload file deposit yang sudah di download dari vps ke browser.
- Connect wallet
- Centang semua, continue
- Confirm deposit

# 7 Setting Validator

Buka vps
kembali ke folder root
```
cd
```

Edit bagian letak keystore kalian dan hapus tanda <>
```
./validator accounts import --keys-dir=<letak-keystore-kalian> --auroria
```
contoh
```
./validator accounts import --keys-dir=/root/staking-deposit-cli-linux-amd64/validator_keys --auroria
```
Ketika muncul seperti dibawah
```
Enter a wallet directory (default: /root/.eth2validators/prysm-wallet-v2):
```
Copy lokasi default wallet tersebut untuk digunakan run validator
- Tekan Enter saja dan masukan password

# 8 Run Validator

Jalankan screen terlebih dahulu

```
screen -Rd validator
```

Edit commandnnya dan hapus <> isi letak wallet default yang sudah disetting di Validator dan address wallet kalian
```
./validator --wallet-dir=<letak-wallet-kalian> --auroria --suggested-fee-recipient=<address-wallet-kalian>
```
contoh
```
./validator --wallet-dir=/root/.eth2validators/prysm-wallet-v2 --auroria --suggested-fee-recipient=0x......
```
Setelah run tekan pada keyboard CTRL + A + D untuk minimize screen biar masih berjalan secara background


# DONE

# Sementara ini saja, next info jika update akan saya share di [x](https://x.com/vegardian)


{Jika ada kesalahan harap dimaklumi karena newbie :D }

