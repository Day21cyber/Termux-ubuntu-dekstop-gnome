# Termux-ubuntu-dekstop-gnome

Berikut langkah-langkah untuk menginstal Ubuntu 18.04 di Termux dan mengaktifkan desktop GNOME:

1. **Memperbarui Repositori**:
   
   ```bash
   pkg update
   ```

2. **Instal Dependensi**:
   
   ```bash
   pkg install proot wget -y
   ```

3. **Unduh Skrip Instalasi Ubuntu**:
   
   ```bash
   wget https://raw.githubusercontent.com/MFDGaming/ubuntu-in-termux/master/ubuntu.sh
   ```

4. **Edit Skrip Instalasi**:
   
   ```bash
   nano ubuntu.sh
   ```

   Ganti versi Ubuntu ke "bionic", kemudian simpan dengan menekan CTRL+X, lalu Y, dan ENTER.

5. **Jalankan Skrip Instalasi Ubuntu**:
   
   ```bash
   bash ubuntu.sh
   ```

6. **Edit file startubuntu.sh**:
   
   ```bash
   nano startubuntu.sh
   ```

   Tambahkan baris berikut setelah `/dev`:
   
   ```bash
   command+=" -b /dev/null:/proc/sys/kernel/cap_last_cap"
   ```

   Simpan perubahan dengan menekan CTRL+X, lalu Y, dan ENTER.

7. **Mulai Ubuntu**:
   
   ```bash
   ./startubuntu.sh
   ```

8. **Memperbarui Repositori Ubuntu**:
   
   ```bash
   apt update
   ```

9. **Instal Gnome Desktop**:
   
   ```bash
   apt install gnome-shell gnome-terminal gnome-tweaks gnome-shell-extension-ubuntu-dock nautilus nano gedit dbus-x11 tigervnc-standalone-server -y
   ```

10. **Konfigurasi xstartup untuk Gnome**:
   
    ```bash
    mkdir ~/.vnc
    nano ~/.vnc/xstartup
    ```

    Tempelkan kode berikut:

    ```bash
    #!/bin/bash

    export XDG_CURRENT_DESKTOP="GNOME"
    service dbus start
    gnome-shell --x11
    ```

    Simpan perubahan dan berikan izin eksekusi:

    ```bash
    chmod +x ~/.vnc/xstartup
    ```

11. **Memulai VNC Server**:
    
    ```bash
    vncserver
    ```

    Pada saat pertama kali menjalankan, Anda akan diminta membuat kata sandi VNC yang akan digunakan saat terhubung ke server.

Setelah mengikuti langkah-langkah di atas, Anda seharusnya dapat menggunakan desktop GNOME di Ubuntu 18.04 yang dijalankan di Termux.
