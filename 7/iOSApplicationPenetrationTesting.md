# iOS Application Penetration Testing

Created: June 22, 2022 1:17 PM

Penetration testing pada iOS memiliki poin-poin pengujian yang sama dengan android hanya saja kita harus beradaptasi dengan perbedaan OS tersebut. OWASP MSTG sudah memberikan gambaran lengkap mengenai bagaimana proses pengujian pada perangkat iOS. Namun disini kita akan membahas fundamental yang nanti akan membantu kalian memahami MSTG.

# **Static Analysis**

Pada metode ini kita akan menemukan kerentanan keamanan dengan menganalisis source code aplikasi iOS. Perlu kalian tahu untuk bagian ini kalian harus memasang terlebih dahulu aplikasi yang akan diuji melalui App Store.

Selanjutnya setelah pemasangan aplikasi iOS sudah dilakukan, kita akan men-decrypt aplikasi dan mengekspor ke dalam bentuk IPA. Berikut ini adalah step yang bisa kalian pelajari.

## ***Unencrypted iOS Application***

Menghubungkan terminal linux ke perangkat iOS

```bash
$ ssh root@<ios IP address>
```

Proses untuk mendapatkan daftar aplikasi yang sudah terpasang

```bash
ipainstaller -l
```

Pencadangan aplikasi yang terpasang ke dalam bentuk IPA

```bash
ipainstaller -b <package id>
```

Aplikasi yang berhasil dicadangkan akan tersimpan ke direktori **/private/var/mobile/Documents/**

Mengunduh IPA ke komputer

```bash
$ scp root@<ios IP address>:/private/var/mobile/Documents/<file name>.ipa <file name>.ipa
```

Dengan demikian kalian berhasil mengunduh file IPA, selanjutnya kita akan memulai proses analisa statis dengan membuka terminal dan masuk ke direktori dimana file IPA tersimpan.

```bash
$ mkdir static_analysis$ mv <file name>.ipa static_analysis$ cd static_analysis$ unzip <file name>.ipa
```

Nah setelah file IPA di extract akan muncul berbagai file dan direktori kalian bisa melakukan analisis secara manual. Tentunya untuk proses ini akan membutuhkan pengetahuan fundamental tentang iOS programming. Dan biasanya jika aplikasi dibangun menggunakan framework react native kalian sudah bisa menganalisis source code dari javascript.

## ***Unencrypted Binary iOS Application***

Sedangkan terkadang aplikasi iOS dibangun menggunakan bahasa native yang membuat file tersebut menjadi berbentuk binary dan tentunya hanya bisa dipahami oleh mesin itu sendiri. Untuk mengatasi kasus seperti ini kita harus melakukan proses decrypt dengan panduan dibawah ini.

```bash
$ class-dump-z <app name>
```

Ketika perintah diatas dijalankan akan muncul source code dalam bahasa pemrograman swift. Dan untuk proses analisa kerentanan bisa dilakukan dengan mempelajari alur program.

## ***Encrypted Binary IOS Application***

Beberapa aplikasi IOS menerapkan mitigasi reverse engineering dengan mengimplementasikan enkripsi untuk mempersulit kita melakukan analisa source code.

Proses decrypt:

```bash
$ clutch -d <app name>
```

Memunculkan class dump:

```bash
$ class-dump-z <app name>
```

# **Dynamic Analysis**

Di materi ini kita akan melakukan analisis dengan metode dinamis. Proses ini biasanya cukup mudah karena kita hanya perlu menjalankan fitur aplikasi atau memasang di perangkat iOS dan setelahnya kita hanya perlu mengamati perubahan atau respon apa yang terjadi.

## ***Application Storage Analysis***

Pertama kita siapkan terlebih dahulu aplikasi DVIA yang menjadi target evaluation kita.

```bash
$ ssh root@<ip ios device>
$ cd /tmp
$ wget https://github.com/prateek147/DVIA-v2/releases/download/v2.0/DVIA-v2-swift.ipa
$ ipainstaller DVIA-v2-swift.ipa
```

Terkadang penggunaan ipainstaller untuk iOS terbaru sering gagal. Hal ini bisa kalian abaikan jika aplikasi target evaluation merupakan tipe production yang bisa dipasang melalui App Store. Dalam hal ini pemasangan aplikasi iOS dilakukan dengan cara normal yakni memasang via App Store.

Lokasi penyimpanan lokal pada iOS biasanya berada di :

```bash
/var/mobile/Containers/Data/Application/<Linkedin-GUID>
```

Perlu teman-teman ketahui ketika aplikasi berhasil terpasang, semua data tersimpan didalamnya baik itu cache hingga penyimpanan seperti username dan password (jika aplikasi memiliki fitur penyimpanan kredensial). Terkadang token pun bisa juga tersimpan di direktori ini.

Dan Linkedin-GUID pada lokasi diatas merupakan hash yang unik pada setiap aplikasi. Sebagai contoh kalian bisa mendapatkan Linkedin-GUID dari aplikasi Instagram menggunakan perintah berikut.

```bash
$ cd /var/mobile/Containers/Data/Application/
$ find . -name Instagram
./23BFE771-229E-4B94-A46A-031C6A0FD84B/Library/Application Support/Instagram
```

Dan ketemu Linkedin-GUID nya adalah 23BFE771-229E-4B94-A46A-031C6A0FD84B. Selanjutnya kita periksa apakah ada data sensitif didalamnya dengan analisis manual. Sebagai contoh pada kasus Instagram cookie tersimpan secara plaintext di folder **Linkedin-GUID/Library/Cookies** dan selain itu penyimpanan data lokal lainnya juga terdapat di **Linkedin-GUID/Library/Preferences**.

## ***Network Traffic Analysis***

Pada bagian ini teknik yang digunakan untuk melakukan analisis jaringan sama persis dengan yang sudah kita lakukan pada android penetration testing sebelumnya. Dengan penggunaan Burp Suite kita sudah bisa untuk mengidentifikasi permintaan dan respon apa yang dilakukan aplikasi tersebut. Yang berbeda pada iOS ketika aplikasi memiliki teknik SSL Pinning. Tentu ini berbeda dalam proses untuk meloloskan perimeter keamanan tersebut.

Biasanya penulis untuk meloloskan SSL pinning pada iOS menggunakan SSL Kill Switch 2 yang bisa dipasang melalui Cydia. Dan apabila tidak bisa barulah menggunakan Objection.

Untuk menjalankan Objection pastikan frida-server sudah berjalan diperangkat iOS. Kalian bisa mengikuti panduan ini ([https://blog.attify.com/bypass-jailbreak-detection-frida-ios-applications/](https://blog.attify.com/bypass-jailbreak-detection-frida-ios-applications/)).

Setelah terpasang pastikan frida berjalan dengan baik melalui perintah berikut :

```bash
$ frida-ps -Uia
```

Lalu kita jalankan objection.

```bash
$ objection --gadget "com.apple.AppStore" explore> ios sslpinning disable
```