# CORS Example Scenario


# Simple Request

Misalnya, konten web di [https://foo.example](https://foo.example/) ingin memanggil konten di domain [https://bar.other](https://bar.other/). Kode semacam ini dapat digunakan dalam JavaScript yang digunakan di foo.example:

```jsx
const xhr = new XMLHttpRequest();
const url = '[https://bar.other/resources/public-data/](https://bar.other/resources/public-data/)';
xhr.open('GET', url);
xhr.onreadystatechange = someHandler;
xhr.send();
```

![Untitled](CORS%20Example%20Scenario%20fe895440953642ef93d3a27df27f81a5/Untitled.png)

Request yang diberikan dari client ke server adalah seperti ini

```
GET /resources/public-data/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example

```

Bisa kita lihat **Origin** dari request tadi adalah **https://foo.example**.

Response dari server akan seperti ini

```
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 00:23:53 GMT
Server: Apache/2
Access-Control-Allow-Origin: *
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: application/xml

[…XML Data…]

```

Ini terjadi karena Header dari server mengizinkan adanya sharing resource dari origin manapun ditandai dengan header **Access-Control-Allow-Origin: ***.

Jika server hanya mengizinkan domain tertentu untuk sharing resource, maka origin harus didefine dalam header. Misalnya hanya mengizinkan domain [https://foo.example](https://foo.example/).

```bash
Access-Control-Allow-Origin: https://foo.example

```

# Preflight Request

Tidak seperti simple request, browser terlebih dahulu mengirimkan permintaan HTTP menggunakan metode OPTIONS ke resource di origin lain, untuk menentukan apakah permintaan sebenarnya aman untuk dikirim. Permintaan cross-origin seperti itu telah di-preflight karena mungkin memiliki implikasi terhadap data pengguna.

Contoh request nya seperti ini

```jsx
const xhr = new XMLHttpRequest();
xhr.open('POST', 'https://bar.other/resources/post-here/');
xhr.setRequestHeader('X-PINGOTHER', 'pingpong');
xhr.setRequestHeader('Content-Type', 'application/xml');
xhr.onreadystatechange = handler;
xhr.send('<person><name>Arun</name></person>');

```

Contoh di atas membuat payload XML untuk dikirim dengan method POST. Juga, ditambahkan header HTTP X-PINGOTHER. Header tersebut bukan bagian dari HTTP/1.1, tetapi umumnya berguna untuk aplikasi web. Karena permintaan menggunakan Content-Type adalah  application/xml, dan karena ada header khusus, permintaan ini di-preflight.

![Untitled](CORS%20Example%20Scenario%20fe895440953642ef93d3a27df27f81a5/Untitled%201.png)

Request preflight akan menghasilkan response seperti ini.

```
OPTIONS /doc HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type

HTTP/1.1 204 No Content
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Vary: Accept-Encoding, Origin
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
```

Ada yang menarik dari request diatas yaitu header OPTIONS.

```
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```

Header **Access-Control-Request-Method** memberi tahu server sebagai bagian dari request preflight bahwa ketika permintaan sebenarnya dikirim, itu akan melakukannya dengan metode  POST. 

Header **Access-Control-Request-Headers** memberi tahu server bahwa ketika permintaan sebenarnya dikirim, itu akan dilakukan dengan header custom X-PINGOTHER dan Content-Type. Sekarang server memiliki kesempatan untuk menentukan apakah dapat menerima permintaan dalam kondisi ini.

Ketika preflight sudah dilakukan, dan ternyata request dapat diterima oleh server, maka client akan mengirim request yang sebenarnya kepada server.

```
POST /doc HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
X-PINGOTHER: pingpong
Content-Type: text/xml; charset=UTF-8
Referer: https://foo.example/examples/preflightInvocation.html
Content-Length: 55
Origin: https://foo.example
Pragma: no-cache
Cache-Control: no-cache

<person><name>Arun</name></person>

HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:40 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 235
Keep-Alive: timeout=2, max=99
Connection: Keep-Alive
Content-Type: text/plain

[Some XML payload]
```

# Request With Credentials

Hal yang paling menarik yang diekspos oleh XMLHttpRequest atau Fetch dan CORS adalah kemampuan untuk membuat permintaan credential yang mengetahui cookie HTTP dan informasi Otentikasi HTTP. Secara default, dalam pemanggilan XMLHttpRequest atau Fetch cross origin, browser tidak akan mengirim credential. Flag khusus harus ditetapkan pada objek XMLHttpRequest atau konstruktor Permintaan saat dipanggil.

Dalam contoh ini, konten yang awalnya dimuat dari [https://foo.example](https://foo.example/) membuat permintaan GET sederhana ke sumber daya di [https://bar.other](https://bar.other/) yang membuat Cookie. Konten di foo.example mungkin berisi JavaScript seperti ini:

```jsx
const invocation = new XMLHttpRequest();
const url = 'https://bar.other/resources/credentialed-content/';

function callOtherDomain() {
  if (invocation) {
    invocation.open('GET', url, true);
    invocation.withCredentials = true;
    invocation.onreadystatechange = handler;
    invocation.send();
  }
}
```

![Untitled](CORS%20Example%20Scenario%20fe895440953642ef93d3a27df27f81a5/Untitled%202.png)

Request dan response yang kita dapatkan adalah

```
GET /resources/credentialed-content/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Referer: https://foo.example/examples/credential.html
Origin: https://foo.example
Cookie: pageAccess=2

HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:34:52 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Credentials: true
Cache-Control: no-cache
Pragma: no-cache
Set-Cookie: pageAccess=3; expires=Wed, 31-Dec-2008 01:34:53 GMT
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 106
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain

[text/plain payload]
```