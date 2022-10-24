# Your Big Project

Hi engineers!

Selamat datang di Sekolah Digital Cilsy, sebuah produk dari PT Cilsy Fiolution Indonesia yang bergerak di bidang Edu-Tech, dimana kalian akan dipersiapkan untuk memiliki skill yang mumpuni untuk masuk ke industri teknologi

![Main Logo-03 Transparent.png](Your%20Big%20Project%2050ac12e088ba43aea6211bb7370bf7c0/Main_Logo-03_Transparent.png)

Selain Sekolah Digital Cilsy, PT Cilsy Fiolution Indonesia juga mempunyai produk lainnya, yaitu sebuah marketplace kursus Online Server & Jaringan, yang kami beri nama cilsy.id (bisa diakses di [https://www.cilsy.id/](https://www.cilsy.id/)).

![Untitled](Your%20Big%20Project%2050ac12e088ba43aea6211bb7370bf7c0/Untitled.png)

Project yang akan kalian kerjakan adalah melakukan eksploitasi ke platform e-learning kami, yaitu cilsy.id. Eitsss tapi jangan langsung meluncur ke [https://www.cilsy.id](https://www.cilsy.id/) yaa, karena environment yang akan digunakan bukanlah yang ini. Kami sudah mempersiapkan environment khusus yang siap untuk dieksploitasi, yaitu [https://vuln.cilsy.id](https://vuln.cilsy.id/).

![Untitled](Your%20Big%20Project%2050ac12e088ba43aea6211bb7370bf7c0/Untitled%201.png)

Halaman web vuln.cilsy.id

Web [https://vuln.cilsy.id](https://vuln.cilsy.id/) merupakan web asli hasil cloning 100% dari salah satu produk Cilsy Fiolution, yaitu Cilsy.id -> [www.cilsy.id](http://www.cilsy.id/) . Namun dengan kondisi saat masih banyak bug yang ada belum di patch.
Sehingga program ini benar-benar menggambarkan kondisi nyata sebuah aplikasi web live production yang digunakan oleh banyak pengguna dan masih memiliki berbagai celah.

# Disclaimer!

- Program bug bounty ini hanya untuk kebutuhan internal Sekolah Hacker dan hanya bisa digunakan oleh para murid, instruktur, dan alumni aktif. Tidak dapat digunakan oleh umum.
- Cakupan yang diperbolehkan untuk diserang hanya subdomain [https://vuln.cilsy.id](https://vuln.cilsy.id/), sedangkan untuk subdomain lain tidak diperbolehkan.
- Seluruh hak cipta dari laporan yang telah dibuat, data-data, juga aplikasi yang digunakan adalah milik Sekolah Hacker (PT. Cilsy Fiolution Indonesia).

## Dilarang keras :

- Menyebarkan data-data sensitif yang telah didapat
- Menyebarkan laporan yang dibuat (tanpa seizin Sekolah Hacker)
- Menyalahgunakan laporan, celah, dan data yang telah didapatkan
- Mengajak masyarakat umum untuk mengikuti program ini.

Apabila terbukti melanggar ketentuan-ketentuan diatas, maka dapat berurusan dengan hukum.

# Informasi Mengenai Celah dan Penilaian

Total Celah yang bisa dicari

- P4-Low : 10 celah
- P3-Medium : 24 celah
- P2-High : 5 celah
- P1-Critical : 8 celah

Jumlah celah diatas bisa lebih banyak,

## Cakupan Celah yang bisa dicari

- Cross-site scripting (XSS).
- Cross-site request forgery on critical activity.
- Server-Side request forgery (SSRF).
- SQL injection.
- DDOS
- Server-side remote code execution (RCE).
- XML external entity attacks (XXE).
- Unvalidated open redirect.
- IDOR
- Access control issues on sensitive data.
- Administrative Login Panel without password or weak password.
- Local file disclosure (LFD).
- Local file inclusion.
- Information disclosure of Sensitive Information.
- Publicly accessible login or admin panels.
- Lack of HTTP security headers (CSP, X-XSS,) etc.

## Cakupan Celah yang tidak diperbolehkan

- Social engineering.
- Celah keamanan yang merupakan celah keamanan pihak ketiga dan seterusnya yang memiliki integrasi dengan sistem kami.
- Self XSS.
- Celah keamanan yang merupakan kesalahan Platform pihak kedua dan seterusnya seperti celah keamanan Web browser.
- Celah keamanan 0-Days (harus Kami verifikasi terlebih dahulu).
- Celah keamanan yang membutuhkan akses fisik ke sistem Kami.
- Kesalahan pengguna atau pegawai Kami yang memberikan akses kredensialnya kepada pihak luar.

## Penilaian pada setiap Celah yang ditemukan

- P4-Low : 1 point
- P3-Medium : 2 point
- P2-High : 4 point
- P1-Critical : 6 point

## Syarat keberhasilan/kelulusan

- Minimal mencapai poin 20 (gabungan dari semua jenis level celah)
- Laporan Celah keamanan yang ditemukan harus mengikuti format reporting yang resmi & profesional.
- Harus bisa mempresentasikan & menjelaskan ke instruktur dengan baik pada saat presentasi Final Project.

Gimana, sudah siap untuk belajar? Lets start the journey!