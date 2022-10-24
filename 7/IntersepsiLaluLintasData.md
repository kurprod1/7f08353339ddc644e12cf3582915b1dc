# Intersepsi Lalu Lintas Data Android dengan Burp

Created: June 22, 2022 1:17 PM

Sama dengan tahapan pada pertemuan sebelumnya dimana kita harus menginstal sertifikat Burp. Namun kali ini kita harus memasangnya di emulator android. Dengan intersepsi ini seorang security engineer dan penetration tester akan mampu melihat permintaan dan respon dari server dan aplikasi.

# **Memasang Sertifikat di Android**

Langkah pertama, kita perlu membangkitkan sertifikat secara manual. Hal ini diperlukan agar setiap lalu lintas data yang tertangkap Burp dengan sertifikat palsu bisa tetap terbaca dan dianggap sertifikat milik kita terverifikasi dan terpercaya.

```bash
$ mkdir certificates && cd certificates
$ sudo apt-get install openssl
$ cp /usr/lib/ssl/openssl.cnf ./
$ openssl req -x509 -days 730 -nodes -newkey rsa:2048 -outform der -keyout server.key -out ca.der -extensions v3_ca -config openssl.cnf
$ openssl rsa -in server.key -inform pem -out server.key.der -outform der
$ openssl pkcs8 -topk8 -in server.key.der -inform der -out server.key.pkcs8.der -outform der -nocrypt
```

Selanjutnya kita akan memasang sertifikat tersebut ke perangkat android, pastikan emulator sudah berjalan.

```bash
$ openssl x509 -inform DER -in ca.der -out ca.pem
$ openssl x509 -inform PEM -subject_hash_old -in ca.pem
$ filename=openssl x509 -inform PEM -subject_hash_old -in ca.pem | head -1
$ cp ca.pem ${filename}.0
$ adb remount
$ adb push ${filename}.0 /system/etc/security/cacerts/${filename}.0
$ adb shell chmod 644 /system/etc/security/cacerts/${filename}.0
```

Restart emulator android. Langkah terakhir bisa teman-teman periksa di menu trusted credentials. Berhubung dalam praktik ini Organization Name saya tulis **Cilsy** dan **FQDN** *.cilsy.id maka akan muncul seperti gambar dibawah ini. Mungkin akan berbeda jika kalian memasukan data berbeda saat membangkitkan sertifikat sebelumnya,

[https://lh4.googleusercontent.com/48aZ0rP2-YURw6_Qwsd5vgsjmILNLUqN2AFFW9D8n1XZkoMNCpM_hxRdBjp8KerafD017tm1P-0Lo4yfe8SWntrO-eOx6PhQeHxzHB1zmplyudj9uvF7cKOzcvIQbjsxlhXyyIIB0GwyOrLdx4rx7vJwdM4](https://lh4.googleusercontent.com/48aZ0rP2-YURw6_Qwsd5vgsjmILNLUqN2AFFW9D8n1XZkoMNCpM_hxRdBjp8KerafD017tm1P-0Lo4yfe8SWntrO-eOx6PhQeHxzHB1zmplyudj9uvF7cKOzcvIQbjsxlhXyyIIB0GwyOrLdx4rx7vJwdM4)

Gambar: Sertifikat terpasang dengan sempurna

# **Memasang Sertifikat di Burp**

Sertifikat yang kita bangkitkan harus kita masukkan ke dalam aplikasi Burp. Caranya kalian bisa membuka proxy settings dan pilih **Import / Export CA Certificate** > **Import** -> **Certificate and private key in DER format**.

[https://lh4.googleusercontent.com/T60QX9LzLr7Au77d4QZI2ssjbjPJkvAM7AhZER5v6YcEkBvswkcfEoVo9Q_Ak4-4jDabbniVOZyTWOKj0rdWL3N7eRoNYVbrW0jtQ7jk5xYJFX6A2xQwlnEiW0liYAhntdnkxZcuZnqw7ukHKIYk5uiZ8T8](https://lh4.googleusercontent.com/T60QX9LzLr7Au77d4QZI2ssjbjPJkvAM7AhZER5v6YcEkBvswkcfEoVo9Q_Ak4-4jDabbniVOZyTWOKj0rdWL3N7eRoNYVbrW0jtQ7jk5xYJFX6A2xQwlnEiW0liYAhntdnkxZcuZnqw7ukHKIYk5uiZ8T8)

# **Mengaktifkan Proxy Burp di Android**

Langkah terakhir diperlukan agar semua lalu lintas data akan dibelokkan ke aplikasi Burp agar kita bisa melakukan analisa lebih lanjut. Klik setting > WiFi > icon gear > icon edit > Advance options. Kemudian ganti Proxy **automatic** ke **manual** dan ganti Proxy Host dan port sesuai dengan IP dan port wifi kalian.

[https://lh6.googleusercontent.com/dWD8tv4nIaFB7AnnE-2J9utMsAYu_U4xoLnSgZJ9HjkvILPk5AP39HHxPmR4PJjnbJ_mItSXS0iF-MDOZyVQ1WHC9wim10tLkwfnixQg_ldbsK6VgVjbCxWN4H79hoE_uTJBIrv61kaGXh8Qozvm1HsH5zw](https://lh6.googleusercontent.com/dWD8tv4nIaFB7AnnE-2J9utMsAYu_U4xoLnSgZJ9HjkvILPk5AP39HHxPmR4PJjnbJ_mItSXS0iF-MDOZyVQ1WHC9wim10tLkwfnixQg_ldbsK6VgVjbCxWN4H79hoE_uTJBIrv61kaGXh8Qozvm1HsH5zw)

Agar konfigurasi bisa langsung aktif kalian harus mematikan wifi pada emulator android dan kemudian hidupkan kembali. Seharusnya setelah ini semua lalu lintas data akan muncul di aplikasi Burp.