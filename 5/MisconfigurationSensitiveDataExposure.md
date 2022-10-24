# Misconfiguration & Sensitive Data Exposure

Misconfiguration biasanya didefinisikan sebagai kegagalan untuk menerapkan semua kontrol keamanan untuk server atau aplikasi web, atau mengimplementasikan kontrol keamanan, tetapi melakukannya dengan kesalahan. Lebih jelasnya bisa dipastikan bahwa aplikasi yang akan kita gunakan cukup memiliki berbagai fitur keamanan. Namun sangat disayangkan pengetahuan Tim Software Engineer terhadap keamanan sangat kurang. Sehingga kontrol keamanan tersebut tidak diimplementasikan dengan benar.

![Gambar: OWASP TOP 10 - Security misconfiguration](https://lh4.googleusercontent.com/9rTdh69PZvXZSCPOPp2XGLGr0oW-EllHAPHsBwH4MKL8M1Luo3Mq0UPEPfyWvh8j3RGfCxfy-eNBIo71yW1SDqGZCcJoD86M2Wgpe-6oOSwI8TCD5TWxmylKGKc654OenwPAlbEngpBWX4qtR7RBb-EcFjM)

Gambar: OWASP TOP 10 - Security misconfiguration

Selain karena kurangnya wawasan di bidang Cyber Security, bisa juga disebabkan oleh kultur perusahaan yang sering terjadi ***over engineering*** berlebihan. Istilah tersebut mulai populer di kalangan perusahaan startup.

Agar paham dengan hal tersebut, penjelasan over engineering contohnya ketika perusahaan baru (belum dewasa) ingin membuat produk software dengan teknologi terbaru meski traffic masih sedikit dengan tim yang sangat terbatas. Sesuatu yang sederhana bisa diselesaikan dengan teknologi lama misal dengan konsep monolith (PHP, MySQL, Apache). Namun jadi rumit ketika memaksakan banyak teknologi terbaru diterapkan apalagi dengan sumber daya terbatas. Akhirnya akan menyebabkan terjadi konfigurasi sistem yang tidak optimal dan penguasaan teknologi yang kurang maksimal.

Kelalaian proses di tahapan code review juga bisa mengakibatkan munculnya misconfiguration vulnerability di production server. Cukup banyak yang jadi sebab tapi intinya adalah tugas kalian sebagai Security Engineer untuk segera mengevaluasi dan menemukan lebih cepat sebelum terjadi serangan.

Misconfiguration memiliki dampak berbagai banyak hal mulai dari server berhasil diambil alih oleh Penyerang. Hingga menyebabkan banyak kebocoran data yang tidak terhitung kerugian perusahaan.

# References

- [A6:2017-Security Misconfiguration](https://owasp.org/www-project-top-ten/2017/A6_2017-Security_Misconfiguration)

# Study Case

## ElasticSearch & Kibana

Perusahaan startup menggunakan ElasticSearch guna untuk menyimpan log secara terdistribusi dan menggunakan dashboard Kibana dalam melakukan visualisasi data. Kali ini kita akan mempraktikkan instalasi ElasticSearch dan Kibana dengan docker compose.

Docker-compose adalah alat untuk mendefinisikan dan menjalankan aplikasi beberapa docker container bersamaan. Dengan tool ini, kita bisa menggunakan file YAML untuk mengkonfigurasi aplikasi Anda. Kemudian, dengan satu perintah, kita bisa membuat dan memulai semua service.  Nah, Lakukan perintah berikut jika docker compose belum pernah dipasang di laptop kalian.

```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

Selanjutnya kita siapkan contoh proyek docker dari repository dan menjalankannya dengan perintah dibawah ini :

```bash
$ git clone https://github.com/ne0z/SecurityMisconfigurationByExample.git
$ cd VulnerableElasticSearchWithKibana$ docker-compose up -d
```

![Gambar: ElasticSearch & Kibana tidak mengimplementasikan autentikasi](https://lh3.googleusercontent.com/eURLWbKfYSOKoBA-h4OMBKndgRw09iJ-FjFWZVArGhTpT66UHW3rvay3Z7EfEeIUTebKakt0K2bww93h3Uo_CxKL_6VvSbiS8kacfdfK3hI2IOkCo39-SHhwZJINopGNKEdRurZ7dDoRYsblJ_GCnZkVufI)

Gambar: ElasticSearch & Kibana tidak mengimplementasikan autentikasi

Dan untuk mematikan server kalian bisa menggunakan perintah **docker-compose down -v** pada direktori yang sama.

Kalian bisa membuka Kibana di alamat **http://localhost:5601**. Seperti yang terlihat pada gambar diatas dashboard Kibana tidak menerapkan otentikasi diawal. Perlu diketahui bahwa untuk menerapkan otentikasi kita harus mengaktifkan lisensi komersial dan mengkonfigurasinya secara manual. Panduan konfigurasi bisa teman-teman akses melalui situs :

- [https://www.elastic.co/guide/en/elasticsearch/reference/6.8/get-started-enable-security.html](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/get-started-enable-security.html)
- [https://www.elastic.co/guide/en/kibana/current/kibana-authentication.html](https://www.elastic.co/guide/en/kibana/current/kibana-authentication.html)

Alternatif yang lebih mudah, open distro elasticsearch dikembangkan untuk kebutuhan keamanan. Open distro dikembangkan untuk kalangan komunitas namun masih layak untuk digunakan di production. Bedanya jika elasticsearch sebelumnya kita harus memiliki lisensi berbayar agar semua fitur security bisa digunakan dan mendapatkan dukungan penuh resmi dari elasticsearch. Untuk Open distro kita hanya memiliki dukungan dari kontribusi komunitas open source. Tapi menurut saya ini cukup membantu mengatasi masalah autentikasi Kibana dengan biaya yang terjangkau.

Untuk menjalankan elasticsearch dari open distro, teman-teman bisa mengikuti perintah sebagai berikut :

```bash
$ docker pull amazon/opendistro-for-elasticsearch:1.6.0
$ docker pull amazon/opendistro-for-elasticsearch-kibana:1.6.0
$ docker run -p 9200:9200 -p 9600:9600 -e "discovery.type=single-node" amazon/opendistro-for-elasticsearch:1.6.0 
```

Exercise

1. Sebagai penyerang apa saja yang bisa kalian dapatkan dari kerentanan elasticsearch diatas ? Jelaskan !
2. Pelajari misconfiguration pada ElasticSearch dan Kibana. Kemudian sebagai seorang Security Engineer atau Penetration tester buatlah rekomendasi berupa solusi menutup kerentanan ini !

### **Bug bounty tips**:

Teman-teman bisa menggunakan shodan.io untuk mencari vulnerable elasticsearch yang tidak memiliki autentikasi. Biasanya kibana berjalan pada port 5601, jadi kalian bisa menggunakan query shodan untuk mencari berdasarkan port 5601.

## ****Kesalahan Konfigurasi Web Server dan App pada Docker****

Kita dapat membuat *docker image* secara otomatis dengan membaca instruksi dari Dockerfile. Jadi Dockerfile ini merupakan dokumen teks yang berisi semua perintah yang bisa dipanggil pengguna pada baris perintah untuk merakit *docker image*.

### Lab

Untuk menguji aplikasi web tersebut kita bisa memulai dengan memetakan URL menggunakan software **dirsearch**. Dirsearch adalah tool berbasis Python yang digunakan untuk memindai direktori web dan file tersembunyi. Teknik Dictionary Attack dipakai di dalam tool ini sehingga mampu menemukan file dan folder. Dictionary Attack memanfaatkan pustaka berisi kata-kata yang sudah didefinisikan sehingga aplikasi Dirsearch cukup mengurutkan daftar kata-kata (wordlist) untuk dicoba pada web app apakah URL tersebut ada (ditandai dengan kode respon HTTP 200, 301, 403) atau tidak (ditandai dengan kode respon HTTP selain 404)

Dirsearch dapat berjalan di Windows, Linux, dan macOS, dan ia menawarkan antarmuka baris perintah yang sederhana, namun kuat. Dengan fitur-fitur seperti multithreading, dukungan proxy, penundaan permintaan, pengacakan agen pengguna, dan dukungan untuk beberapa ekstensi. Jika dalam OS kalian belum terpasang dirsearch, teman-teman bisa mengikuti perintah dibawah ini :

```bash
$ git clone https://github.com/maurosoria/dirsearch.git
$ cd dirsearch
```

Selanjutnya kita akan memindai URL pada aplikasi web dengan alamat http://localhost menggunakan dirsearch. Biasanya ini masuk dalam tahapan awal active information gathering sehingga setelah ini kita akan membahas bagaimana proses identifikasi celah dari temuannya.

```bash
$ python3 dirsearch.py -u http://[masukkan_url_disini] -e php,css,asp
Target: http://localhost
[22:28:34] Starting:[22:28:34] 400 -  157B  - /%2e%2e/google.com
[22:28:36] 301 -  169B  - /.git  ->  http://localhost/.git/....
[22:28:36] 200 -   58B  - /.gitignore....
[22:28:37] 403 -  555B  - /.htaccess~
[22:28:37] 403 -  555B  - /.htpasswd-old
[22:28:37] 403 -  555B  - /.htusers
[22:28:37] 403 -  555B  - /.htpasswds
[22:28:37] 403 -  555B  - /.htpasswd_test
[22:28:50] 403 -  555B  - /admin/.htaccess
[22:29:02] 403 -  555B  - /administrator/.htaccess
[22:29:06] 301 -  169B  - /app  ->  http://localhost/app/
[22:29:06] 403 -  555B  - /app/.htaccess
[22:29:07] 301 -  169B  - /assets  ->  http://localhost/assets/
[22:29:15] 200 -  817B  - /composer.json
[22:29:15] 200 -  126KB - /composer.lock
[22:29:19] 301 -  169B  - /database  ->  http://localhost/database/
[22:29:20] 403 -  555B  - /database/[22:29:34] 200 -	2KB - /index.php
[22:29:54] 200 -  903B  - /phpunit.xml
[22:29:56] 301 -  169B  - /public  ->  http://localhost/public/
[22:29:57] 200 -  775B  - /readme.md
[22:29:57] 301 -  169B  - /resources  ->  http://localhost/resources/
[22:30:04] 301 -  169B  - /storage  ->  http://localhost/storage/
[22:30:07] 301 -  169B  - /tests  ->  http://localhost/tests/
[22:30:07] 403 -  555B  - /tests/
[22:30:11] 200 -	0B  - /vendor/autoload.php
```

Dari aplikasi Dirsearch kita menemukan URL yang rentan mulai dari .git yang berisi informasi mengenai *source code* dan *version control*. Kemudian diikuti dengan composer.json yang berisi dependency apa yang terpasang di aplikasi web tersebut.

## Redis Tanpa Authentikasi

Redis, singkatan dari Remote Dictionary Server, adalah penyimpanan data nilai utama di dalam memori yang super cepat dengan sumber terbuka untuk digunakan sebagai database, cache, broker pesan, dan antrian.

Biasanya redis di arsitektur microservice untuk menyimpan data seperti token user, hal ini dikarenakan redis yang terbukti mampu melayani permintaan dengan performa cepat. Selain itu redis memiliki fitur seperti expire key dimana sebagai developer bisa memberikan waktu kapan data itu akan dihapus secara otomatis. Hal ini sangat diperlukan terutama untuk penyimpanan token autentikasi yang dibatasi misal 1 hari. Jika user sudah melebihi 1 hari maka token tersebut menjadi tidak valid.

Sayangnya redis ketika kita pasang di server tidak menerapkan autentikasi keamanan. Kita harus mengatur secara manual untuk itu mengikuti dari kebutuhan perusahaan. Artinya jika kita bisa mengakses redis tanpa autentikasi tersebut akan ada kemungkinan besar kita mendapatkan token-token dari user yang sudah login.

Dari kasus tersebut kita bisa login menggunakan token tersebut untuk mengakses halaman sensitif seperti my profile dan lain sebagainya. Akhirnya kita bisa mendapatkan data user dengan begitu banyak.

Untuk memahami lebih detail teman-teman bisa mencoba redis menggunakan perintah berikut:

```bash
$ docker run -d --name redis -p 0.0.0.0:6379:6379 redis:latest
```

Redis akan berjalan pada port 6379 dan untuk mengaksesnya kita perlu memasang redis-client pada laptop kita.

```bash
$ apt-get update$ apt-get install redis-tools
```

Kita mulai menambahkan data dulu kedalam redis

```bash
$ redis-cli -h 127.0.0.1$ SET 1234 '{"username":"danang","password":"c935ea8b4360d0ddce46d43e51f69487c3510266","email":"danang@sekolahhacker.com"}'
$ exit
```

Perintah diatas dimaksudkan untuk menambahkan data kredensial berupa JSON dengan key 1234 yang merupakan token. Untuk mengeksploitasi redis yang tidak memiliki otentikasi, teman-teman bisa mengikuti perintah dibawah ini untuk mendapatkan semua key :

```bash
$ redis-cli -h 127.0.0.1 --scan --pattern '*'
```

Selanjutnya teman-teman perlu mendapatkan value dari key yang sudah didapatkan :

```bash
$ redis-cli -h 127.0.0.1 GET 1234 
```

![Gambar: Data kredensial dari Redis](https://lh6.googleusercontent.com/2d4zUgOQ_ZXQtwwI78QCkgoM_8TZS9qdPGlPnrTGhg1TtVunamzJkQ1IcYEyGCtBTVDl-q13dFcQA_0aZkd0I7QL2O2O-AZcXpz1GW3dtQAcLQMkpaVU7n-3LS1ji-CL3cC79kPS6Ps94YhxHA)

Gambar: Data kredensial dari Redis

![Gambar: Hasil pencarian server redis yang tidak menerapkan autentikasi](Misconfiguration%20&%20Sensitive%20Data%20Exposure%20e41edbca6b4340ef84d373d4acd36a06/Untitled.png)

Gambar: Hasil pencarian server redis yang tidak menerapkan autentikasi

Nah begitulah kira-kira kita bisa mengeksploitasi redis, sekedar pengetahuan untuk kalian. Bahwa jika kita tinjau menggunakan shodan.io dengan query **port:6379 redis_version**. Akan ditemukan sebanyak 29.542 server yang tidak menerapkan autentikasi pada redis !

Kesimpulan dari materi ini teman-teman agar bisa menemukan kerentanan terbaru di aplikasi yang lain sedikit memerlukan penelitian terhadap aplikasi. Biasanya bisa dilakukan dengan mencoba memasang aplikasi yang sering digunakan perusahaan-perusahaan startup. Setelah itu kita mengamati kelalaian apa yang kemungkinan terjadi.