# iOS Fundamental

Created: June 22, 2022 1:17 PM

iOS berbeda dengan android yang sudah kita tahu bahwa sistem operasi android menggunakan basis linux. iOS menggunakan basis seperti Unix dan BSD, sehingga kalian harus mempelajari fundamental arsitektur agar bisa memahami perbedaan yang ada.

[https://lh4.googleusercontent.com/E-EV5MvurKdv0oSOcBinRAny-pYLzXyeZsBqGP--llSt2BdF87ZahYPqmQ66ycoc6AJYZ5ArmkMKOjAd7KP80UajdFgwm9lnMP89C4_3dyxfLgtNb8tqdLn8hhdpoT4_SapZlTXOy0FMtymnhhzvGr-rwCI](https://lh4.googleusercontent.com/E-EV5MvurKdv0oSOcBinRAny-pYLzXyeZsBqGP--llSt2BdF87ZahYPqmQ66ycoc6AJYZ5ArmkMKOjAd7KP80UajdFgwm9lnMP89C4_3dyxfLgtNb8tqdLn8hhdpoT4_SapZlTXOy0FMtymnhhzvGr-rwCI)

Dari gambar diatas sangat terlihat bahwa arsitektur IOS sangat berbeda dengan android. Terdapat beberapa layer seperti Kernel, Core OS, Core Services, Media dan Cocoa Touch. Sedangkan untuk security model teman-teman bisa mengakses informasi resminya di [https://support.apple.com/guide/security/welcome/web](https://support.apple.com/guide/security/welcome/web)

[https://lh3.googleusercontent.com/ECBO7KYynMIqhfOBITZSFfglhIyP-Z-ehimDa1NF1_UQEQ_8nb3M8ZK6b0lzmRWJcR1fu5Na3KyiDhzRk5QsE3mnonQ7mh_NUv1LR_flptFfvXujB7zSg8X43rO8JPz7XE3pm8BO_X4MFE8oFJrcdpPbY1c](https://lh3.googleusercontent.com/ECBO7KYynMIqhfOBITZSFfglhIyP-Z-ehimDa1NF1_UQEQ_8nb3M8ZK6b0lzmRWJcR1fu5Na3KyiDhzRk5QsE3mnonQ7mh_NUv1LR_flptFfvXujB7zSg8X43rO8JPz7XE3pm8BO_X4MFE8oFJrcdpPbY1c)

Sedangkan untuk kita sederhanakan kembali, kurang lebih security model bisa kita visualisasikan menjadi seperti berikut :

[https://lh4.googleusercontent.com/KXpgueljkBFkAwl0mIFOZ2wcaNrL6S4KD6Cx34IFfrqwNsbCNI3JdJW6GvHIbuVWvmnvPpRkGKjNCdbqLq0IphmJuDipn-tvcQZS4xPV1LWTRo1kraL13FR3L82KJu91rtGhImfrq81J0qOqqnAA53ylijw](https://lh4.googleusercontent.com/KXpgueljkBFkAwl0mIFOZ2wcaNrL6S4KD6Cx34IFfrqwNsbCNI3JdJW6GvHIbuVWvmnvPpRkGKjNCdbqLq0IphmJuDipn-tvcQZS4xPV1LWTRo1kraL13FR3L82KJu91rtGhImfrq81J0qOqqnAA53ylijw)

# **iOS File System Isolation**

Sistem file menangani penyimpanan file data, aplikasi, dan file yang terkait dengan sistem operasi itu secara persisten. Oleh karena itu, sistem file adalah salah satu sumber daya mendasar yang digunakan oleh semua proses.

Perlu kalian tahu sistem file pada produk apple menggunakan APFS dimana sudah menjadi bawaan untuk iOS 10.3 dan yang paling terbaru. MacOS juga mendukung format file sistem lain namun untuk bawaan sudah dipastikan menggunakan APFS.

Sistem file pada iOS memberikan proteksi keamanan sandbox yang cukup mutakhir dengan memisahkan antara aplikasi, data, dan kontainer iCloud. Kurang lebih bisa kalian amati seperti gambar dibawah ini :

[https://lh5.googleusercontent.com/fAoySk2X4VZ94UPIKYFPsw5V9sqF16C9GWoTox3gI6kVakFjCEe98GjjntmBQ_2ichT0gt1G86WZFPwEKBAj64heSdXgtB1MUqq7gGb_Oz1opsokkPSkpNZBG4WIzFsP5Nic0GvaW0JiMKSL95ywIoncE0Y](https://lh5.googleusercontent.com/fAoySk2X4VZ94UPIKYFPsw5V9sqF16C9GWoTox3gI6kVakFjCEe98GjjntmBQ_2ichT0gt1G86WZFPwEKBAj64heSdXgtB1MUqq7gGb_Oz1opsokkPSkpNZBG4WIzFsP5Nic0GvaW0JiMKSL95ywIoncE0Y)

Aplikasi pada umumnya dilarang mengakses atau membuat file di luar direktori kontainernya. Satu pengecualian untuk aturan ini adalah ketika aplikasi menggunakan antarmuka sistem publik untuk mengakses hal-hal seperti kontak atau musik pengguna. Dalam kasus tersebut, sistem framework untuk menangani setiap operasi terkait file yang diperlukan untuk membaca atau memodifikasi penyimpanan data yang sesuai.

# **Application Sandbox**

Aplikasi iOS juga mengimplementasikan konsep sandbox untuk membatasi akses ke sumber daya sistem dan data pengguna di aplikasi iOS untuk mengandung kerusakan jika suatu aplikasi diretas.

App Sandbox memberikan perlindungan ke sumber daya sistem dan data pengguna dengan membatasi akses aplikasi Pengguna ke sumber daya yang diminta.

[https://lh6.googleusercontent.com/nb0RofNWRwiGGHQzCcv5iRTxDAayOtkwhS-hvUps7YDN-hNR-j0TI-tuWocywDiW0nEcPJwpE9VDZPcDX_4Kxq9nOf7AQ570wcFc5phoDX0oJfCdFXqV-hysTqjg0FJdhkfJiMLd2qGpLPbAiT1NGSAKPlc](https://lh6.googleusercontent.com/nb0RofNWRwiGGHQzCcv5iRTxDAayOtkwhS-hvUps7YDN-hNR-j0TI-tuWocywDiW0nEcPJwpE9VDZPcDX_4Kxq9nOf7AQ570wcFc5phoDX0oJfCdFXqV-hysTqjg0FJdhkfJiMLd2qGpLPbAiT1NGSAKPlc)

Sebagai contoh dengan adanya sandbox maka aplikasi 1 tidak akan bisa mengakses atau mengganggu aplikasi 2. Jika teman-teman tertarik untuk mempelajari lebih dalam bisa kalian baca dokumentasi keamanan iOS melalui

[https://developer.apple.com/documentation/security](https://developer.apple.com/documentation/security)