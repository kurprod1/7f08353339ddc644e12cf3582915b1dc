# Symmetric Encryption

Created: June 22, 2022 1:17 PM

Jika kita berbicara enkripsi pada sudut pandang kunci atau password sebenarnya enkripsi terbagi menjadi 2 jenis. Yang pertama adalah enkripsi simetris dimana diperlukan password dan algoritma yang sama untuk membalikkan ciphertext menjadi plaintext.

Enkripsi simetris biasanya dibutuhkan untuk mengamankan informasi untuk kebutuhan beberapa pengguna saja. Misal Adi mengirimkan ke Dian informasi rahasia yang algoritma dan sandi sudah saling mengetahui.

1. **Data Encryption Standard (DES)**

Algoritma DES merupakan salah satu enkripsi simetris dengan ukuran blok 64 bit (8 byte atau maksimal 8 karakter) dan ukuran kunci juga sama 8 byte (harus 8 karakter).

Untuk mempelajari secara langsung bisa kalian coba enkripsi perintah berikut :

```bash
cd EncryptionByExample/SymmetricEncryption/DES
echo "Ini pesan yang sangat rahasia" > ciphertext.txt
python des_encryption.py admin123 plaintext.txt ciphertext.txt
```

Setelah kalian menjalankan program tersebut file ciphertext.txt akan dibangkitkan dan berisi teks yang sudah terenkripsi dari proses sebelumnya.

Dan untuk mengembalikan ciphertext menjadi plaintext kembali, kalian bisa menjalankan perintah berikut :

```bash
python des_decryption.py admin123 ciphertext.txt
Results: Ini pesan yang sangat rahasia
```

Untuk referensi lebih lanjut bisa teman-teman pelajari secara mandiri di URL berikut : [https://academic.csuohio.edu/yuc/security/Chapter_06_Data_Encription_Standard.pdf](https://academic.csuohio.edu/yuc/security/Chapter_06_Data_Encription_Standard.pdf)

1. **Advanced Encryption Standard (AES)**

AES banyak ditemukan di implementasikan di banyak aplikasi. Itu karena telah menjadi standar global enkripsi dan digunakan untuk menjaga keamanan komunikasi dalam jumlah yang signifikan.

[https://lh6.googleusercontent.com/r-Runoy_o_IOzSXQ2l8kMen6NU-V5SIksn8xpxt-jLc-4Ic3JtofsS3TMgSI0clbIi7a3qOS1jKOgyZYeYhvvnVoctncrFdnXpRNqE6ugmsdJiKivCJQc2XrCF57Xgl3k-UeEDHygRViwP2HdHlYSw65_gE](https://lh6.googleusercontent.com/r-Runoy_o_IOzSXQ2l8kMen6NU-V5SIksn8xpxt-jLc-4Ic3JtofsS3TMgSI0clbIi7a3qOS1jKOgyZYeYhvvnVoctncrFdnXpRNqE6ugmsdJiKivCJQc2XrCF57Xgl3k-UeEDHygRViwP2HdHlYSw65_gE)

Advanced Encryption Standard (AES) memiliki keunggulan kecepatan dan keamanan yang lebih baik. Beberapa aplikasi seperti Whatsapp, AES digunakan untuk mengenkripsi history chat yang tersimpan di local storage Android.

Sedangkan untuk praktik kita bisa menjalankan contoh program yang sudah tersedia dengan perintah berikut :

```bash
$ cd EncryptionByExample/SymmetricEncryption/AES
$ sudo apt install python-crypto
$ python aes_app.py
Key: '`C\x8c\xe0&\xa0\x82W"\xec\xa6\xaa(\xb95\x03\x85\xd8*\x9du\xc7\xec\xb2\xc8\xbej\x86\x13\xe9\xc7\xe0'
Encrypted string: svZO5HeP23qWDwl94J83SijeIJlBv78otRDeP9trNSU=
Decrypted string: password
```

Berbeda dengan DES dimana password berupa string, secara default kunci AES sesuai dengan panjang bit yang kita gunakan misal 128 bit, 192 bit, dan 256 bit.

Agar bisa mendukung kunci string biasa dan panjang bisa sesuka kita maka harus dikombinasikan dengan CBC dan IV untuk membangkitkan ke bentuk block ukuran bit diatas. Lebih jelasnya bisa teman-teman coba dengan perintah ini di folder yang sama seperti materi sebelumnya :

```bash
$ python aes_iv_encryption.py admin "Ini pesan rahasia"
Result : fqvNPzloIG8o9uHcB6rMwpJJhPAIx6njnnKRwNoq8C5KOHAiKz6uycDEDuEluCwe
$ python aes_iv_decryption.py admin fqvNPzloIG8o9uHcB....
Result : Ini pesan rahasia
```

1. **Rivest Cipher 4 (RC4)**

Jika pada materi sebelumnya hasil dari enkripsi terlihat ciphertext sangat berbeda dari plaintext. Namun pada enkripsi ini hanya mengacak posisi data yang ada. Sehingga enkripsi ini lemah dibanding dengan AES maupun DES.

```bash
$ cd SymmetricEncryption/RC4
$ python rc4-encrypt.py
Key : "iL\xd9mu\xefOQ\xa9\x85/@\n'\xe4C;{C\xeb\x83\x077\xb30\x95+\xef\x96\x8b\x9f\xd2"
Ciphertext : '!-\x89\x9bb\xe2\xeeQ\x90\xacJ\xf4\xb8\xc0j'
Decrypted Text: RC4 test hehehe
```