# Pendahuluan

Ini adalah dokumentasi yang memberikan panduan langkah demi langkah _setup_ dan _remote_ VPS Biznet Gio Cloud via terminal dengan cara _\_metode-1 CREATE SSH KEY_\_.

# Langkah-Langkah

1.  Buat akun [Biznet Gio Cloud](https://www.biznetgio.com/)
2.  Setelah masuk ke halaman, di bagian _sidebar_ klik _Compute_, lalu pilih _NEO Lite_
3.  Klik _CREATE NEW_, lalu isi _form_
4.  Pada bagian _SSH Key_ pilih _CREATE SSH KEY_, lalu berikan nama file SSH Key
5.  klik _CREATE_, lalu file SSH otomatis terunduh, ekstensi file SSH adalah _*.pem*_
6.  Jika sudah mengisi _form_ dan sudah yakin klik _NEXT_, lalu lakukan pembayaran
7.  Beralih ke halaman _Dashboard_, lalu klik nama service VPS yang ada telah dibuat
8.  Beralih ke halaman _NEO Lite_, lalu klik _OPEN CONSOLE_ untuk mengakses konsol atau terminal bawaan VPS Biznet Gio
9.  Masukan _username_ dan _password_
10. Update sistem

    ```bash
    sudo apt update
    ```

11. Aktifkan akses _Password Authentication_ (Opsional)
    **Petunjuk: Jika Anda tidak ingin ada autentikasi setiap mengakses VPS lewati langkah ini**

    ```bash
    sudo su
    sudo nano /etc/ssh/ssh_config
    ```

    **Instruksi:**

        1. Ubah PasswordAuthentication no menjadi PasswordAuthentication yes seperti gambar dibawah ini
        2. Tekan CTRL + x
        3. Kemudian muncul pesan seperti ini -> (If prompted with "Save modified buffer?"), tekan Y, lalu tekan Enter untuk menyimpan

12. Tutup konsol Biznet Gio, lalu Kembali lagi ke perangkat lokal anda
13. Buatlah sebuah direktori, lalu pindahkan file SSH berekstensi _*.pem*_ ke direktori tersebut
14. Buka terminal, lalu arahkan ke direktori yang telah dibuat

    ```bash
    cd /path/to/directory
    ```

15. Buka koneksi menggunakan file SSH

    ```bash
    ssh -i <SSHKey.pem> <SERVICE NAME OR USERNAME>@<HOST OR IPADDRESS>
    ```

16. Melihat _benchmark_ dan spesifikasi VPS (Opsional)

```bash
wget -q0- bench.sh | bash
```

17. Test kecepatan koneksi internet (Opsional)

```bash
sudo apt-get install curl
curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash
sudo apt-get install speedtest
```
