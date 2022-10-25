# Asymmetric Encryption

Kekurangan dari enkripsi simetris tidak cocok digunakan pada layanan yang memiliki banyak pengguna. Sebagai contoh sebuah website yang pengunjungnya merupakan user yang tidak kita kenal.

Meski kita tidak mengenal siapa yang mengunjungi web kita, tapi kita memiliki tanggung jawab untuk mengamankan transmisi data. Apabila transmisi data di menggunakan enkripsi simetris sama saja semua orang harus tahu kuncinya bukan ? Nah, jika semua memiliki kunci enkripsi berarti semua bisa melihat data yang ditransmisikan orang lain.

Untuk mengatasi kebutuhan tersebut maka enkripsi asimetris ini dibutuhkan karena terdapat 2 jenis kunci. Kunci yang saya maksud adalah kunci publik (public key) dan kunci privat (private key). Lebih jelasnya berikut perbedaan dua kunci tersebut :

1. **Public key**

    Kunci ini digunakan untuk melakukan enkripsi saja, bebas untuk disebarkan melalui berbagai media.

2. **Private key**

    Kunci ini bisa digunakan untuk melakukan enkripsi dan dekripsi. Karena bisa melakukan dekripsi maka kunci ini tidak boleh tersebar.

Penerapan enkripsi asimetris banyak dipergunakan untuk melayani pengguna seperti transmisi data pada Whatsapp, Telegram, HTTPS, git, dan masih banyak lagi.

![](https://lh3.googleusercontent.com/lbtNEh5BB3JirM-99EsdA6GwZfJpq6-H4Ejj0GcIvDZTab6yMWTGDbxI3sEkdrzMrg4mAjyvu-FjyOqCDwCjM1a-olG8RI2BzhaxRE-ZG0nNjTuM8a9I-5Kdtj6gUI99CQ0isH5UMRaeLf-enV8MyaGTqQE)

Sebelum terjalinnya komunikasi antar pengguna dan server perlu saling bertukar kunci publik agar enkripsi bisa dilakukan secara aman. Untuk demonstrasi materi ini kita akan lakukan dengan tools OpenSSL :

1. Sebagai Alice (nama samaran) anda perlu membangkitkan kunci publik dan privat.

    ```bash
    $ openssl genrsa -out private.key 2048
    $ openssl rsa -in private.key -pubout -out public.key
    ```

2. Kirimkan public.key kepada rekan anda bernama Bob

3. Di komputer Bob gunakan public key milik Alice untuk mengenkripsi file

    ```bash
    $ openssl rsautl -encrypt -pubin -inkey public.key -in plaintext.txt -out encrypted.txt
    ```

4. Bob selanjutnya perlu mengirim file yang sudah terenkripsi ke Alice

5. Step terakhir Alice perlu melakukan dekripsi file

    ```bash
    $ openssl rsautl -decrypt -inkey private.key -in encrypted.txt -out plaintext.txt
    ```

### **RSA**

Enkripsi pada studi kasus diatas menggunakan algoritma RSA. RSA adalah sebuah algoritma berdasarkan skema public-key cryptography. Diberi nama RSA sebagai inisial para penemunya: Ron Rivest, Adi Shamir, dan Leonard Adleman.

RSA dibuat di MIT pada tahun 1977 dan dipatenkan oleh MIT pada tahun 1983. Setelah bulan September tahun 2000, paten tersebut berakhir, sehingga saat ini semua orang dapat menggunakannya dengan bebas.

Nah, lebih sederhananya enkripsi RSA memungkinkan proses enkripsi bisa dilakukan oleh 2 kunci baik privat dan publik. Namun untuk dekripsi hanya bisa dilakukan dengan kunci privat.