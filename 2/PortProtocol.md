# Port&Protocol

Pada bagian sebelumnya membahas tentang apa yang terjadi pada sebuah paket data ketika akan dikirim dan ketika paket data tersebut diterima. Sekarang pertanyaannya adalah apa yang berperan diantara device yang akan saling bertukar informasi sehingga paket data bisa ditrasnmisikan. Disinilah fungsi sebuah protokol. Protokol akan menentukan bagaimana cara sebuah paket data ditransmisikan. Ada beberapa jenis protokaol yang sering kita gunakan seperti TCP, UDP, ICMP, dan IP Protokol lainnya.

## **Internet Protocol (IP)**

Adalah protokol standard yang digunakan untuk mengkomunikasikan data melalui berbagai jenis perangkat dan layer berdasarkan ip address yang tersimpan di paket header. Setiap datagram memiliki dua komponen, yakni header dan payload. IP header berisi informasi source IP address, destination IP address, dan beberapa informasi data lain yang dibutuhkan router untuk mengirim datagram. Kemudian payload adalah isi dari data yang akan dikirim. Metode penggabungan data payload dan header menjadi sebuah paket data disebut encapsulation. Pengiriman data dilakukan dengan sistem per paket dan/atau per connection. Sistem ini menjamin keutuhan data, dan mencegah terjadinya kekurangan ataupun duplikasi data.

## **Protokol TCP**

Protokol ini merupakan salah satu jenis protokol yang paling sering digunakan di internet. Contoh aplikasi yang menggunakan protokol TCP misalnya http, email, ftp, dll. TCP bekerja dengan pengalamatan port seperti berikut :

- Port 1 - 1024 : Low Port (Standard Service Port). Port ini telah digunakan oleh service standart. Disarankan jangan menggunakan low port jika Anda ingin melakukan costumize port pada sebuah aplikasi atau service.
- Port 1025 - 65536 : High port (untuk transmisi lanjutan). Kita bisa gunakan port ini untuk transmisi atau service yang bersifat custom/tidak standart. Misalnya kita membuat proxy server. Maka port yang kita gunakan untuk proxy server adalah High Port ini. Kalau kita perhatikan, default proxy sendiri biasanya menggunakan high port, seperti port 8080 atau 3128.

### Prinsip **Kerja TCP**

Pada saat melakukan tugasnya, protokol TCP memiliki beberapa prinsip kerja. Prinsip kerja sebuah protokol ini akan menjadi referensi bagi pembuat program atau admin jaringan untuk memilih protokol apa yang nanti akan digunakan untuk bisa melakukan trasnmisi data.

### **Connection-Oriented**

Sebelum data dapat ditransmisikan antara dua host, dua proses yang berjalan pada lapisan aplikasi harus melakukan negosiasi untuk membuat sesi koneksi terlebih dahulu. Proses pembuatan koneksi TCP disebut juga dengan "Three-way Handshake". Tujuan metode ini adalah agar dapat melakukan sinkronisasi terhadap nomor urut dan nomor acknowledgement yang dikirimkan oleh kedua pihak dan saling bertukar ukuran TCP Window.

- Client : SYN -> Server : Client akan mengirimkan SYN ke server
- Server : SYN-ACK -> Client : Server merespon SYN Client dengan mengirimkan SYN-ACK ke Client
- Client : ACK -> Server : Setelah menerima SYN-ACK dari server, client mengirim ACK ke Server.

Setelah melewati handshake tadi, baru kemudian koneksi terbentuk (established). Bisa dikatakan device yang menggunakan protokol TCP ini akan melakukan kesepakatan terlebih dahulu sebelum transmisi data terjadi. TCP menggunakan proses jabat tangan yang sama untuk mengakhiri koneksi yang dibuat. Hal ini menjamin dua host yang sedang terkoneksi tersebut telah menyelesaikan proses transmisi data dan semua data yang ditransmisikan telah diterima dengan baik. Koneksi TCP ditutup dengan menggunakan proses terminasi koneksi FIN (TCP connection termination).

