# Broken Authentication

![Untitled](Broken%20Authentication%2068f5bb00fb3941aea29fc95adc64fc82/Untitled.png)

Kategori kerentanan ini terjadi ketika suatu sistem atau aplikasi tidak mampu melakukan autentikasi untuk mengidentifikasi identitas dan akses kontrol dengan baik. Hal ini menyebabkan seorang penyerang mampu melakukan *bypass* metode autentikasi. Sebagai contoh berikut kasus kerentanan broken authentication yang sering ditemukan :

- Kredensial otentikasi pengguna tidak dilindungi saat disimpan.
- Kredensial login yang dapat diprediksi.
- ID sesi terbuka di URL (mis., Token tercantum pada URL).
- ID sesi rentan terhadap serangan session fixation.
- Nilai sesi tidak habis atau tidak valid setelah keluar.
- ID sesi tidak dirotasi setelah login berhasil.
- Kata sandi, ID sesi, dan kredensial lainnya dikirim melalui koneksi yang tidak dienkripsi.

Untuk memahami kerentanan ini, kita perlu mempelajari cara kerja session dan authentication pada suatu koneksi.

# Session & Authentication Concept

Kita dapat mengatakan bahwa HTTP adalah apa yang memungkinkan komunikasi antara klien (frontend) dan server (backend). HTTP merupakan stateless sehingga setiap permintaan yang dibuat sama sekali tidak mengetahui adanya tindakan yang diambil sebelumnya.

Lebih jelasnya mengenai konsep stateless adalah dimana request yang dilakukan oleh klien setelah mendapatkan respon selanjutnya koneksi akan dihentikan. Ketika client melakukan request baru tanpa adanya penanda seperti cookie atau session id maka web server tidak akan bisa mengenali kita.

Katakanlah misalnya kita baru saja masuk ke akun twitter kita dan kita menavigasi ke halaman pengaturan kita, dengan perilaku HTTP default, kita akan diminta untuk masuk kembali karena server tidak tahu bahwa kita baru saja masuk tetapi dengan otentikasi sesi dan token maka dapat memberi tahu server bahwa kami sudah pernah melewati proses autentikasi sebelumnya.

![](https://lh6.googleusercontent.com/EpAyx9Qum7MEgtiN9ci3Wkg-RcXViQcNST5njqgIa3k19uzNLX3XYsFr6K8m6VsZYvX9LEevLNvoUeNs5BgkvNNxsPqB295siorqY548qsxJeWWd7II11lRvrRUToGC-PNBTwba15uPeSTdFlvFhdQUEKp8)

Gambar: Konsep Autentikasi menggunakan Sesi

Nah diatas merupakan proses autentikasi yang biasanya terjadi di aplikasi web. Pada proses awal kita belum memiliki akses terhadap aplikasi web sehingga harus mengirimkan username dan password. Setelah itu ketika server merespon bahwa username dan password benar maka server akan memberikan ID sesi dalam bentuk cookie kepada klien.

Nah klien menerima ID sesi dalam bentuk cookie tersebut dan akan dipergunakan untuk mengakses halaman-halaman web.

Konsep otentikasi diatas hanya salah satu dari sekian banyaknya alur yang ada. Hanya saja dalam security engineering teman-teman perlu meninjau kembali alur yang dipakai di perusahaan tersebut. Dan memastikan apakah sudah sesuai dengan standar yang jadi acuan atau bisa jadi alur autentikasi dibuat tanpa menggunakan standar sama sekali.

## Must Read Materials

- [A typical HTTP session - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Session)

## Standarization

Standar autentikasi yang baik dan benar untuk keamanan bisa mengambil referensi :

1. [NIST Digital Identity Guidelines (800-63)](https://pages.nist.gov/800-63-3)
2. [OWASP Proactive Controls: Implement Digital Identity](https://owasp.org/www-project-proactive-controls/v3/en/c6-digital-identity)
3. [OWASP Application Security Verification Standard: V2 Authentication](https://owasp.org/www-project-application-security-verification-standard)
4. [OWASP Application Security Verification Standard: V3 Session Management](https://owasp.org/www-project-application-security-verification-standard)
5. [OWASP Testing Guide: Identity,](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/03-Identity_Management_Testing/README) [Authentication](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/04-Authentication_Testing/README)
6. [OWASP Cheat Sheet: Authentication](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
7. [OWASP Cheat Sheet: Credential Stuffing](https://cheatsheetseries.owasp.org/cheatsheets/Credential_Stuffing_Prevention_Cheat_Sheet.html)
8. [OWASP Cheat Sheet: Forgot Password](https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html)
9. [OWASP Cheat Sheet: Session Management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)
10. [OWASP Automated Threats Handbook](https://owasp.org/www-project-automated-threats-to-web-applications/)

# Reference

- [A2:2017-Broken Authentication](https://owasp.org/www-project-top-ten/2017/A2_2017-Broken_Authentication)
- [Authentication vulnerabilities | Web Security Academy](https://portswigger.net/web-security/authentication)
- [Authentication vulnerabilities](https://dev.to/ms_74/authentication-vulnerabilities-15po)