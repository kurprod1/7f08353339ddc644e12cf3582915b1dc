# Common Vulnerabilities

Created: June 22, 2022 1:17 PM

# Serangan DoS

WebSockets memungkinkan jumlah koneksi yang tidak terbatas mencapai server. Ini memungkinkan penyerang membanjiri server dengan serangan DOS. Ini sangat membebani server dan menghabiskan sumber daya di server itu. Kemudian situs web menjadi sangat lambat.

# Tidak Ada Otentikasi Selama Proses Handshake

Masalahnya di sini adalah bahwa protokol WebSocket tidak membiarkan server mengotentikasi klien selama proses handshake. Hanya mekanisme normal untuk koneksi HTTP yang tersedia. Itu termasuk otentikasi dan cookie HTTP dan TLS. Handshake yang diupgrade masih terjadi dari HTTP ke WebSocket. Tapi, HTTP mengirimkan informasi otentikasi langsung ke WS. Ini dapat dimanfaatkan dan kami menyebutnya serangan **Cross-Site WebSocket Hijacking**.

# Unencrypted TCP

Masalah lain dengan WebSockets adalah bahwa mereka dapat digunakan melalui channel TCP yang tidak terenkripsi. Hal ini menyebabkan semua jenis masalah yang tercantum dalam OWASP Top 10 A6-Sensitive Data Exposure.

# Input Vulnerability

Teknik seperti XSS adalah serangan umum namun sangat berbahaya yang dapat sangat merusak situs web. Nampaknya pesan yang dikirim menggunakan protocol Websocket juga terdapat celah kerentanan XSS.

# Tunneling

WebSockets memungkinkan siapa pun melakukan tunnel layanan TCP arbitrer. Contohnya adalah tunneling koneksi database secara langsung melalui dan mencapai browser. Dalam kasus serangan Cross-Site Scripting itu berkembang dan akhirnya menjadi pelanggaran keamanan yang lengkap.

# Sniffing Attack

Transfer data melalui protokol WebSocket dilakukan dalam teks biasa, mirip dengan HTTP. Oleh karena itu, data ini rentan terhadap serangan man-in-the-middle. Untuk mencegah kebocoran informasi, gunakan protokol WebSocket Secure (wss://). Seperti HTTPS, wss tidak berarti aplikasi web Anda aman, tetapi memastikan bahwa transmisi data dienkripsi menggunakan Transport Layer Security (TLS).