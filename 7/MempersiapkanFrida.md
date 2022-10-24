# Mempersiapkan Frida

Created: June 22, 2022 1:17 PM

Frida merupakan aplikasi yang bekerja dalam membantu kita melakukan analisis secara dinamis. Tool ini akan menginjeksi aplikasi dengan intruksi atau script dengan dukungan banyak bahasa pemrograman seperti Python, NodeJS, dan lain-lain.

1. **Memasang Frida Server pada Android**

Frida Server merupakan tool agent yang perlu dijalankan di device yang menjadi target of evaluation kita. Jika kita ingin melakukan mobile app penetration testing maka frida server harus dijalankan di perangkat android tentunya dengan permission **root**.

Karena emulator android yang kita gunakan menggunakan arsitektur i686 atau mudahnya menggunakan prosessor intel / amd maka kita gunakan frida-server yang sesuai.

```bash
$ wget https://github.com/frida/frida/releases/download/12.8.20/frida-server-12.8.20-android-x86.xz
```

```bash
$ xz -d frida-server-12.8.20-android-x86.xz
$ adb push frida-server-12.8.20-android-x86 /data/local/tmp
$ adb shell chmod +x /data/local/tmp/frida-server-12.8.20-android-x86
$ adb shell

$ cd /data/local/tmp
$ ./frida-server-12.8.20-android-x86
```

Setelah kalian menjalankan perintah diatas, biarkan terminal tersebut tetap aktif. Dan lanjutkan proses berikutnya dengan terminal baru.

# **Memasang Frida Client pada Host OS**

Frida client ini adalah sebuah tool yang dijalankan di komputer pentester guna untuk menyuntikkan kode atau instruksi tertentu untuk merubah alur dari program ataupun aksi lain guna membantu pentester menganalisis aplikasi. Melanjutkan dari materi sebelumnya kali ini kita akan melakukan instalasi terlebih dahulu.

Pastikan anda membuka terminal baru, lalu ketik perintah berikut :

```bash
$ sudo python -m pip install frida-tools
$ frida-ps -U
 PID  Name
----  -----------------------------------------------
 147  adbd
 824  android.ext.services
 326  android.hardware.audio@2.0-service
 327  android.hardware.camera.provider@2.4-service
 331  android.hardware.cas@1.0-service
```

Perintah **frida-ps -U** untuk mendapatkan daftar aplikasi yang berjalan pada perangkat android kita. Jika tidak muncul daftar aplikasi tersebut, maka bisa diasumsikan bahwa frida-server tidak berjalan semestinya.