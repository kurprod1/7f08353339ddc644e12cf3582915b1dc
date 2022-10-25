# Websocket Vulnerabilities

WebSocket banyak digunakan dalam aplikasi web modern. WebSocket digunakan untuk semua jenis tujuan, termasuk melakukan action pengguna dan mengirimkan informasi sensitif. Hampir semua kerentanan keamanan web yang muncul dengan HTTP biasa juga dapat muncul terkait dengan komunikasi WebSockets.

![Untitled](Websocket%2052c1d9af44154e02831707c0a4337869/Untitled.png)

WebSockets adalah protokol komunikasi full-duplex dua arah yang dimulai melalui HTTP. Mereka biasanya digunakan dalam aplikasi web modern untuk streaming data dan lalu lintas asinkron lainnya.

Perbedaan yang mencolok antara WebSocket dan HTTP ada pada umur request. Dengan HTTP, client mengirim request dan server mengembalikan response. Biasanya, respons terjadi saat itu juga, dan transaksi selesai. Bahkan jika koneksi jaringan tetap establish, ini akan digunakan untuk transaksi terpisah dari request dan response sebelumnya.

Koneksi WebSocket dimulai melalui HTTP dan biasanya berumur panjang. Pesan dapat dikirim ke kedua arah kapan saja dan tidak bersifat transaksional. Koneksi biasanya akan tetap terbuka dan idle sampai client atau server siap untuk mengirim pesan.

Implementasi yang mudah dengan Websocket adalah chatting karena pesan dapat dikirim kapan saja, dan dapat diterima dengan segera.