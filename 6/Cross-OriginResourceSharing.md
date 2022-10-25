# Cross-Origin Resource Sharing

Cross-Origin Resource Sharing (CORS) adalah mekanisme berbasis header HTTP yang memungkinkan server untuk mengizinkan sharing resource kepada domain selain domain asal. Dalam cross-origin request, browser mengirimkan header yang menunjukkan method HTTP dan header yang akan digunakan dalam permintaan yang sebenarnya.

Contoh request cross-origin adalah kode JavaScript front-end yang disajikan dari [https://domain-a.com](https://domain-a.com/) menggunakan XMLHttpRequest untuk membuat permintaan [https://domain-b.com/data.json](https://domain-b.com/data.json).

![Untitled](Cross-Origin%20Resource%20Sharing%20a0ae9ccd0e1f49d79841b444074742e0/Untitled.png)

Mekanisme CORS mendukung permintaan cross-origin yang aman dan transfer data antara browser dan server. Browser modern menggunakan CORS dalam API seperti XMLHttpRequest atau Fetch untuk mengurangi risiko permintaan HTTP cross-origin.