# Persiapan Lab

Created: June 22, 2022 1:17 PM

Untuk pelatihan kali ini kita akan menggunakan beberapa program yang harus dipasang dan dipersiapkan sebelum pelatihan dimulai.

# **Perangkat Android**

- Genymotion
- Emulator android dengan root yang sudah tersedia
- Drozer (Pemasangan bisa mengikuti panduan di [https://github.com/FSecureLABS/drozer](https://github.com/FSecureLABS/drozer))
- Frida
- BurpSuite
- APKSigner (sudo apt install apksigner)

# **Aplikasi Android**

Sedangkan aplikasi untuk praktik peserta sebagai berikut :

[Untitled](Persiapan%20Lab%2048e43ed3d6c04e78bff3da9b0bdaf05b/Untitled%20Database%200935384f7c364bc88ccc5680e1bfa3d3.csv)

Semua aplikasi diatas diharuskan untuk dipasang pada emulator android kalian sebelum memulai pelatihan.

# **Mengambil APK dari Android**

Mengambil APK yang terpasang pada perangkat android

```bash
$ adb shell pm list packages 	# menampilkan daftar aplikasi yang terpasang
$ adb shell pm path com.example.id # mendapatkan lokasi APK
$ apk=`adb shell pm path com.example.id | head -1 | awk -F':' '{print $2}'`
$ adb pull $apk com.example.id.apk
```