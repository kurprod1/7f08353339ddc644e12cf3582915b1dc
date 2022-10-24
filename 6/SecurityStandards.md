# Security Standards

Kerentanan ini juga banyak dibahas baik dari standar keamanan seperti OWASP, NIST, PCI DSS, ISO 27001, hingga SANS. Artinya kerentanan ini sangat populer dan banyak sering ditemukan di semua aspek teknologi.

## **OWASP**

Jika kita memahami penerapan keamanan pada konsep Secure Software Development Lifecycle (SSDLC), mitigasi keamanan diterapkan baik dari sisi plan, code, build, test, release, deploy, operate dan monitor. Semua tahapan tersebut mengutip pencegahan XSS agar tidak terjadi.

![](https://lh3.googleusercontent.com/yCIRgcOLlXjyYQPvUyqWMrSBaP8RdyV2aQvC4bqoBu4MYyG6ylyFJJ235fD0W8yKT6e3g6F0KNncfxvLBxIlG9M3L76EFnK7QxBXxcBUinlR91yf1oh6VI0HjEm2ycPzUNs5aGszYoQGdv-p9vVTNLktDSg)

Pada tahap perencanaan OWASP menyinggung XSS pada dokumen [Application Verification Standard 4.0](https://owasp.org/www-pdf-archive/OWASP_Application_Security_Verification_Standard_4.0-en.pdf) di V5 yang sangat tegas untuk selalu mengimplementasikan Validation, Sanitization and Encoding pada produk atau fitur yang akan dibuat. Tanggung jawab ini harus dipegang teguh oleh CTO, Product Owner, Product Manager, hingga Software Architect. Karena posisi tersebut punya kewenangan terhadap desain dan perencanaan fitur produk.

Namun dari sekian banyaknya posisi yang sudah dijelaskan, orang yang punya tugas untuk menuliskan *Acceptance Criteria* pada suatu fitur yang akan dikerjakan tim engineer ialah Product Owner dan Manager. Sehingga sebagai security engineer, rekomendasi untuk mencegah kerentanan secara dini bisa dilakukan dengan memberikan edukasi mengenai ASVS V5 pada mereka untuk antisipasi secara awal.

Sedangkan untuk tahapan code pada SDLC selain memberikan edukasi tentang Cross-Site Scripting kita bisa membantu menyiapkan aplikasi SAST yang bisa dijalankan mudah oleh tim software engineer. Hal tersebut perlu dilakukan agar software engineer mampu meninjau apalah input validation, sanitization, dan encoding sudah diterapkan dengan benar. Standar yang bisa jadi acuan bagi mereka adalah [OWASP Secure Coding Practice](https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf).

Pada tahap build proses analisis identifikasi XSS bisa dilakukan dengan menerapkan SAST dan DAST pada CI/CD pipeline. Hal ini bisa mengurangi beban security engineer karena banyak tahapan untuk mengidentifikasi kerentanan tersebut.

Dan proses setelah build yakni proses test, pada tahap ini seperti yang sering kita singgung pada materi sebelumnya. Proses test akan dilakukan oleh QA yang sudah diberikan edukasi tentang basic security testing. Barulah setelah ini kalian yang bekerja sebagai security engineer akan menguji aplikasi tentunya mengikuti standar [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/stable/)


## **NIST 800-44 ver2**

Panduan ini membahas mengenai bagaimana pengamanan aplikasi web dan web server. Pada panduan tersebut juga tegas bahwa Cross Site Scripting merupakan salah satu bagian yang harus kita periksa dan dicegah. Teman-teman bisa membuka dokumen panduan standar NIST di [https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-44ver2.pdf](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-44ver2.pdf). Pada bagian “Checklist for Securing Web Content” (bab 6.5) menyatakan bahwa semua data yang dimasukkan oleh pengguna harus di validasi tanpa terkecuali.

## **PCI DSS type D**

Bahkan pada standar PCI DSS sering digunakan oleh startup yang memakai pembayaran digital juga menyertakan pada **Goal 5 : Requirement 6.5.7**. Bagian ini akan menyuruh kalian memeriksa kebijakan dan prosedur pengembangan perangkat lunak dan wawancarai personil yang bertanggung jawab untuk memverifikasi bahwa scripting lintas situs (XSS) diatasi dengan teknik pengkodean yang mencakup :

1. Memvalidasi semua parameter sebelum dimasukkan
2. Memanfaatkan escaping atau encoding

Arti dari kutipan diatas bahwa tidak cukup kita menguji akan adanya XSS, tetapi juga perlu memeriksa apakah perusahaan sudah memiliki kebijakan tertulis mengenai siapa saja yang punya tanggung jawab untuk memastikan bahwa semua data di validasi sebelum disimpan.

Cukup tegas bukan ?

Dari semua standar yang sudah kita singgung diatas, tentu XSS tidak bisa kita anggap celah yang sederhana. Perlu dicegah baik dari proses perencanaan hingga ketika sudah masuk ke server produksi harus dipastikan bahwa celah ini tidak ada.