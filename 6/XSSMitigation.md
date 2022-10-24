# XSS Mitigation

## **Input Validation**

Setiap data yang diberikan oleh pengguna harus melalui validasi. Tentunya kita harus mendefinisikan kriteria data yang akan diterima, misalkan saja kita menerima hanya huruf. Sehingga jika pengguna mengirimkan data selain huruf maka server akan menolak data tersebut dan memberikan informasi mengenai alasan kenapa data tersebut tidak diterima.

## **Input Sanitization**

Sanitasi merupakan teknik untuk menghilangkan data yang tidak sesuai dengan kriteria yang sudah ditentukan. Bisa kita contohkan jika kriteria data yang masuk adalah berupa angka, maka jika pengguna mengirimkan data berupa kombinasi angka dan huruf selanjutnya server akan menghapus semua huruf dan meneruskan angka untuk ditangani ke proses selanjutnya.

## **Input Encoding**

Encoding sering digunakan jika kita mengharapkan apapun yang diberikan pengguna bisa diterima, namun perlu mekanisme pencegahan agar script berbahaya tidak berjalan di browser pengguna. Maka dari itu teknik encoding atau escaping diperlukan agar memenuhi kondisi seperti ini.

Teknis mengenai cara mitigasi celah XSS bisa kalian telusuri standar OWASP berikut :

1. [https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)