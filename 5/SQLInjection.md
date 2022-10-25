# SQL Injection

SQL Injection merupakan celah aplikasi web yang memungkinkan penyerang menyuntikkan SQL query. Ini umumnya memungkinkan penyerang untuk melihat data yang biasanya tidak dapat mereka ambil melalui fitur aplikasi web. Dalam banyak kasus penyerang dapat memodifikasi, atau menghapus data, bahkan bisa menjalankan command shell tertentu tergantung DBMS yang dipergunakan.

![](https://lh6.googleusercontent.com/KnU4ZRm6o508wvWfgJocu_awb_f0Z-Ker9wTDUps80vx7Wxtg3zPlhnu86Aot8rSmlWddKEFpN4vO0Shzd3-bWmUJfXq4GWB5SWP_aq7cRC5dRnc-_tLsT3ez8bJu_l8iGnlvWQqbADe05vAxgwnXFWa8Kk)

Gambar: Ilustrasi SQL Injection

Agar lebih memahami lebih jelas, dibawah ini tersedia potongan source code PHP yang didalamnya terdapat kerentanan SQL Injection :

```php
$id = $_GET['id'];  	 
$data = DB::select("select * from data where id = '$id'");
```

Bisa, kalian perhatikan diatas bahwa variabel ID didapatkan dari HTTP GET parameter. Kemudian ID tersebut dimasukkan dalam SQL Query tanpa ada validasi, sanitasi, ataupun encode. Alhasil kita bisa menyuntikkan perintah SQL ke dalam DB.

Untuk mempelajari mengenai SQL injection ini kalian bisa membaca referensi berikut, agar bisa mengerjakan project yang diberikan.

- [SQL Injection](https://www.w3schools.com/sql/sql_injection.asp)
- [What is SQL Injection? Tutorial & Examples | Web Security Academy](https://portswigger.net/web-security/sql-injection)

<center>

<iframe width="560" height="315" src="https://www.youtube.com/embed/fiq59DuhY68" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</center>