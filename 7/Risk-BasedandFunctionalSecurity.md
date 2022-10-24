# Risk-Based and Functional Security Testing

Created: June 22, 2022 1:17 PM

Kita sebelumnya sudah belajar cara membuat automation script dengan Postman. Kali ini kita akan optimalkan penggunaan aplikasi ini untuk melakukan automation security testing.

Dari source code (link sudah disertakan di Persiapan lab) ternyata memiliki kerentanan SQL Injection pada proses authentication.

[https://lh6.googleusercontent.com/dI4WlVK5xNZHkozIrY64ih2Og5Kf2nbGAzyfuTQQrgpsH8xjl8lfKWqIPMS9reeH358smrXehQFgVEbzXbMVe49wlQwsBG0KWWhVeTOJYA7Lb-o6WEkZKmGWdbzY6Q-fwEKp5LAkJOLmM-dGqTM5HABqCdI](https://lh6.googleusercontent.com/dI4WlVK5xNZHkozIrY64ih2Og5Kf2nbGAzyfuTQQrgpsH8xjl8lfKWqIPMS9reeH358smrXehQFgVEbzXbMVe49wlQwsBG0KWWhVeTOJYA7Lb-o6WEkZKmGWdbzY6Q-fwEKp5LAkJOLmM-dGqTM5HABqCdI)

Untuk link detailnya bisa kalian akses di [https://s.id/lknuW](https://s.id/lknuW)

Dari informasi penting tersebut seharusnya akan terjadi error apabila nama pengguna kita tambahkan tanda kutip.

[https://lh6.googleusercontent.com/Nt8Nit1WnheaUSqDp44BZmAGyCP8fg6R2O4Wnw7fGReupIF7bjcX7ZYf5-m8pA0EF1iBhmgwkanDIGNQQjpMz7Kb5z0m03P-lzu8Kfx13HUjwWla5Gt4fNneNBkWIZiaAtF5VUJJI4fxZ3qq6pKQ3Iv7mPw](https://lh6.googleusercontent.com/Nt8Nit1WnheaUSqDp44BZmAGyCP8fg6R2O4Wnw7fGReupIF7bjcX7ZYf5-m8pA0EF1iBhmgwkanDIGNQQjpMz7Kb5z0m03P-lzu8Kfx13HUjwWla5Gt4fNneNBkWIZiaAtF5VUJJI4fxZ3qq6pKQ3Iv7mPw)

Nah kita sudah berhasil menemukan SQL Injection dengan cara menambahkan tanda kutip. Agar lebih yakin, kita bisa coba juga dengan menambahkan **‘ or ‘’=’**.

[https://lh4.googleusercontent.com/Z2_pkHIsze1UZmdbicWFf1UzNA7iXCBaCq6rkvOFBtmLETHTdx6XqTwD7RJ7TPi-c0cmoV0zr5SKfY0f-AJdSwLl3B6FwEKBdhiE6b-hVmTpGY9XTWO9rWhao-FPF29SmGz4Usv7hzfiguexY9iD1XXQt_A](https://lh4.googleusercontent.com/Z2_pkHIsze1UZmdbicWFf1UzNA7iXCBaCq6rkvOFBtmLETHTdx6XqTwD7RJ7TPi-c0cmoV0zr5SKfY0f-AJdSwLl3B6FwEKBdhiE6b-hVmTpGY9XTWO9rWhao-FPF29SmGz4Usv7hzfiguexY9iD1XXQt_A)

Bisa kalian lihat bukan hasil penambahan **‘ or ‘’=’** ternyata bisa mensiasati autentikasi dan kita berhasil login.

# **Automation Security Testing**

Pada materi ini kita akan melanjutkan hasil uji coba pada materi sebelumnya dengan menyempurnakan proyek Postman kita.

1. Kita buat collection baru dengan menduplikasi collection sebelumnya cukup tekan **CTRL+D** pada collection **authentication-service**.

[https://lh6.googleusercontent.com/X_L8ad0uFr9QCwf6oFneaScrYhTs72NSySb0WVppZEeZtMQZEbKljKb84CvN-t5Bgt5pwxlSILGuaMOn37J0WUbW8u1WIaMFbfk02dDeVCx7zzgDVIjMeLb2G96YxfAFFzCEaLz2lgyHlO3ept5qJVS3XE8](https://lh6.googleusercontent.com/X_L8ad0uFr9QCwf6oFneaScrYhTs72NSySb0WVppZEeZtMQZEbKljKb84CvN-t5Bgt5pwxlSILGuaMOn37J0WUbW8u1WIaMFbfk02dDeVCx7zzgDVIjMeLb2G96YxfAFFzCEaLz2lgyHlO3ept5qJVS3XE8)

Lalu ubah nama **authentication-service Copy** menjadi **authentication-service-vulnerability.**

Pada folder **users** kita ganti dengan nama bug kita yakni **AUTH-2020-07-0001: SQL Injection** dengan tujuan sebagai berikut :

1. AUTH	: Merupakan nama platform yang kita test
2. 2020	: Tahun kita mengidentifikasi celah ini
3. 07	: Bulan kita mengidentifikasi celah ini
4. 0001	: Urutan ke berapa celah kalian temukan. Berhubung ini pertama kali menemukan bug di bulan Juli maka saya tulis 0001
5. SQL Injection	: Keterangan nama celah

Format penulisan nama celah tersebut sebenarnya tidak wajib, kalian bisa membuat format sesuai selera kalian. Sedangkan untuk format diatas digunakan penulis modul ini sesuai dengan pengalaman untuk memudahkan pencarian automation test script jika sewaktu-waktu dibutuhkan.

[https://lh3.googleusercontent.com/k81KHSO7tlS1qkHhK05mHVTKfkPreHMDPEnzI0fJUQrGj2UuNqBI7W0LyIyW__ED9rd6ndWuI7icgiqBWzKhB_JxRuEleDAbqMXIyZzz7T7xmSppCvcwgjqaCMKtZMuxlDVC6lR-RIsKRkqn7XrX49vvLg4](https://lh3.googleusercontent.com/k81KHSO7tlS1qkHhK05mHVTKfkPreHMDPEnzI0fJUQrGj2UuNqBI7W0LyIyW__ED9rd6ndWuI7icgiqBWzKhB_JxRuEleDAbqMXIyZzz7T7xmSppCvcwgjqaCMKtZMuxlDVC6lR-RIsKRkqn7XrX49vvLg4)

Dan untuk body raw pada **01. Step to reproduce** sebagai berikut :

[https://lh6.googleusercontent.com/Bu6NpEME6hQkNHSWRnf6_e5REzUup_TpaM1aNwnbPntX4xTul_J4oQcfJhySDrWyXYqrSG7wyo3ary9zFA6ZVAb20bTzy5kysvdHLlUP8DaZdUhY6yHy64LZDawLUZr5yOGFqw1qjln8Oou0w02j8bmgdRI](https://lh6.googleusercontent.com/Bu6NpEME6hQkNHSWRnf6_e5REzUup_TpaM1aNwnbPntX4xTul_J4oQcfJhySDrWyXYqrSG7wyo3ary9zFA6ZVAb20bTzy5kysvdHLlUP8DaZdUhY6yHy64LZDawLUZr5yOGFqw1qjln8Oou0w02j8bmgdRI)

[https://lh6.googleusercontent.com/xBohGNxlHVdjl2JSgsE3Ew122-yXmuerp8mGTiZP_VR8K77FfWo7MbA_5TgAIW3xidVR-diC5ssvzAVc4tC8C_Y2t49yzUDTC1-bhNO9ZQDfP3fV2YIfc288pvByONQhH3zrAfmoSdx_h9satts1XGjpNO8](https://lh6.googleusercontent.com/xBohGNxlHVdjl2JSgsE3Ew122-yXmuerp8mGTiZP_VR8K77FfWo7MbA_5TgAIW3xidVR-diC5ssvzAVc4tC8C_Y2t49yzUDTC1-bhNO9ZQDfP3fV2YIfc288pvByONQhH3zrAfmoSdx_h9satts1XGjpNO8)

Jika semua sudah siap kalian bisa menekan icon play  >  pada **authentication-service-vulnerability** hingga muncul tombol **Run** seperti dibawah ini.

[https://lh5.googleusercontent.com/R-07GukflEfxB6r74aIRQRfaE4mR39-1mwZh_SgVXsuCil6Xm9Ymsp5ILFdSNLDjNGg-XXMi6-VaVaB2MoDaNKjYXlO0WfWzOz00v7anZIOK6uP6Qliz6_jthqYwKJ9YzjTzMUOaSoENxwERV7NAhFS4ZqQ](https://lh5.googleusercontent.com/R-07GukflEfxB6r74aIRQRfaE4mR39-1mwZh_SgVXsuCil6Xm9Ymsp5ILFdSNLDjNGg-XXMi6-VaVaB2MoDaNKjYXlO0WfWzOz00v7anZIOK6uP6Qliz6_jthqYwKJ9YzjTzMUOaSoENxwERV7NAhFS4ZqQ)

Nah langkah selanjutnya tinggal kalian klik **Run**.

[https://lh3.googleusercontent.com/VysClnyf2C5QhmFSMhIhZS3A0iZ89AcfGYeULGsV4GisulihbRH9aC5BN4fcwD8oXexbgFbGODi_5f8wv2nJZl86d-3RY64MMyV4OadcGeMS0x_xdMP1iyTgXQGtR1Uesn0vnJJuCxwZCs6Xn8BTe9usAtY](https://lh3.googleusercontent.com/VysClnyf2C5QhmFSMhIhZS3A0iZ89AcfGYeULGsV4GisulihbRH9aC5BN4fcwD8oXexbgFbGODi_5f8wv2nJZl86d-3RY64MMyV4OadcGeMS0x_xdMP1iyTgXQGtR1Uesn0vnJJuCxwZCs6Xn8BTe9usAtY)

Dan terakhir tinggal klik tombol **Run authentication…**

[https://lh5.googleusercontent.com/XD9mLaaFhpj0ELvqqeXnZN-zOkjxLxwI-tLT9e2tXKw-45cyj7IBqgJamxaoOuUqfWBEknKKDeoDdOnDZpoC7T9GepAi0F65pJ_k-Ljc7qXvQOlE1MAHSj6zPKlqmLfxwqqXn0AYtVAH6H-Wjk2Wcgg7TqM](https://lh5.googleusercontent.com/XD9mLaaFhpj0ELvqqeXnZN-zOkjxLxwI-tLT9e2tXKw-45cyj7IBqgJamxaoOuUqfWBEknKKDeoDdOnDZpoC7T9GepAi0F65pJ_k-Ljc7qXvQOlE1MAHSj6zPKlqmLfxwqqXn0AYtVAH6H-Wjk2Wcgg7TqM)

Nah status FAIL diatas bukan postman yang error, tapi memang karena sesuai dengan test script yang kita buat jika bug masih ada maka statusnya akan FAIL. Kurang lebih seperti itu, jika nanti kalian diminta untuk tes ulang bug yang sudah kalian temukan lama. Kalian cukup menjalankan Postman dengan beberapa klik tanpa takut lupa ! Mudah bukan ?

Jika ada cara mudah, kenapa kita cari jalan yang sulit ….