![https://data-flair.training/blogs/wp-content/uploads/sites/2/2021/12/connection-oriented-service-and-connectionless-service.webp](https://data-flair.training/blogs/wp-content/uploads/sites/2/2021/12/connection-oriented-service-and-connectionless-service.webp)

### **Reliable Transmission**

Data yang dikirimkan ke sebuah koneksi TCP akan diurutkan dengan sebuah nomor urut yang unik disetiap byte data dengan tujuan agar data dapat disusun kembali setelah diterima. Pada saat transmisi, bisa jadi data dipecah/difragmentasi, hilang, atau tiba di device tujuan tidak lagi urut. Pada saat data diterima, paket data yang duplikat akan diabaikan dan paket yang datang tidak sesuai dengan urutannya akan diurutkan agar dapat disusun kembali.

### Error **Detection**

Jika terjadi error, misalnya ada paket data yang hilang pada saat proses transmisi, bisa dilakukan pengiriman ulang data yang hilang. Untuk menjamin integritas setiap segmen TCP, TCP mengimplementasikan penghitungan TCP Checksum.

**Flow Control**

Mendeteksi supaya satu host tidak mengirimkan data ke host lainnya terlalu cepat. Flow Control akan menjadi sangat penting ketika bekerja di lingkungan dimana device satu dengan device yang lain memiliki kecepatan komunikasi jaringan yang beragam. Sebagai contoh, ketika PC mengirimkan data ke smartphone. kemampuan PC dengan smartphone tentu berbeda. Smartphone lebih lambat dalam memproses data yang diterima daripada PC, maka TCP akan mengatur aliran data agar smartphone tidak kewalahan.

**Segment Size Control**

Mendeteksi besaran MSS (maximum segment size) yang bisa dikirimkan supaya tidak terjadi IP fragmentation. MSS adalah infomasi ukuran data terbesar yang dapat ditransmisikan oleh TCP dalam bentuk segment tunggal. Informasi MMS ini dalam format Bytes. Untuk performa terbaik, MSS bisa ditetapkan dengan ukuran yang cukup kecil untuk menghindari fragmentasi IP. Fragmentasi IP dapat menyebabkan hilangnya paket dan retransmisi yang berlebihan.

**Congestion Control**

Prisip kerja TCP terkhir yang cukup penting adalah Congestion Control. TCP menggunakan beberapa mekanisme untuk mencegah terjadinya congestion pada network. mekanisme yang dilakukan salah satunya adalah mengatur aliran data yang masuk ke dalam network.

### **ICMP**

Salah satu jenis protokol yang biasa digunakan untuk pengecekan dan mengindikasi error pada saat transmisi dalam sebuah jaringan. ICMP disalurkan berbasis best effort sehingga bisa mengetahui jika terjadi error (datagram lost). Host (baik device yang mencoba transmisi ataupun device tujuan transmisi tujuan) akan mendeteksi apabila terjadi permasalahan tranmisi, dan membuat ICMP message yang akan dikirimkan ke host asal. Contoh penggunaan protokol ICMP yang sering kita lakukan misalnya pada saat kita menjalankan Ping atau Traceroute.

![https://static.javatpoint.com/tutorial/computer-network/images/icmp-protocol2.png](https://static.javatpoint.com/tutorial/computer-network/images/icmp-protocol2.png)

## **UDP**

User Datagram Protocol (UDP) merupakan salah jatu jenis protokol yang biasa digunakan utnuk transmisi sederhana dengan mekanisme protokol yang minimal.

### ***Prinsip Kerja UDP***

- **Connectionless** : Device yang satu bisa mengirimkan pesan/datagram ke device lainnya di jaringan, tanpa terlebih dahulu melakukan negosiasi (hand-shake).
- **Unreliable** : Datagram yang dikirimkan pun tidak dijamin sampai ke tujuan. Paket data UDP akan dikirimkan sebagai datagram tanpa adanya nomor urut atau pesan acknowledgment. Tidak ada flow control ataupun mekanisme lain untuk menjaga keutuhan datagram (unreliable). Akan tetapi UDP melakukan mekanisme checksums untuk data integrity.

UPD biasanya digunakan karena beberapa alasan berikut :

Protokol yang "ringan" (lightweight) : Lebih hemat sumber daya memori dan prosesor, beberapa protokol lapisan aplikasi membutuhkan penggunaan protokol yang ringan yang dapat melakukan fungsi-fungsi spesifik dengan saling bertukar pesan. Contoh dari protokol yang ringan adalah fungsi query nama dalam protokol lapisan aplikasi Domain Name System.

**Transmisi broadcast** : Untuk mengirimkan datagram, UDP tidak perlu membuat koneksi terlebih dahulu dengan sebuah host tertentu, dengan begitu UDP memungkinkan untuk membuat transmisi broadcast. Protokol TCP yang hanya dapat mengirimkan transmisi one-to-one, karena harus ada proses handshake terlebih dahulu antar device. Contoh transmisi broadcast salah satunya query nama dalam protokol NetBIOS Name Service.

**Streaming dan Game Online** : Streaming dan game online membutuhkan transmisi yang real time. Jika ada paket yang hilang pada saat trasmisi kemudian harus menunggu paket pengganti, maka beban network akan berlebih, dan jeda menunggu akan membuat data tidak lagi real time.