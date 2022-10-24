# IP Address

IP Address (internet protocol address) merupakan deretan angka biner antara 32 bit sampai dengan 128 bit yang digunakan sebagai alamat/identitas untuk tiap komputer/host dalam jaringan. Angka 32 bit digunakan untuk alamat IP Address versi IPv4 dan angka 128 bit digunakan untuk IP Address versi IPv6. IPv6 merupakan IP versi terbaru, namun masih jarang digunakan, sehingga disini kita akan lebih difokuskan pada pembahasan IPv4.

Setiap perangkat jaringan baik komputer, router, ataupun yang lain, harus memiliki identitas/alamat yang unik. Dimana alamat unik inilah yang digunakan oleh masing-masing perangkat sebagai acuan ketika ingin saling berkomunikasi. IP Address ini sama halnya dengan alamat rumah seseorang.

Sebagai seorang cyber security engineer, wajib menguasai ilmu IP Address ini. Karena nantinya setiap server yang kita test atau lindungi pasti memiliki IP Addressnya masing-masing.

## **Pembagian Kelas IP Address**

Jumlah IP Address yang banyak ini harus dibagi-bagikan keseluruh pengguna jaringan internet di seluruh dunia. Untuk mempermudah proses pembagiannya, IP Address  dikelompokan dalam kelas-kelas. IP Address dikelompokan dalam lima kelas, yaitu kelas A, B, C, D, dan E. Perbedaannya terletak pada ukuran, jumlah IP Address, serta peruntukan dari masing-masing kelas yang dapat diklasifikasikan sebagai berikut :

- IP Adddress kelas A digunakan untuk jaringan yang berukuran sangat besar. Range address dari kelas ini adalah 1.255.255.255-127.255.255.255.
- IP Address Kelas B digunakan untuk jaringan berukuran besar dan sedang. Range address ini dimulai dari 128.0.255.255-191.0.255.255.
- IP Address Kelas C digunakan untuk pembagian jaringan dengan ukuran user yang lebih sedikit. Range address ini dimulai dari 192.0.0.255-223.0.0.255
- Kelas D diperuntukan bagi jaringan multicast, dengan range IP 224.0.0.0 – 239.255.255.255.
- Kelas E untuk Eksperimental. Dengan range ip 240.255.255.255 hingga 255.255.255.255.

Kelas A – C adalah kelas yang dapat digunakan untuk perangkat jaringan (komputer, server, router, dll). Sedangkan untuk kelas D dan E tidak bisa.

Disini tidak perlu terlalu dihapalkan terkait pembagian masing-masing kelasnya. Yang penting kita paham dan mengetahui bahwa alamat IP Address itu dapat dibagi-bagi/dipecah lagi kedalam porsi yang lebih kecil sesuai kebutuhan.

### **Private IP Address**

Pada arsitektur IP address, Private IP Address adalah IP Address yang diperuntukkan untuk jaringan lokal. IP private tidak boleh ada di jaringan internet dan tidak dapat diakses di jaringan internet. Pada implementasi di jaringan real, biasanya jaringan lokal menggunakan IP Private, kemudian ditambahkan sebuah router yang menjembatani jaringan lokal yang menggunakan IP private dengan jaringan publik yang menggunakan IP Public. IP Private yang dapat digunakan sudah ditentukan, yaitu hanya :

Kelas A :

10.0.0.0/8

10.0.0.0 – 10.255.255.255

Kelas B :

172.16.0.0/22

172.16.0.0 – 172.31.255.255

Kelas C :

192.168.0.0/16

192.168.0.0 – 192.168.255.255

Selain dari IP diatas, tidak dapat digunakan untuk IP Private. Karena biasanya sudah termasuk kedalam IP Publik atau IP-IP Spesial lainnya (Multicast, experimental).

### **Public IP Address**

IP Publik adalah IP yang bisa diakses oleh semua orang di internet. Setiap aplikasi maupun web yang dapat kita akses di internet, dibaliknya pasti terdapat komputer server yang dipasang IP Publik. Karena itu untuk bisa mendapatkan IP Publik, kita harus membayar kepada Provider/ISP (Internet Service Provider. Tidak seperti IP Private yang dapat digunakan sesuka hati. Nilai IP Publik yang bisa digunakan adalah selain dari IP Private, dan kita tidak dapat asal menentukan. Harus disesuaikan dengan yang sudah kita dapat dari ISP.

### **NAT (Network Address Translation)**

Untuk mengatasi keterbatasan IP Publik yang jumlahnya sedikit dan mahal, maka ada teknologi bernama NAT. NAT merupakan  teknologi yang memungkinkan alamat IP Private bisa mengakses/diakses ke/dari internet melalui satu IP address Publik. IP Private seperti dibungkus/disembunyikan kedalam IP Publik sehingga IP Private akan menyerupai/sama persis dengan IP Publik di mata internet. Orang-orang atau komputer yang berada di internet tidak mengenali IP Privatenya, melainkan hanya IP Publiknya saja. Berikut adalah ilustrasi dari NAT.

![Untitled](IP%20Address%20f1f7c2a45bde4bf181b9d2f1f850c5c1/Untitled.png)