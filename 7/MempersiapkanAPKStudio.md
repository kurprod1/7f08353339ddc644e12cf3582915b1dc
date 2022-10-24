# Mempersiapkan APK Studio

Created: June 22, 2022 1:17 PM

Mungkin ini menjadi materi baru dari kalian mengenai software APK Studio. Aplikasi ini akan membantu kita untuk merekayasa balik aplikasi yang istilah kerennya ***reverse engineering***. Ini dapat melakukan decompile APK ke bentuk yang hampir asli dan membangunnya kembali setelah melakukan beberapa modifikasi. Istilah kerennya adalah ***cracking*** atau ***patching*.** Jika teman-teman menggunakan windows pasti pernah menggunakan istilah cracking pada aplikasi yang berbayar sehingga bisa dijalankan secara gratis. Nah, seperti itulah cara kerjanya

Dalam proyek mobile app penetration testing, teknik ini bisa kita gunakan untuk melakukan analisis statis secara Black Box. Lebih jelasnya, meski kita menggunakan Black Box kita bisa melakukan decompile APK agar kita bisa merubahnya ke bentuk source code kembali. Dari situ kita akan mudah dalam mengidentifikasi kerentanan dengan membaca source code tersebut.

Sebelum kita membahas lebih dalam mempelajari teknik reverse engineering. Teman-teman perlu menyiapkan terlebih dahulu lab untuk pengujian. Pertama, kalian harus mempersiapkan APK Studio, jalankan perintah dibawah ini dalam OS Linux kalian.

Install Java JRE dan JDK

```bash
$ sudo add-apt-repository ppa:linuxuprising/java
$ sudo apt-get update
$ sudo apt-get install oracle-java11-installer-local
$ sudo apt-get install oracle-java11-set-default-local
```

Install Qt

```bash
$ sudo add-apt-repository ppa:beineri/opt-qt-5.12.3-xenial
$ sudo apt update
$ sudo apt install libgl1-mesa-dev qt512base
```

Apabila Anda menggunakan OS Linux lain, silakan baca dokumentasi instalasi QT di link berikut [https://doc.qt.io/qt-5/linux.html](https://doc.qt.io/qt-5/linux.html)

Install APK Studio

```bash
$ wget https://github.com/vaibhavpandeyvpz/apkstudio/releases/download/5.2.3/ApkStudio-5.2.3-x86_64.AppImage
$ mv ApkStudio-5.2.3-x86_64.AppImage /usr/bin/apkstudio
$ chmod +x /usr/bin/apkstudio
```

Download APK Tool

```bash
$ wget https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.4.1.jar
```

Install Jadx

```bash
$ brew install jadx
```

Download Uber APK Signer

```bash
$ wget https://github.com/patrickfav/uber-apk-signer/releases/download/v1.1.0/uber-apk-signer-1.1.0.jar
```

Untuk menjalankan APK Studio kalian bisa menggunakan perintah **apkstudio** di terminal linux. Lalu jika sudah bisa dijalankan, kalian mengatur lokasi semua program yang sudah kalian download pada menu setting di APK Studio. Berikut contoh konfigurasinya :

[https://lh6.googleusercontent.com/GpZRh1UdzqdTKK1rlGuL8dC2Lg9PuBg_NuK2Rf8D0zPtvcSzDkOr9nL7YbK5mUubo3h0oQVG0BPmCaboyuj_YGETZnZoPmSxvLQPiNc9O5WiLbPL07WyqkqrauAlN-1bZtq-rTv424PU8shW55fD6U_4n44](https://lh6.googleusercontent.com/GpZRh1UdzqdTKK1rlGuL8dC2Lg9PuBg_NuK2Rf8D0zPtvcSzDkOr9nL7YbK5mUubo3h0oQVG0BPmCaboyuj_YGETZnZoPmSxvLQPiNc9O5WiLbPL07WyqkqrauAlN-1bZtq-rTv424PU8shW55fD6U_4n44)