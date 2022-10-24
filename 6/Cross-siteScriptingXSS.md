# Cross-site Scripting (XSS)


Serangan yang dikenal Cross-Site Scripting (XSS) merupakan salah satu dari tipe injection,
dimana script berbahaya disuntikkan ke dalam website yang terpercaya. Serangan XSS
terjadi ketika penyerang menggunakan aplikasi web untuk mengirimkan kode berbahaya,
umumnya kode tersebut merupakan script yang bisa berjalan di sisi browser untuk pengguna
lain.

![Untitled](/6/XSS/Untitled.png)

XSS terjadi disebabkan karena tidak adanya filter mengenai data yang dikirimkan dan yang
akan ditampilkan ke pengguna lain. Perlu menerapkan teknik input validation, sanitization,
atau encoding sehingga data yang berbahaya bisa tersaring dengan baik.
Mengenai celah XSS, perlu kalian ketahui ketika kita bisa menyuntikkan javascript ke dalam
halaman web. Tentu banyak hal yang bisa kita lakukan seperti :

- Mencuri cookie pengguna untuk mendapatkan sesi autentikasi (take over user
account).
- Memaksa browser untuk melakukan permintaan tertentu (XSS + CSRF)
- Mengambil alih komputer pengguna dengan memanfaatkan exploit browser

Tentu selain 3 hal diatas masih banyak aktivitas yang bisa dilakukan penyerang sesuai
kreativitas terhadap kemampuan attack vector-nya.