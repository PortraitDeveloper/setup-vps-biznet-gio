# Pendahuluan

Ini adalah dokumentasi yang memberikan panduan langkah demi langkah cara melakukan setup SSH key untuk mengakses VPS.

# Langkah-Langkah

## Berlangganan VPS

1. Berlangganan layanan VPS dan buat akun. Pada dokumentasi ini menggunakan layanan VPS [Biznet Gio Cloud](https://www.biznetgio.com/)
2. Di bagian _sidebar_ klik _Compute_, lalu pilih _NEO Lite_
3. Klik _create new_, lalu isi _form_

## Aktifkan Akses Password Authentication

```bash
sudo su
```

```bash
sudo nano /etc/ssh/ssh_config
```

**Instruksi:**

1. Ubah PasswordAuthentication no menjadi PasswordAuthentication yes seperti gambar dibawah ini
2. Tekan CTRL + x
3. Kemudian muncul pesan seperti ini -> (If prompted with "Save modified buffer?"), tekan Y, lalu tekan Enter untuk menyimpan

## Konfigurasi Authorized Keys untuk Menggunakan Kunci Publik

```bash
chmod g-w /home/user
chmod 700 /home/user/.ssh
chmod 600 /home/user/.ssh/authorized_keys
```

## Membuat SSH Key di Lokal

```bash
ssh-keygen
```

Menampilkan SSH Public Key

```bash
cat ~/.ssh/id_rsa.pub
```

copy-paste ke Biznet Gio di bagian SSH Key

## Remote VPS

Open terminal

```bash
ssh <USERNAME>@<HOST OR IPADDRESS> -p 22
```

## Melihat Spesifikasi dan Benchmark VPS

```bash
wget -q0- bench.sh | bash
```

## Speedtest Koneksi Internet

```bash
sudo apt-get install curl
curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash
sudo apt-get install speedtest
```

## Method-2

1. Download sshkeyfile.pem
2. Put in some directory
3. cd directory

Akses VPS Via Terminal

```bash
ssh -i <sshkeyfile.pem> <SERVICE NAME OR USERNAME>@<HOST OR IPADDRESS>
```

Jika tidak bisa akses, jalankan perintah berikut:

```bash
rm -f /Users/dmu/.ssh/known_hosts
```

# Referensi
