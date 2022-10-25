# HTTP Fuzzing

Jika kalian sudah mampu mengidentifikasi port dan jenis service pada materi sebelumnya. Nah di materi ini kita akan mencoba mengidentifikasi apakah terdapat error pada aplikasi yang nanti akan menyebabkan terganggunya availability.

Sebelum masuk ke materi teknis, apabila kalian masih belum terbiasa dengan HTTP Request Header akan bagus jika kalian membaca bahan bacaan berikut.

[HTTP - Header Fields](https://www.tutorialspoint.com/http/http_header_fields.htm)

Tool yang akan kita gunakan adalah sfuzz yang umumnya sudah terpasang di Kali Linux.  Sedangkan lokasi template data fuzzing untuk aplikasi sfuzz berada di /usr/share/sfuzz-db.

Jika kita amati pada basic.http kurang lebih isinya seperti berikut :

```bash
ls /usr/share/sfuzz-db/
total 120
-rwxr-xr-x 1 root root  4683 Nov 25  2015 bad-nums.blocks.inc
-rwxr-xr-x 1 root root  3222 Nov 25  2015 basic.a11
-rwxr-xr-x 1 root root   195 Nov 25  2015 basic.cmd
-rwxr-xr-x 1 root root  1249 Nov 25  2015 basic.cvs
-rwxr-xr-x 1 root root  1391 Nov 25  2015 basic-fuzz-strings.list
-rwxr-xr-x 1 root root  1890 Nov 25  2015 basic.http
-rwxr-xr-x 1 root root   847 Nov 25  2015 basic.http.blocks
-rwxr-xr-x 1 root root   743 Nov 25  2015 basic.nuke
-rwxr-xr-x 1 root root   946 Nov 25  2015 basic.pop3
-rwxr-xr-x 1 root root  1183 Nov 25  2015 basic.rtsp
-rwxr-xr-x 1 root root  1000 Nov 25  2015 basic.smtp
-rwxr-xr-x 1 root root	52 Nov 25  2015 basic.unknown
-rwxr-xr-x 1 root root  4589 Nov 25  2015 big-ant.0day
-rwxr-xr-x 1 root root  1218 Nov 25  2015 http-etc-enumeration.list
-rwxr-xr-x 1 root root	72 Nov 25  2015 http-nuke-enumeration.list
-rwxr-xr-x 1 root root   267 Nov 25  2015 php-vuln.test
-rwxr-xr-x 1 root root 12086 Nov 25  2015 server.basic.http
-rwxr-xr-x 1 root root  2191 Nov 25  2015 server.browser-fuzz.blocks
-rw-r--r-- 1 root root  5848 Nov 25  2015 sfuzz-plugin-example.so
-rw-r--r-- 1 root root  8144 Nov 25  2015 sfuzz-server-plugin.so
-rwxr-xr-x 1 root root  2300 Nov 25  2015 smb.0day
-rwxr-xr-x 1 root root  2421 Nov 25  2015 std-cmdline-exploits.list
-rwxr-xr-x 1 root root  1186 Nov 25  2015 twitter.cfg
-rwxr-xr-x 1 root root  2403 Nov 25  2015 vulnerable-echo-server.c
```

Jika kita amati pada basic.http kurang lebih isinya seperti berikut :

```bash
$ cat /usr/share/sfuzz-db/basic.http

sequence=%n
sequence=%f
sequence=%%n
. . .

GET /FUZZ HTTP/1.0

--
```

Penggunaan tanda FUZZ mengindikasikan posisi sampel data fuzzing ditempatkan. Artinya jika kalian ingin menempatkan FUZZ pada user-agent seharusnya contoh template-nya akan seperti ini :

```bash
GET / HTTP/1.1
User-Agent: FUZZ

--
```

Selanjutnya kita akan menggunakan sfuzz untuk mendeteksi apakah ada kerentanan pada aplikasi dengan perintah berikut :

```bash
$ sfuzz -S vuln.cilsy.id -p 31335 -T -f /usr/share/sfuzz-db/basic.http > report.txt
```