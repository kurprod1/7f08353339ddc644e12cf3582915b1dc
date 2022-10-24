# Pengenalan Cryptography

Created: June 22, 2022 1:17 PM

Dalam bahasa indonesia biasa disebut dengan kriptografi, bidang ini mempelajari tentang menerapkan perlindungan informasi. Mekanisme penerapannya bisa menggunakan algoritma programming, tapi bisa juga dalam bentuk lain seperti aturan dan definisi bahkan bisa juga dalam bentuk instrumen elektronika.

[https://lh5.googleusercontent.com/6o4tyoR-X9Oesz0pqOfs7rwnQiYoO_Q9JYqcuWqDVH4axrOOUmkLWTaqhst8eEk2VVaXnNbv9iW0nwDV2E2VTODk5oq_uQYmQPgjCAkVzbz9Wedo8EbM9-hGYtFemRViF3X6pXTXztNDU8cIcsMwJ8eOsD8](https://lh5.googleusercontent.com/6o4tyoR-X9Oesz0pqOfs7rwnQiYoO_Q9JYqcuWqDVH4axrOOUmkLWTaqhst8eEk2VVaXnNbv9iW0nwDV2E2VTODk5oq_uQYmQPgjCAkVzbz9Wedo8EbM9-hGYtFemRViF3X6pXTXztNDU8cIcsMwJ8eOsD8)

Pada proses kriptografi diatas awal mula teks yang masih dalam bentuk orisinil disebut dengan istilah plaintext. Plaintext dimasukkan pada algoritma enkripsi dan diberikan password yang nantinya menghasilkan teks acak berbeda dengan teks aslinya. Teks yang sudah dienkripsi ini disebut dengan istilah chipertext.

Nah, ciphertext yang sudah didapatkan pada proses sebelumnya bisa kita kirimkan melalui jaringan. Hal ini tidak menjadi masalah karena kerahasiaan informasi terjamin oleh kekuatan enkripsi tersebut dan password yang hanya diketahui oleh orang yang berhak. Sehingga penerima ciphertext untuk bisa mendapatkan plaintext harus melakukan decryption.

Decryption merupakan proses untuk mengubah ciphertext menjadi dalam bentuk plaintext kembali. Namun untuk keberhasilan proses decryption diperlukan algoritma dan password yang sama.

Dan sebagai tambahan, dalam dunia cyber security selain Enkripsi juga ada teknik lain untuk menyembunyikan teks asli yakni Hash function. Hash berbeda dengan enkripsi dimana enkripsi masih memungkinkan untuk dibalikkan prosesnya untuk mendapatkan plaintext. Namun pada hash tidak ada metode mengembalikannya ke bentuk plain text, satu-satunya hanya menggunakan teknik brute-force.

Sebelum memulai materi mengenai enkripsi kalian persiapkan terlebih dahulu harus mempersiapkan tool enkripsi dengan perintah berikut :

```bash
git clone https://github.com/ne0z/EncryptionByExample.git
```