# Penetration Testing Introduction

## **Apa itu Penetration Testing**

Penetration Testing (disingkat pentest) adalah suatu kegiatan dimana seseorang mencoba mensimulasikan serangan yang bisa dilakukan terhadap jaringan organisasi / perusahaan tertentu untuk menemukan kelemahan yang ada pada sistem jaringan tersebut. Orang yang melakukan kegiatan ini disebut penetration tester (disingkat pentester). Penetration Testing mempunyai standar resmi sebagai acuan dalam pelaksanaannya. Standar ini bisa dilihat di [http://www.pentest-standard.org/](http://www.pentest-standard.org/index.php/Main_Page).

## **Untuk Apa Dilakukan Penetration Testing?**

Dengan melakukan pentest, celah-celah keamanan yang ada dapat diketahui dan dengan demikian dapat diperbaiki secepatnya. Seorang pentester mensimulasikan serangan yang dapat dilakukan, menjelaskan risiko yang bisa terjadi, dan melakukan perbaikan sistem tanpa merusak infrastruktur jaringan perusahaan tersebut.

## **Seberapa Penting Penetration Testing di Dunia IT?**

Pentest merupakan salah satu peran penting dalam dunia IT, terutama saat-saat seperti sekarang ini dimana perkembangan teknologi sangatlah cepat berkembang dan segala sesuatu mulai terkoneksi ke internet.

Kenapa kegiatan pentest diperlukan ? Perusahaan-perusahaan besar yang menyimpan data-data sensitif (seperti Bank) tentu tidak ingin jaringannya dibobol oleh orang tidak bertanggung jawab yang kemudian bisa mengambil alih kontrol jaringan dan menimbulkan kerugian yang sangat besar. Oleh karena alasan itu perusahaan menginvestasikan dana untuk memperkuat sistem jaringannya. Salah satu metode paling efektif adalah melakukan pentest.

## **Memahami Terminologi Ethical Hacking**

Berikut ini istilah-istilah penting yang perlu dipahami dalam etika hacking :

- *Threat* : Lingkungan atau situasi yang dapat mengakibatkan potensi penerobosoan keamanan.
- *Exploit* : Perangkat lunak yang memanfaatkan bug, kesalahan, atau kerentanan, yang menyebabkan akses tidak sah, eskalasi hak istimewa atau penolakan layanan pada sistem komputer. Ada dua metode untuk mengklasifikasikan exploit :
1. *Remote exploit* : Bekerja melalui jaringan dan memanfaatkan kerentanan keamanan tanpa akses sebelumnya ke sistem yang rentan.
2. *Local exploit* : Membutuhkan akses sebelumnya ke sistem yang rentan untuk meningkatkan hak istimewa.
3. Exploit merupakan cara yang pasti untuk menerobos keamanan sistem TI melalui kerentanan.
4. *Vulnerability* : adanya cacat perangkat lunak, desain logika, atau kesalahan pelaksanaan yang dapat menyebabkan kejadian tak terduga dan tidak diinginkan yang menjalankan instruksi buruk atau merusak pada sistem.
5. *Target of evaluation* : sistem, program, atau jaringan yang menjadi subjek keamanan analisis atau serangan.

Serangan terjadi ketika sebuah sistem disebabkan oleh kerentanan (Vulnerability). Banyak serangan yang diabadikan melalui *exploit*.

## **Tujuan Pentesting**

Keamanan terdiri dari empat elemen dasar :

- Confidentiality
- Authenticity
- Integrity
- Availability

Tujuan seorang hacker adalah untuk mengeksploitasi kerentanan dalam sistem atau jaringan untuk menemukan kelemahan dalam satu atau lebih dari empat elemen keamanan.

## **Segitiga Keamanan, Fungsionalitas, dan Kemudahan Penggunaan**

![https://lh6.googleusercontent.com/tgzmQ1HKbbTFP0WmONFLbR4uJeMd93PogK2uvZZpDYwxSqks4t0j4Tvq7gQ67JQdBR2yYhs6XG3cgRU6q1VYTzE9sJabgbVyglavWIjLERDo7VBS0F3teuPTL48oU0_wpIxFQ8FQ9i1qVCfmuKnmK-It1yY](https://lh6.googleusercontent.com/tgzmQ1HKbbTFP0WmONFLbR4uJeMd93PogK2uvZZpDYwxSqks4t0j4Tvq7gQ67JQdBR2yYhs6XG3cgRU6q1VYTzE9sJabgbVyglavWIjLERDo7VBS0F3teuPTL48oU0_wpIxFQ8FQ9i1qVCfmuKnmK-It1yY)

Sebagai seorang profesional keamanan, sulit untuk menyeimbangkan antara menambahkan penghalang keamanan untuk mencegah serangan dan membiarkan sistem tetap berfungsi bagi pengguna. Segitiga keamanan, fungsionalitas, dan kemudahan penggunaan adalah representasi keseimbangan antara keamanan dan fungsionalitas dan kemudahan penggunaan sistem bagi pengguna. Secara umum, seiring peningkatan keamanan, fungsionalitas sistem dan kemudahan penggunaan berkurang bagi pengguna.

# **Do’s and Don’ts (Legal View)**

Sebagai  manusia, tentunya kita akan terkait dengan norma dan peraturan yang ada di tempat kita berada. Seperti kata pepatah, **di mana bumi dipijak, di situ langit dijunjung.** Ternyata, dalam menjalankan penetration testing juga kita memiliki aturan-aturan yang perlu kita patuhi. Pada bagian ini, kita akan membahas mengenai hal apa saja yang diperbolehkan dan dilarang dalam penetration testing.

## **Hal Yang diperbolehkan dalam Penetration Testing**

![https://lh5.googleusercontent.com/PuauA_IKjPpsxCMi7zDSzsJC--bs9Aa4wq_gjxUx-Mk9bgA9Btoc0vbXMr_CTE-ZegRkl3KLvY8yGhFrbPMV7g4HujYJqBwKT2Yq1wWGg05r3YrEjMqKbOceGRwT6Ane11cV4mfOibA4KiDE7RqCXXp6_Lg](https://lh5.googleusercontent.com/PuauA_IKjPpsxCMi7zDSzsJC--bs9Aa4wq_gjxUx-Mk9bgA9Btoc0vbXMr_CTE-ZegRkl3KLvY8yGhFrbPMV7g4HujYJqBwKT2Yq1wWGg05r3YrEjMqKbOceGRwT6Ane11cV4mfOibA4KiDE7RqCXXp6_Lg)

Ada beberapa hal yang sangat perlu untuk diperhatikan ketika melakukan penetration test, antara lain :

1. Hormati pengetahuan dan kebebasan informasi.
2. Memberitahukan System Owner/Administrator akan adanya pelanggaran keamanan/lubang keamanan yang Anda lihat.
3. Jangan mengambil keuntungan yang tidak fair dari sebuah aksi.
4. Tidak mengumpulkan dan mendistribusikan sesuatu yang ilegal.
5. Tidak mengambil risiko bodoh dan selalu mengetahui kemampuan sendiri.
6. Selalu bersedia untuk secara terbuka memberitahukan, mengajarkan berbagai informasi dan metode yang diperoleh.
7. Jangan pernah melakukan aksi ke suatu sistem untuk mencari keuntungan.
8. Jangan pernah memberikan akses ke seseorang yang akan memberikan kerusakan.
9. Tidak pernah secara sengaja menghapus dan merusak file pada komputer yang bukan milik sendiri.
10. Hormati mesin orang lain, dan memperlakukannya seperti mesin sendiri.

## **Hal yang dilarang dalam Penetration testing**

Selain hal yang harus diingat dan diterapkan, dalam dunia penetration test juga ada beberapa hal yang sangat dilarang dan sebisa mungkin untuk dihindari, antara lain :

1. Melakukan uji coba tanpa seizin pemilik sistem.
2. Mengambil keuntungan tanpa seizin dan atau sepengetahuan pemilik sistem.
3. Melakukan tindakan uji coba untuk keperluan pihak manapun yang bersifat kriminal.
4. Mencuri data yang ada dalam suatu sistem yang sedang diuji coba tanpa seizin pemilik sistem.

Selain beberapa hal diatas, disetiap regional baik itu benua atau negara, telah menerapkan kebutuhan aturan yang sudah diatur dalam hukum negara masing-masing, sehingga seorang Pentester harus mengetahui lebih lanjut hukum yang berlaku di masing-masing negara dimana lokasi sistem berada.

# **Mengenal Fase Hacking**

![image source: eccouncil.org](Penetration%20Testing%20Introduction%208f416150c41949ba92f94d78cac07b4f/Untitled.png)

image source: eccouncil.org

**Tahap 1 : Pengintaian Pasif dan Aktif**

Pengintaian pasif melibatkan pengumpulan informasi mengenai target potensial tanpa pengetahuan individu atau perusahaan yang ditargetkan. Pengintaian aktif melibatkan menyelidik jaringan untuk menemukan host individu, alamat IP, dan layanan di jaringan.

**Tahap 2 : Scanning**

Scanning melibatkan pengambilan informasi yang ditemukan selama pengintaian dan menggunakannya untuk memeriksa jaringan. Alat yang mungkin digunakan oleh peretas selama tahap scanning dapat mencakup dialer, port scanner, network mapper, sweepers, dan vulnerability scanner. Hacker mencari informasi yang dapat membantu mereka melakukan serangan seperti nama komputer, alamat IP, dan akun pengguna.

**Tahap 3 : Mendapatkan Akses**

Ini adalah tahap dimana hacking sebenarnya terjadi. Kerentanan yang ditemukan selama tahap pengintaian dan scanning sekarang dimanfaatkan untuk mendapatkan akses.

**Tahap 4 : Mempertahankan Akses**

Begitu seorang hacker mendapatkan akses, mereka ingin menyimpan akses itu untuk eksploitasi dan serangan di masa depan. Terkadang, hacker membajak sistem dari hacker lain atau petugas keamanan dengan mengamankan akses eksklusif mereka dengan backdoor, rootkit, dan Trojan.

**Tahap 5 : Menutupi Jejak**

Begitu hacker berhasil mendapatkan dan mempertahankan akses, mereka menutup jejak mereka untuk menghindari deteksi oleh petugas keamanan, untuk terus menggunakan sistem yang dimiliki, untuk menghapus bukti hacking, atau untuk menghindari tindakan hukum.

**Catatan**

Fase yang dijelaskan diatas merupakan fase umum yang digunakan dalam aktifitas seorang pentester, beberapa organisasi menerapkan fase yang berbeda yang sudah ditentukan sesuai kebutuhan organisasi masing-masing.

Untuk mempelajari mengenai phases pada penetration testing, cobalah baca artikel berikut: 

- [Penetration Testing](https://www.eccouncil.org/what-is-penetration-testing/)