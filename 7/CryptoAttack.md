# Crypto Attack

Created: June 22, 2022 1:17 PM

Serangan yang bisa kita lakukan pada kriptografi sebenarnya ada banyak sekali seperti :

1. Known plaintext attack
2. Chosen plaintext attack
3. Side-channel attack
4. Collision attack
5. Dan sebagainya

Referensi mengenai teknik serangan kriptografi bisa kalian buka disini [https://s.id/l15rX](https://s.id/l15rX)

Nah, dari sekian banyak teknik hampir semua serangan dilakukan berbasis matematika. Namun pada pertemuan yang sangat pendek ini kita pelajari teknik yang paling mudah yakni dengan melakukan memory dump attack untuk mendapatkan sandi enkripsi dan brute force untuk mendapatkan plaintext dari hash.

1. **Memory Dump Attack**

Teori singkatnya bahwa apa saja program yang berjalan selalu akan disimpan di dalam RAM tidak terkecuali kunci yang kalian ketik pada aplikasi. Sebagai contoh kali ini kita akan mendapatkan kunci dari suatu aplikasi android [https://play.google.com/store/apps/details?id=com.dewdrop623.androidcrypt&hl=en](https://play.google.com/store/apps/details?id=com.dewdrop623.androidcrypt&hl=en)

Kalian bisa persiapkan aplikasi tersebut di emulator android kalian. Pastikan kalian sudah memiliki akses root.

[https://lh4.googleusercontent.com/COWHKaY2wb-x76DdNutbZig_N9oMqPtT16wrGAfQkyAWfAjRNPGeyHniWH_Sv2HJYavIY5X4GuOw2u_q1x2q2nOFM8a4Aud7dGYhXdhnzMOjCGOT6JIaPMYpajqUdoc049Zg-HB0WFIvgKyQiwKYBIQJV9g](https://lh4.googleusercontent.com/COWHKaY2wb-x76DdNutbZig_N9oMqPtT16wrGAfQkyAWfAjRNPGeyHniWH_Sv2HJYavIY5X4GuOw2u_q1x2q2nOFM8a4Aud7dGYhXdhnzMOjCGOT6JIaPMYpajqUdoc049Zg-HB0WFIvgKyQiwKYBIQJV9g)

Selanjutnya kita akan mencoba mendapatkan kunci tersebut di dalam memory :

```bash
$ adb root on
$ wget https://github.com/friendlyJLee/pmdump/raw/master/pmdump_prebuilt_bin/pmdump.android.arm

$ adb push pmdump.android.arm /data/local/tmp/pmdump
$ adb shell chmod +x /data/local/tmp/pmdump
$ adb shell
$ cd /data/local/tmp
$ pid=`ps -A | grep androidcrypt | awk '{print $2}'`
$ ./pmdump +r +w -x +p $pid
```

Setelah perintah diatas dijalankan kalian bisa memeriksa apakah **inipasswordsaya** terdapat didalam memori RAM atau tidak dengan perintah berikut :

```bash
$ strings output_pmdump.bin  | grep inipasswordsaya                                     	 
inipasswordsaya
inipasswordsaya
```

Hasilnya password ternyata tersimpan dalam memori.

1. **Hash Brute Force Attack**

Materi ini kita akan membahas penggunaan teknik brute-force untuk mendapatkan plaintext dari suatu hash. Ada banyak tool yang bisa kita gunakan salah satunya adalah hashcat. Hashcat memiliki fitur untuk brute-force dengan menggunakan Graphic Card sehingga prosesnya bisa lebih cepat dari CPU.

Untuk memeriksa kecepatan brute-force kita bisa gunakan :

```bash
$ hashcat -b
```

Dan untuk proses brute-force kita bisa lakukan dengan perintah berikut :

```bash
$ echo -e "admin" | sha1sum | awk '{print $1}' > hash.txt
$ hashcat -m 100 hash.txt /usr/share/wordlists/sqlmap.txt
```