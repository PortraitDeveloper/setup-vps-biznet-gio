# Pendahuluan

Ini adalah dokumentasi yang memberikan panduan langkah demi langkah _setup_ dan _remote_ VPS Biznet Gio Cloud via terminal dengan cara _\_metode-2 IMPORT SSH KEY_\_.

# Langkah-Langkah

1.  Buat akun [Biznet Gio Cloud](https://www.biznetgio.com/)
2.  Setelah masuk ke halaman, di bagian _sidebar_ klik _Compute_, lalu pilih _NEO Lite_
3.  Klik _CREATE NEW_, lalu isi _form_
4.  Pada bagian _SSH Key_ pilih _IMPORT SSH KEY_
5.  Beralih ke perangkat lokal Anda, lalu buka terminal
6.  Buat SSH Key

    ```bash
    ssh-keygen
    ```

7.  Menampilkan SSH Public Key

    ```bash
    cat ~/.ssh/id_rsa.pub
    ```

    _Petunjuk: *Copy* SSH Public Key_

8.  Beralih ke halaman _form_ Biznet Gio, lalu _paste_ SSH Public Key yang telah dibuat
9.  Jika sudah mengisi _form_ dan sudah yakin klik _NEXT_, lalu lakukan pembayaran
10. Beralih ke halaman _Dashboard_, lalu klik nama service VPS yang ada telah dibuat
11. Beralih ke halaman _NEO Lite_, lalu klik _OPEN CONSOLE_ untuk mengakses konsol atau terminal bawaan VPS Biznet Gio
12. Masukan _username_ dan _password_
13. Update sistem

    ```bash
    sudo apt update
    ```

14. Aktifkan akses _Password Authentication_ (Opsional)
    **Petunjuk: Jika Anda tidak ingin ada autentikasi setiap mengakses VPS lewati langkah ini**

    ```bash
    sudo su
    sudo nano /etc/ssh/ssh_config
    ```

    **Instruksi:**

        1. Ubah PasswordAuthentication no menjadi PasswordAuthentication yes seperti gambar dibawah ini
        2. Tekan CTRL + x
        3. Kemudian muncul pesan seperti ini -> (If prompted with "Save modified buffer?"), tekan Y, lalu tekan Enter untuk menyimpan

15. Konfigurasi _Authorized Keys_ untuk Menggunakan Kunci Publik (Opsional)

    ```bash
    chmod g-w /home/user
    chmod 700 /home/user/.ssh
    chmod 600 /home/user/.ssh/authorized_keys
    ```

16. Tutup konsol Biznet Gio, lalu beralih lagi ke perangkat lokal, kemudian buka terminal
17. Buka koneksi SSH

    ```bash
    ssh <USERNAME>@<HOST OR IPADDRESS>
    ```

18. Melihat _benchmark_ dan spesifikasi VPS (Opsional)

    ```bash
    wget -q0- bench.sh | bash
    ```

19. Test kecepatan koneksi internet (Opsional)

    ```bash
    sudo apt-get install curl
    curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash
    sudo apt-get install speedtest
    ```