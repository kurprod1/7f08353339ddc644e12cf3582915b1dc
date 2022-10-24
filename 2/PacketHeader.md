# Packet Header

Pada ulasan sebelumnya kita membahas bagaimana proses sebuah data ditransmisi, sekarang kita akan mencoba membongkar sebuah data. Apa isi sebiah data sehingga data tersebut bisa di transmisikan. ketika kita analogikan mengirim data di internet itu seperti mengirim POS, bisa dikatakan data adalah isi surat tersebut, kemudian paket header adalah amplop, perangko, alamat, dan kelengkapan lainnya. Paket header ini memberikan beberapa informasi tambahan. Jika kita bedah sebuah paket data yang ditrasnmisikan menggunakan ipv4, maka isi dari paket data tersebut bisa kita lihat seperti gambar berikut :

![IPv4 - Wikipedia](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/IPv4_Packet-en.svg/1200px-IPv4_Packet-en.svg.png)

- **IPVer :** Menyimpan informasi versi IP yang digunakan (IPv4 atau IPv6).
- **IHL (IP Header Leght)** : Informasi panjang keseluruhan header paket data. Minimum panjang IP header adalah 20 bits, dan maximum panjang adalah 24 bits.
- ***ToS* :** Adalah sebuah field dalam header IPv4 yang memiliki panjang 8 bit dan digunakan untuk menandakan jenis Quality of Service (QoS) yang digunakan oleh datagram yang bersangkutan untuk disampaikan ke router-router internetwork. Implementasi TOS ini biasanya saat kita melakukan limitasi HIT di web proxy mikrotik atau service VOIP.
- **16 Bit Total Length :** Isian 16 bits ini memberikan informasi ukuran keseluruhan paket(fragment)termasuk header dan data. Informasi ditampilkan dalam format bytes
- ***16 Bit Identification, Fragment Offset Flag/Length** :* Pada saat ip packet berjalan di internet, paket ini mungkin akan melewati beberapa router yang tidak bisa menghandle ukuran packet, misalnya nilai Maximum transmission unit (MTU) yang dimilikinya lebih kecil dibandingkan ukuran datagram IP, maka paket akan di pecah atau di fragmentasi menjadi paket - paket yang lebih kecil untuk kemudian akan disusun kembali setelahnya. Parameter ini yang akan digunakan untuk fragmentasi dan penyusunan kembali.
- **TTL :** Ada kemungkinan sebuah IP packet berjalan tanpa tujuan di jaringan Internet. Contoh kasus misalnya adanya kesalahan routing atau routing loop. Agar paket ini tidak berputar-putar di jaringan internet selamanya, nilai TTL ini akan dikurangi setiap kali paket data melewati router. Ketika nilai TTL sebuah paket data sudah habis atau memiliki nilai 0, maka paket tersebut akan di drop atau dibuang.
- ***Protocol** :* Berisi informasi protokol apa yang digunakan untuk melakukan transmisi data.
- **16 Bit Header Checksum :** informasi nilai yang dihitung berdasarkan kalkulasi content IP header. Digunakan untuk menentukan apakah ada error pada saat dilakukannya transmissi data.
- **32 Bit Source IP Address :** 32 bits informasi sumber IP paket data.
- **32 Bit Destination IP Address :** 32 bits informasi IP yang dituju paket data.
- **Options (if any) :** Parameter ini termasuk jarang digunakan, memiliki panjang yang bervariasi, dari 0 sampai kelipatan 32 bits. Parameter ini bisa digunakan untuk menyimpan sebuah nilai untuk opsi security, Record Route, Time Stamp, dll.
- **Data :** Berisi data yang ditransmisikan.

Dari informasi paket header diatas, pada akhirnya sebuah data bisa dikirim dari satu host ke host yang lain.