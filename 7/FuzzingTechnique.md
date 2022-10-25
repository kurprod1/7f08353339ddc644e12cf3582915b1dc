# Fuzzing Technique

Untuk lab kali ini disediakan beberapa target pada domain vuln.cilsy.id dengan port sebagai berikut :

1. 31335
2. 31336
3. 31337
4. 31338

Semua port di atas **tidak diketahui** jenis service apa yang berjalan sehingga kalian dituntut untuk mampu **mengidentifikasi** baik secara manual maupun secara otomatis.

Pada materi ini instruktur akan memberikan contoh teknik fuzzing dengan skenario HTTP (port 31335) dan FTP (port 31336). Meskipun sudah kita beritahukan mengenai jenis service pada port tersebut akan lebih baik jika kita mengidentifikasi sesuai dengan tahapan penetration testing yang benar.

```bash
nmap -p31335,31336 -sT -sV vuln.cilsy.id

31335/tcp open  unknown
31336/tcp open  unknown
```

Dari hasil pemindaian port diatas kita bisa dapatkan bahwa port 31335 dan 31336 tidak dikenal. Kita bisa menggunakan curl untuk memastikan apakah dua port diatas merupakan webserver dengan perintah berikut :

```bash
curl http://vuln.cilsy.id:31335

<html>
	<**head**>
		<**title**>404 Not Found</**title**>
	</**head**>
	<**body**>
		<**h1**>URL not found</**h1**>
	</**body**>
</**html**>
```

Dari hasil diatas sudah bisa dipastikan port 31335 adalah webserver, hal ini bisa kita lihat dari respon berupa HTML.

```bash
curl http://vuln.cilsy.id:31336

curl: (1) Received HTTP/0.9 when not allowed
```

Pada port 31336 tidak merespon HTML justru memberikan respon yang tidak memberikan informasi jelas. Hal yang bisa kita lakukan untuk identifikasi paling sederhana adalah menggunakan nc atau telnet langsung pada port 31336. Jika beruntung server yang tidak diketahui tersebut memberikan informasi.

```bash
telnet vuln.cilsy.id 31336

Trying vuln.cilsy.id...
Connected to vuln.cilsy.id.
Escape character is '^]'.
220 A very warm welcome!
```

Akhirnya! Server memberikan respon, tapi menarik ada kode 220 pada responnya. Kita bisa menggunakan google untuk memastikan kode apakah 220 itu.

![](https://lh5.googleusercontent.com/TuL3FwQkzEvCnHOROHoA9ZO9qnHXENVymRr1GXZPfsTzkfEIkIsBSgiDCghoB1Mc-61MdGKdiT5ec7MKzepiSs7z316Tuc8qfI7X4nuPrt7I8FAdPOd0-mOAKDw7unIClFLeRPiy78G0niBJHuVJGq7mURc)

Dan ternyata memang benar bahwa kode 220 merupakan respon dari FTP Server. Dengan demikian seharusnya kita bisa menghubungkan ke port 31336 dengan perintah ftp biasa.

```bash
ftp vuln.cilsy.id 31336

Connected to vuln.cilsy.id.
220 A very warm welcome!
Name (vuln.cilsy.id:cilsy): anonymous
331 User name okay, need password
Password:
230 Login successful
ftp>
```

Benar bukan ? Kita bisa menghubungkannya dengan perintah ftp biasa.