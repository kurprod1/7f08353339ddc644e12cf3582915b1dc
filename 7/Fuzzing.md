# Fuzzing

Fuzz testing atau Fuzzing adalah teknik pengujian Black Box, yang pada dasarnya terdiri dari menemukan bug menggunakan injeksi data cacat/semi-cacat secara otomatis.

![Untitled](Fuzzing%20980b5b39e2544de6954a9de3bfc5b25e/Untitled.png)

Fuzzing ini merupakan bagian teknik yang digunakan QA untuk menemukan kesalahan programming dan vulnerability pada software, sistem operasi atau jaringan. Biasanya kita perlu mendalami cara kerja dan komunikasi aplikasi tersebut seperti halnya jika kita akan menguji aplikasi web server kita
harus tahu protokol HTTP. Dan umumnya indikator aplikasi memiliki kerentanan yakni
aplikasi mengalami crash.

Banyak best practice yang bisa kita ikuti agar kalian memiliki tahapan yang tetap dalam melakukan teknik ini. Gambar diatas menunjukkan step sebagai berikut :

1. Identification of target system
    
    Bagian ini kalian harus mengidentifikasi aplikasi apa yang akan kalian fuzzing. Sebagai contoh apakah aplikasi ini berupa ftp server, ssh server, binary apps, dan lain sebagainya.
    
2. Determination of inputs
    
    Kalian perlu mempelajari data seperti apa yang diterima oleh aplikasi atau sistem.
    
3. Generation of fuzzed data
    
    Bagian ini kita harus membuat variasi data yang akan kita berikan kepada aplikasi.
    
4. Execution of tests with fuzzed data
    
    Ketika variasi data sudah kalian buat pada tahap ini kalian perlu memberikan kepada aplikasi
    
5. Analysis of system behavior
    
    Setelah data diberikan ke aplikasi apakah terjadi respon yang tidak sesuai ?