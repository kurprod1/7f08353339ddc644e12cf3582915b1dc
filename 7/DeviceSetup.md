# Device Setup

Created: June 22, 2022 1:17 PM

Di materi sebelumnya kalian sudah memahami konsep dasar file system dan app sandbox yang menjadi persyaratan dasar sebelum memulai mempelajari iOS Penetration testing. Selanjutnya kalian harus mempersiapkan hardware dan software.

# **Jailbreak IOS**

Proses ini untuk mengaktifkan akses root pada iOS sehingga anda bisa leluasa dalam memasang berbagai aplikasi pentest seperti frida dan lain sebagainya. Proses jailbreak secara instan bisa dilakukan menggunakan aplikasi 3utools (windows) atau checkra1n (tersedia untuk linux).

Link Download Jailbreak tools:

1. [https://checkra.in](https://checkra.in/)
2. [http://www.3u.com](http://www.3u.com/)

Penulis merekomendasikan checkra1n karena simpel dan mudah dijalankan, selain itu kalian bisa memasangnya langsung di Kali Linux sehingga tool untuk pentest bisa langsung dijalankan.

Hal pertama yang harus dilakukan yakni membuka aplikasi checkra1n hingga muncul gambar berikut .

[https://lh6.googleusercontent.com/oj3zxqKEjD-YfMSs6zeU20iN5nhSzzrIWda2a7GHxexV6SqtQGTE8TcogaPQSAkbmhDVu8tn_7hZ260DcmgtFX0pbwKpSoyI_9wugC44Q_AykY0VObSa_xYBR2kt5qDY1kH0UfWrxDnTq3bp1OoLU3uO4Bo](https://lh6.googleusercontent.com/oj3zxqKEjD-YfMSs6zeU20iN5nhSzzrIWda2a7GHxexV6SqtQGTE8TcogaPQSAkbmhDVu8tn_7hZ260DcmgtFX0pbwKpSoyI_9wugC44Q_AykY0VObSa_xYBR2kt5qDY1kH0UfWrxDnTq3bp1OoLU3uO4Bo)

Siapkan kabel lightning iPhone dan perangkat iPhone anda. Jika siap kalian bisa melanjutkan dengan mengklik tombol **Start**. Selanjutnya akan muncul tampilan yang berisi panduan apa saja yang harus dilakukan. Dalam hal ini kalian harus mengklik kembali tombol **Start** dan dalam waktu 4 detik kalian harus menekan tombol **Home** dan tombol **Power** ditahan hingga step dua selesai. Langkah terakhir ketika layar menunjukkan anda sudah berada di tahap ketiga kalian harus segera melepas tombol **Power** saja dan tombol **Home**  tidak boleh anda lepas.

[https://lh3.googleusercontent.com/Dj2-Sr8t63l07NmlQqavBBXbwXp_sVgF3rvOpJhT5PDYqwOaKIhb71YhBUFjLLc-4SBdw-DVHa7Xpv6Y2X1jtxW7eMXAhNlyyeBVaPVf8MZy2uFQuwgrKV8iPG9Mr1FCRsN3wM4W2PKEKTrgDxRKAfJhokA](https://lh3.googleusercontent.com/Dj2-Sr8t63l07NmlQqavBBXbwXp_sVgF3rvOpJhT5PDYqwOaKIhb71YhBUFjLLc-4SBdw-DVHa7Xpv6Y2X1jtxW7eMXAhNlyyeBVaPVf8MZy2uFQuwgrKV8iPG9Mr1FCRsN3wM4W2PKEKTrgDxRKAfJhokA)

Gambar diatas merupakan panduan yang sudah kita bahas sebelumnya. Kali ini ketika kalian berhasil melakukan step-step sesuai gambar diatas selanjutnya akan muncul progress bar yang menunjukkan berapa lama proses jailbreak selesai.

[https://lh3.googleusercontent.com/0N6cL3aiJcDs8V_vN6YIY8EGA_w8sR0B9ezKcNqNymxlpZsNbVSitVH3PKHQPxELeDZVENpF11URdv2edMJhl-p0Z3OGddF2aGUZNDqu8ONzdVriRwhipyzpeKvi2oDNde5D2RWtPB_w4YEsiXxY-VPQblE](https://lh3.googleusercontent.com/0N6cL3aiJcDs8V_vN6YIY8EGA_w8sR0B9ezKcNqNymxlpZsNbVSitVH3PKHQPxELeDZVENpF11URdv2edMJhl-p0Z3OGddF2aGUZNDqu8ONzdVriRwhipyzpeKvi2oDNde5D2RWtPB_w4YEsiXxY-VPQblE)

Nah semua proses sudah selesai jika dilihat perangkat iPhone akan memuat ulang iOS untuk beberapa saat. Dan setelah selesai memuat ulang kalian bisa memeriksa kembali di iPhone pasti sudah terpasang aplikasi baru bernama **Cydia** dan **checkra1n**.

[https://lh4.googleusercontent.com/pMGB8RMTK-rIBHHqrke-fO6xLklC54y09T-84pm3-mtFgdw4rDawNf-YXjp47QX3smDa7Tn92dU6bU2MciFQ1s4djx4RNQ_twmp9rmHhE-yDXMWcpb8NQuf-IDIxlLp95qxgOYIE5DllFB7uI_kdllopodM](https://lh4.googleusercontent.com/pMGB8RMTK-rIBHHqrke-fO6xLklC54y09T-84pm3-mtFgdw4rDawNf-YXjp47QX3smDa7Tn92dU6bU2MciFQ1s4djx4RNQ_twmp9rmHhE-yDXMWcpb8NQuf-IDIxlLp95qxgOYIE5DllFB7uI_kdllopodM)

**Cydia** merupakan aplikasi yang mengizinkan kita memasang aplikasi lain dari sumber yang tidak resmi atau bisa kita sederhanakan bahwa **Cydia** seperti App store. Step berikutnya kita harus memasang OpenSSH agar bisa mengakses SSH iPhone. Untuk melakukannya kalian buka aplikasi Cydia dan carilah OpenSSH seperti gambar dibawah ini.

[https://lh6.googleusercontent.com/tr2Rr-52-1CQ0o1S3CsLAK5aEols6w4PDw0FSBImxEDvnfI5sUHBYFKUuXCjtDco_Ga3t2P6O4HnVX-aw18pGflDK-XvubaLQEGeBQdNQgL8n8_sYjMze7HesvQcvtJApmQ4CzCp1zR_etdwqStr2S4NpOw](https://lh6.googleusercontent.com/tr2Rr-52-1CQ0o1S3CsLAK5aEols6w4PDw0FSBImxEDvnfI5sUHBYFKUuXCjtDco_Ga3t2P6O4HnVX-aw18pGflDK-XvubaLQEGeBQdNQgL8n8_sYjMze7HesvQcvtJApmQ4CzCp1zR_etdwqStr2S4NpOw)

Jika muncul seperti gambar diatas silahkan klik **OpenSSH**.

[https://lh3.googleusercontent.com/Z-vHZnXFnT_APU9kgH125DDM2WY6_uw09oR0GNxbsu0lY48uKfEVzPyoKmg2aW2CZTumuJ6_DlTqjuK1Bz0SAFa3K1lAlDARVEmKU2smO52YxGwoSXw8CrlOHNPIsxqTtL_YiJAZsJJeEeqPE8WOzORCUoA](https://lh3.googleusercontent.com/Z-vHZnXFnT_APU9kgH125DDM2WY6_uw09oR0GNxbsu0lY48uKfEVzPyoKmg2aW2CZTumuJ6_DlTqjuK1Bz0SAFa3K1lAlDARVEmKU2smO52YxGwoSXw8CrlOHNPIsxqTtL_YiJAZsJJeEeqPE8WOzORCUoA)

Pada bagian kanan atas muncul tombol **Install**. Klik tombol tersebut untuk memasang OpenSSH di iPhone kalian.

[https://lh6.googleusercontent.com/B-cFAI9t1aKaZnz6rgjmblgXJgXnbeD5PcYaMdverIKSy5wkrQypGbdySx7zHxjoYUav0poSbToAE6JD3IU--yaAiS7xI57MLBWYV64tnwQSBd2DlSTuE9ys71b0TovNAAbuspoxEXD8qb3gxme7zzpt7Jk](https://lh6.googleusercontent.com/B-cFAI9t1aKaZnz6rgjmblgXJgXnbeD5PcYaMdverIKSy5wkrQypGbdySx7zHxjoYUav0poSbToAE6JD3IU--yaAiS7xI57MLBWYV64tnwQSBd2DlSTuE9ys71b0TovNAAbuspoxEXD8qb3gxme7zzpt7Jk)

Proses pemasangan membutuhkan waktu yang cukup lama tergantung kecepatan internet kalian. Seandainya sudah selesai kalian bisa mengakses ssh iPhone dengan default user dan password berikut :

- User	: root
- Password: alpine
- User	: mobile
- Password: alpine

Jangan lupa untuk mengganti password tersebut agar lebih aman.

## **iOS Pentest Tools**

Pada bagian ini kalian harus memasang beberapa tools dibawah ini guna membantu kalian dalam proses penetration testing yang akan kita bahas di materi selanjutnya.

1. **Ipainstaller Console	:** Untuk memasang maupun mengekspor aplikasi yang terpasang menjadi file ipa installer dan bisa kita salin ke komputer
2. **Erica Utilities			:** Untuk memasang perintah-perintah shell yang kita butuhkan untuk pentest
3. **Class-dump-z		:** Tool yang berguna untuk mengunduh aplikasi beserta data dalam format GZIP dari iPhone
4. **AppSync			:** Tool yang mengizinkan kita untuk memasang aplikasi dari luar App Store
5. **Terminal				:** Kita bisa memasang terminal di iPhone jika anda memerlukan
6. **Cycript				:** Seperti frida namun tamper code bisa dilakukan secara interaktif melalui terminal

Semua tool diatas bisa kalian pasang melalui **Cydia**, sedangkan untuk tool dibawah ini harus dipasang secara manual.

***Frida***

Untuk memasang Frida server ke perangkat iOS kalian bisa mengikuti panduan :

[https://frida.re/docs/ios](https://frida.re/docs/ios/#:~:text=Setting%20up%20your%20iOS%20device,running%20on%20your%20iOS%20device.)

**Install Burp Certificate**

Setelah semua aplikasi kebutuhan iOS penetration test terpasang di perangkat kalian. Selanjutnya kita akan membahas bagaimana memasang sertifikat Burp di perangkat iOS. Langkah pertama kalian harus mengakses IP address burp suite untuk mengunduh sertifikat Burp.

[https://lh3.googleusercontent.com/Ce8AW8QDvQee4eQsnq_Ya2beuWafpAfReQ0tGQThpOnn7IiYrlRD0y1y2lmTv8S4mIijUYHKNgRd38UATubu4VSgrnY8M8H_QpJ-IVkEjb1jMoBTV39rYf_kmDFtVjdbLJufE8iaYokevL-9lANSwUy8N04](https://lh3.googleusercontent.com/Ce8AW8QDvQee4eQsnq_Ya2beuWafpAfReQ0tGQThpOnn7IiYrlRD0y1y2lmTv8S4mIijUYHKNgRd38UATubu4VSgrnY8M8H_QpJ-IVkEjb1jMoBTV39rYf_kmDFtVjdbLJufE8iaYokevL-9lANSwUy8N04)

Klik pada bagian **CA Certificate** diatas kalian akan memulai proses pengunduhan. Jika selesai klik install untuk memasang sertifikat.

[https://lh4.googleusercontent.com/jzZnRoZkSoYqwOirNsSS1mJXOYNdGIlXsE4yv76Qd2rerFqvw27UpV52A6t_kBBCZVPpNVgop4YnfeIsEjQoFdsssp8rFM5yRp-5UJFWZ7M9t2Nflpg_K3KLKqPgqFTM5J0Y_S2397NXTmI1KnSYYSibT2E](https://lh4.googleusercontent.com/jzZnRoZkSoYqwOirNsSS1mJXOYNdGIlXsE4yv76Qd2rerFqvw27UpV52A6t_kBBCZVPpNVgop4YnfeIsEjQoFdsssp8rFM5yRp-5UJFWZ7M9t2Nflpg_K3KLKqPgqFTM5J0Y_S2397NXTmI1KnSYYSibT2E)

[https://lh6.googleusercontent.com/Rvy52-psN7bOf7dcaQLTc_tkzee6tbYUS1sIes1-tMuzJkyO2qS6N9ZNb45e-0GQrvCzgSGZV62HblT3fWxx-rNnZhoQN9Dd6jdStv96t9iuhx2xgN8l10yyW4mXv8T8EazxxOGxA8qKTglC71SaheSciO8](https://lh6.googleusercontent.com/Rvy52-psN7bOf7dcaQLTc_tkzee6tbYUS1sIes1-tMuzJkyO2qS6N9ZNb45e-0GQrvCzgSGZV62HblT3fWxx-rNnZhoQN9Dd6jdStv96t9iuhx2xgN8l10yyW4mXv8T8EazxxOGxA8qKTglC71SaheSciO8)

[https://lh6.googleusercontent.com/o2OBT0kPCh4BMrXwuRg73Zzow7gN4grkvMOri3Fqb4Mmfo6GCp09EQLDtQk9Vb40dLbQ2QdJwnC4rnewKhbNjG6lYopvK1luuSUw_2xl2aWCtFyOFS5TfOkEhtPCLl_qv99xlnrQvVNzi3807MJJocWo6Zc](https://lh6.googleusercontent.com/o2OBT0kPCh4BMrXwuRg73Zzow7gN4grkvMOri3Fqb4Mmfo6GCp09EQLDtQk9Vb40dLbQ2QdJwnC4rnewKhbNjG6lYopvK1luuSUw_2xl2aWCtFyOFS5TfOkEhtPCLl_qv99xlnrQvVNzi3807MJJocWo6Zc)

Di bagian akhir tahapan diatas muncul informasi **Verified** yang menandakan bahwa sertifikat sudah dipercaya oleh perangkat. Sehingga dengan proses tersebut kita akan bisa melakukan intercept terhadap traffic yang melewati proxy burp.

**Burp Proxy Setting**

Pengaturan proxy pada iOS terletak di pengaturan > Wifi > Pilih icon **i** pada nama wifi yang terhubung > Pada bagian bawah pilih konfigurasi proxy > Manual > Silahkan atur IP proxy dan port yang sesuai.