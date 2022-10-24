# Hash Function

Created: June 22, 2022 1:17 PM

Hash memiliki keunikan sendiri dimana hanya memiliki 1 jalan (one way). Artinya sekali plaintext tersebut diubah menjadi hash maka tidak ada algoritma untuk membalikkan ke bentuk semula. Selain itu hash tidak memerlukan sandi, artinya hash dibuat bukan untuk berbagi informasi secara aman.

Penggunaan Hash sering digunakan untuk validasi keutuhan dan keaslian data. Sebagai contoh pada penyimpanan password dalam database. Server tidak perlu menyimpan password asli tetapi mereka hanya butuh apakah sandi yang dikirimkan pengguna merupakan sandi yang sesuai atau tidak.

[https://lh5.googleusercontent.com/5DIbx2lYj3D1tSyL0nI6tR7eG_f-0hp6dfyKkiIlDP5B1JD3ZnQyT-p6hvfd3caG_YiUU9IxlQdZHPrEHHDnbI8RfDdCxeWC28MTVJnbUjX4DvxPvuOo3VVu6kBUskW0pC6L8Qu6hetKoAqP60H8smuyJ6U](https://lh5.googleusercontent.com/5DIbx2lYj3D1tSyL0nI6tR7eG_f-0hp6dfyKkiIlDP5B1JD3ZnQyT-p6hvfd3caG_YiUU9IxlQdZHPrEHHDnbI8RfDdCxeWC28MTVJnbUjX4DvxPvuOo3VVu6kBUskW0pC6L8Qu6hetKoAqP60H8smuyJ6U)

Pada gambar diatas kata **FOX** setelah dimasukkan ke dalam algoritma hash menjadi **DFCD3454**. Sehingga jika FOX merupakan password maka proses validasi hanya membandingkan hash yang dikirim oleh pengguna dengan hash yang tersimpan didalam database.

1. **MD5 HASH**

Algoritma hash ada banyak sekali salah satunya adalah MD5 yang memiliki ciri-ciri panjangnya 128 bit ( 32 byte ). Contoh perintah untuk membangkitkan hash sebagai berikut:

```bash
$ echo -e "admin" | md5sum | awk '{print $1}'456b7016a916a4b178dd72b947c152b7
```

Dan untuk membangkitkan hash MD5 pada suatu file bisa kita gunakan perintah berikut :

```bash
$ md5sum /etc/passwd
```

1. **SHA1 HASH**

Untuk SHA1 memiliki panjang 160 bit ( 40 byte ) artinya panjang dari hash ini sebanyak 40 karakter. Cukup mudah bukan untuk mengidentifikasi jenis hash?

```bash
$ echo -e "admin" | sha1sum | awk '{print $1}' 4015bc9ee91e437d90df83fb64fbbe312d9c9f05
```

Dan untuk membangkitkan SHA1 hash dari suatu file sama seperti sebelumnya :

```bash
$ sha1sum /etc/passwd
```

Selain sha1 ada juga pengembangannya yakni :

- sha224sum
- sha256sum
- sha384sum
- sha512sum