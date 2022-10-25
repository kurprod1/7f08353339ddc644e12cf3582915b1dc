# XSS Categories


Faktanya Cross-site scripting ternyata tidak hanya teknik yang sederhana, ada 2 kategori jika dilihat dari bagaimana celah ini terpicu. Biasanya jika malicious script bisa tersimpan secara permanen akan disebut sebagai XSS Persistent dan sedangkan jika tidak tersimpan di database biasa disebut dengan istilah XSS Reflected.

Seiring berkembangnya teknologi dan bagaimana antar teknologi saling berintegrasi (microservice) akhirnya bermunculan teknik-teknik baru. Beberapa diantaranya adalah XSS Blind dan XSS DOM Based.

Untuk proses pembelajaran kita bisa menggunakan lab DVWA yang bisa dipersiapkan dengan perintah berikut :

```sql
docker run --rm -it -p 31331:80 vulnerables/web-dvwa
```

Setelah dijalankan kita akan bisa membuka halaman DVWA melalui alamat [http://localhost:31330](http://localhost:31330/) dengan web browser.

![](https://lh5.googleusercontent.com/dRTlDo5ttTWQ2ThisCQdYggrKWiF2KWqxCUWdvpZ28sn1TTokEnvzd4fUipDjFIj4Zd_UBchcIRxHnnSdmvpkduoCa6p0FW9fxgh666CSKKIsT5knaKYvLuA9BU1NyEWbeJzqCOQiA5kPhEfDEwnOLMBu1k)

Kalian bisa melewati halaman login dengan memanfaatkan celah SQL Injection berikut :

Username : **admin**
Password  : **‘ or 1=1--**

Selanjutnya akan muncul halaman setup DVWA, kalian cukup mengklik tombol **create / reset database**
Dan setelah ini web DVWA siap untuk kita gunakan dalam pembelajaran dan sekedar informasi tambahan default password DVWA username **admin**
dan password adalah **password**

![](https://lh3.googleusercontent.com/pjryOOW5MMwGcebyTxY636StXwLR3QiFHLkr8Q8GnRpdwxbccoHs-HZa2V_yqF86wnq5a0Ru4P66yvhjHJ3kwTff11ic96psABuTrtdILygUNLjsaf-3cEBXGeQV-VK0fNL8sBZb81Qgro_SKmBFERzsYO0)

## **XSS Persistent**

Serangan Persistent Cross-site Scripting (Stored XSS) mewakili salah satu dari tiga jenis utama Scripting Cross-site. Dua jenis serangan lain dari jenis ini adalah Non-Persistent XSS (Reflected XSS) dan XSS berbasis DOM. Secara umum, celah XSS Persistent memungkinkan kita menyuntikkan malicious script ke dalam database aplikasi web. Sehingga script tersebut tersimpan secara permanen.

![](https://lh4.googleusercontent.com/r6BfsOrtmMNJfNnwWWMAHidfCdnbH6hlrv8TDWoqQxKHPJ3hJZ8LyCSmtkfXBI1FXFot9PXd6PjxfknxmKE7hkIbfgoA6pf_Zuxnxx-HyiZM1jN7huI5Wfl-l8smGKFzN4nKZQ3dPgAUHStUTBDQmWEe3B8)

Seperti dalam kasus sebagian besar serangan berbasis web, mengeksploitasi kerentanan Persistent XSS memerlukan beberapa penelitian untuk bisa menemukannya. Jenis situs web tertentu lebih rentan terhadap kerentanan seperti itu karena memungkinkan pengguna untuk berbagi konten. Sebagai contoh :

- XSS pada facebook ( [https://opnsec.com/2018/03/stored-xss-on-facebook/](https://opnsec.com/2018/03/stored-xss-on-facebook/) )

Tidak seperti XSS Reflected, XSS persisten tidak memerlukan fase rekayasa sosial. Korban serangan ini tidak perlu terpikat untuk mengklik tautan yang dibuat. Namun, ketika mengeksploitasi kerentanan Persistent XSS, penyerang sering mencoba untuk mendapatkan lebih banyak korban untuk mengunjungi halaman web yang rentan sehingga mereka mengirim pesan spam atau mempromosikan halaman di jejaring sosial.

Nah untuk latihan pertama ini dengan DVWA, kalian bisa membuka alamat [http://localhost:31331/vulnerabilities/xss_s/](http://localhost:31331/vulnerabilities/xss_s/). Dalam halaman ini tersedia buku tamu untuk diisi oleh pengguna. Langkah pertama yang akan kita lakukan adalah mencoba apakah aplikasi web tersebut mengimplementasikan input validation dengan mengirimkan data seperti gambar dibawah ini.

![](https://lh6.googleusercontent.com/KW2YnlpqyEfVs7avLcDlRZjfQtW-YVWahkhH2zWnWIqW2cEh2HY-1xkNo7EccuR_IW9Tv8w7dtfQBHvMOqLlAEfcyIuCmgDYaGrNq7ACY4VgIgneTiNL27Z5QouVHdvqussUNcqjetvQWZmg6w6Czsi6_Hc)

Setelah kalian mengirimkan data seperti pada gambar diatas. Kalian akan menemukan bahwa kode HTML yang kalian suntik melalui form guest book tersebut tidak dihilangkan ataupun di encode. Sehingga hasilnya akan seperti ini :

![](https://lh5.googleusercontent.com/TzIwPhqjHg03x5ay8_usRwriMEgNF6o2NBAwqCR4ru-Gtxy2vDj5Tjh8BP477_HSa6xnxeevPIJVZQZC5fihFg79qBLw55qHnkK0GEn9XX4DWixE8KrW1LHnUnYPI4UZQBcC96XrslMBrwWo3BE6bGX8ISQ)

Bisa kalian lihat ? teks “ini adalah tebal” tampil dalam format bold sesuai dengan HTML tag yang kalian suntik pada aksi sebelumnya.

Langkah berikutnya kita harus memastikan apakah kode javascript juga bisa disuntik melalui fitur tersebut atau tidak. Payload yang akan kita kirim sesuai pada gambar dibawah ini.

![](https://lh3.googleusercontent.com/V54-5WPV3iarmAho_JMEffEaA8BojU2gibHVbCfGyTgtjg5Af8H6Vs3Wzd1jzERN4dEHvWMt5h9ZhRkh9xs_lcqRNEpakZXIsIBQqhr-30SBu_ixahBtvH7a0wU0RIh8L8Pj7DYHaL3ZccLRyohYjNgeIuk)

Jika payload diatas sudah kalian kirim dengan menekan tombol **Sign Guestbook**, apabila muncul alert maka sudah jelas bahwa javascript bisa tersimpan dan tereksekusi di browser pengguna.

![](https://lh5.googleusercontent.com/9U4qwaVTlE6xuuvD50DiDuKhqbUXaYdzQMrXxT8--fQDKWRc-h-kE8oNFhGxi3qyqZKv106zGiC-U73cx3eAVODETTL0al7Z-QS9NErmG_jnH13niwjuZq2DvHtx1pNwohYujk6Km_4f0I2sXFt-lORf1SA)

Bisa kita tarik kesimpulan, dengan adanya celah XSS ini kita bisa menyuntikkan berbagai macam hal seperti HTML bahkan hingga javascript. Artinya jika javascript dibuat untuk mencuri cookie maka penyerang akan bisa melewati proses autentikasi tanpa perlu kredensial username dan password. Sedangkan jika mau, kita bisa memaksa browser pengguna untuk melakukan aksi-aksi tertentu tanpa disengaja oleh pengguna dengan menginjeksi kode javascript tertentu.

Nah agar lebih seru, teman-teman bisa loncat ke materi **XSS Attack** di modul ini ****untuk mencoba jenis-jenis payload apa yang bisa kita gunakan.

1. ***Exercises***
- Pelajari jenis payload yang bisa kalian coba, dan dokumentasikan !
- Selain XSS, temukan celah lain yang ada di halaman guest book tersebut ! Dan berikan penjelasannya.

## **XSS Blind**

Kerentanan XSS blind adalah varian dari kerentanan XSS persisten. Hal ini terjadi ketika input penyerang disimpan oleh server web dan dieksekusi sebagai skrip berbahaya di bagian lain aplikasi atau di aplikasi lain.

![](https://lh3.googleusercontent.com/uPvl07PjedpHqQrSGw_TPyDEQ2E-8Ngk-9aw_FLT1ZIKtWa1ARignDu9g-5EnJoUZ1hFFrcAQyUr29ZpMHORx3E-wMBXvRFfuaKYDNeuEMQB7iUXqEQh3hhDh0P4KcMyHnV659UhcQSEOoKgf-TZ2N5wJyc)

Gambar: Ilustrasi Blind XSS Vulnerability

Misalnya, penyerang menyuntikkan payload berbahaya ke halaman kontak / umpan balik dan ketika administrator aplikasi sedang meninjau entri umpan balik, payload penyerang akan dimuat. Input penyerang dapat dieksekusi dalam aplikasi yang sama sekali berbeda (misalnya aplikasi internal di mana administrator meninjau log akses atau pengecualian aplikasi).

## **XSS Reflected**

XSS adalah jenis XSS tertentu yang skrip jahatnya memantul dari situs web lain ke peramban korban. Itu dilewatkan dalam kueri, biasanya, dalam URL. Itu membuat eksploitasi semudah menipu pengguna untuk mengklik tautan.

Dibandingkan dengan XSS Persistent, XSS Non-Persistent hanya membutuhkan skrip berbahaya untuk ditambahkan ke tautan dan pengguna mengkliknya.

Pada DVWA kita bisa menemukan kerentanan XSS Reflected dengan mengakses URL sebagai berikut :

```bash
http://localhost:31331/vulnerabilities/xss_r/?name=<**script**>alert(1);</**script**>
```

Kalian bisa mengganti payload **<script>alert(1);</script>** dengan payload lain.

Cara penyerangan XSS Reflected bisa kita lakukan dengan memanfaatkan Social Engineering ke pengguna. Kita mengirimkan via email link tersebut agar diklik oleh pengguna sehingga malicious script akan berhasil tereksekusi.

## **XSS DOM-Based**

Sedangkan untuk DOM yang sering dikenal dengan Document Object Model. Document Object Model (DOM) digunakan sebagai antarmuka pemrograman untuk dokumen HTML dan XML.

Ini mewakili halaman sehingga program dapat mengubah struktur dokumen, gaya (CSS style), dan konten secara dinamis. DOM mewakili dokumen sebagai nodes dan objects. Dengan begitu, bahasa pemrograman dapat terhubung ke halaman.

![](https://lh3.googleusercontent.com/ZH16viG501R_KV9v05RiKwTUL2YmpW7QB4HSjHyEkIPOGdNjxsuZ5ORhyc4qOzIJfNoPMasMi7GaDzauAIPsL1FfozUHRoKtdgB2lQb9iLUnzgxhXXZ5DgsdS_iRpNcdQqNbpx2YKqFVhNV96cAQExht27Q)

Gambar: Ilustrasi DOM

Jika kalian tertarik mendalami DOM silahkan bisa menelusuri referensi berikut :

1. [https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
2. [https://www.petanikode.com/javascript-dom/](https://www.petanikode.com/javascript-dom/)
3. [https://www.duniailkom.com/tutorial-belajar-javascript-pengertian-core-javascript-dan-dom-document-object-model/](https://www.duniailkom.com/tutorial-belajar-javascript-pengertian-core-javascript-dan-dom-document-object-model/)

Nah, pada DVWA letak kerentanan terdapat di bagian potongan kode dibawah ini :

![](https://lh4.googleusercontent.com/nWFXz_6NtsTZ_DyPKN05EuQLBkJBRASMoLr4VxbtvMeR7Pg9BVvhBW0332duZwxB7ZIIQyjVpDmzIGXx4mhkIA_0g3XNYmCSOrKN6MW33BhMP7BHyDjoP6jWeou7hLTFpYXSpCfI4XbWk5QsqyZrJpvpIXo)

Variabel **lang** pada potongan javascript diatas untuk mengambil nilai dari parameter **default** yang berada di address bar browser kalian. Kemudian nilai tersebut ditulis ke dalam HTML melalui document.write. Karena tidak adanya input validation, sanitization, ataupun encoding hal ini menyebabkan XSS DOM based muncul.

Untuk mengeksploitasinya sama seperti XSS Reflected yakni kita memberikan malicious script pada URL. Contohnya sebagai berikut :

```bash
http://localhost:31331/vulnerabilities/xss_d/?default=English<**script**>alert(1);</**script**>
```