# Android Security Checklist

Created: June 22, 2022 1:17 PM

Untuk memudahkan kalian dalam pengujian keamanan aplikasi android. Beberapa daftar pengujian perlu jadi panduan agar kalian bisa mudah menentukan langkah awal hingga terakhir.

# **Platform Overview**

Android pada dasarnya sudah menerapkan security by design. Artinya konfigurasi standar android sudah aktif berbagai perimeter keamanan.

## ***Android Users and Groups***

Meskipun android berbasis linux bukan berarti implementasinya persis seperti di linux desktop. Di Android, dukungan multi-pengguna dari kernel Linux ke aplikasi sandbox: dengan beberapa pengecualian, setiap aplikasi berjalan seolah-olah dibawah pengguna Linux yang terpisah, secara efektif diisolasi dari aplikasi lain dan sistem operasi lainnya.

Untuk memahaminya kita bisa memeriksa dengan perintah berikut :

```bash
$ adb shell ps -A

USER       	PID  PPID 	VSZ	RSS WCHAN        	ADDR S NAM
root         	2 	0   	0  	0 kthreadd        	0 S [kthreadd]
root         	3 	2   	0  	0 smpboot_thread_fn   0 S [ksoftirqd/0]
system     	572 	1   12860   1816 do_wait	75c05747c0 S qseecomd
audioserver	732 	1   42144  12352 binder_ioctl_write_read f715cc00 S android.hardware.audio@2.0-service
bluetooth  	733 	1   15556   3176 binder_ioctl_write_read 7f5c771758 S android.hardware.bluetooth@1.0-service-qti
cameraserver   734 	1  119504  39016 binder_ioctl_write_read ee6d6c00 S android.hardware.camera.provider@2.4-service
media      	738 	1   11340   3708 binder_ioctl_write_read f06d3c00 S android.hardware.drm@1.0-service
u0_a38   	14943   702 1078776  58824 SyS_epoll_wait ec023ac0 S com.android.vending:download_service
u0_a100  	14980   701 3820488 121080 SyS_epoll_wait 78ab333668 S tech.kargo.transporter
u0_a105  	15113   701 4480704 102944 SyS_epoll_wait 78ab333668 S com.ss.android.ugc.trill:push
u0_a88   	15386   702 1045004  51844 SyS_epoll_wait ec023ac0 S com.android.chrome
```

Level user untuk menjalankan aplikasi memiliki user yang berbeda-beda. Sedangkan untuk driver terpisah sesuai dengan jenisnya. Sebagai contoh driver camera memiliki username **cameraserver**.

Dan untuk konfigurasinya bisa kalian lihat di [https://s.id/lAmVq](https://s.id/lAmVq). Pada source code tersebut memuat definisi user app.

#define AID_ROOT         	0  /* traditional unix root user */	#define AID_SYSTEM    	1000  /* system server */	#...	#define AID_SHELL     	2000  /* adb and debug shell user */	#...	#define AID_APP      	10000  /* first app user */	...

Agar lebih jelas, umumnya user dan password di linux tersimpan di /etc/passwd, /etc/group, dan /etc/shadow. Namun pada android user range ID sudah di definisikan di source code. Seperti potongan source code di atas AID_APP dengan id 10000. Untuk aplikasi pertama yang dijalankan akan mendapat username u0_a0 dengan ID 10000 dan aplikasi kedua akan mendapatkan username u0_a1 dengan ID 10001.

Jadi username tidak dibuat terlebih dahulu tetapi akan otomatis bangkit ketika kita pengguna memasang aplikasi tersebut.

## ***Android Security Hardening***

Android memiliki fitur untuk mempersulit penyerang melakukan exploitasi.

**SELinux**

Jika kalian sudah pernah memberikan permission file ke user tertentu dengan chmod dan chown. Maka SELinux memberikan keamanan tambahan dengan konsep Mandatory Access Control (MAC) untuk mengunci lebih lanjut proses mana yang harus memiliki akses ke resource yang mana.

**ASLR, KASLR, PIE and DEP**

Proteksi ini merupakan standar untuk mencegah serangan atau eksploitasi buffer overflow attack dengan memberikan address memory yang acak, mencegah eksekusi program pada user space dari kernel space, dan mencegah eksekusi program yang tersimpan di stack memory.

**SECCOMP**

Aplikasi android terkadang bisa memuat program C/C++. Seccomp memiliki fitur untuk memfilter system call apa saja yang diizinkan pada level aplikasi biasa.

## ***Data Storage***

Setiap aplikasi memiliki mekanisme penyimpanan, detail lokasi bisa kalian perhatikan pada tabel berikut :

[Untitled](Android%20Security%20Checklist%2055b3d6f5e8994a068d9d4da175b88693/Untitled%20Database%20a2e32c0853b94f03b96b3beb142e37d0.csv)

Goal dari pengujian pada Data Storage :

1. Memastikan tidak ada data sensitif yang mudah terekspos dalam penyimpanan internal android. Data sensitif yang dimaksud misalnya seperti Access Key, Hardcoded Password or Secret, Kredensial, dan informasi personal.
2. Keyboard cache tidak diaktifkan saat menulis data sensitif.
3. Tidak ada data sensitif yang dibagikan ke pihak ketiga.

**MSTG-STORAGE-1 & MSTG-STORAGE-2**

Semakin sedikit informasi yang tersimpan di penyimpanan lokal android semakin baik. Akan adanya password strong guideline membuat pengguna harus memasukkan password rumit setiap kali ingin menggunakan aplikasi.

Untuk memudahkannya terkadang software engineer menyimpan token ke penyimpanan lokal. Hal ini dilakukan agar pengguna tidak perlu melakukan login sesuai dengan masa berlaku token tersebut.

Pengujian pada tahap ini kita perlu memastikan apakah data sensitif tersebut sudah diamankan dengan menggunakan konsep seperti enkripsi baik simetris maupun asimetris.

Mengambil semua data storage yang kita perlukan :

```bash
$ adb root on
$ adb pull /data/data/<package id> <package id>
$ cd <package id>
```

Memeriksa Database

```bash
$ ls databases
$ sqlite3 databases/<file name>.db
sqlite> .help
sqlite> .databases
sqlite> .tables
sqlite> .mode column
sqlite> .headers on
sqlite> SELECT * FROM <NAMA TABEL>;
.... Lakukan query SQLite untuk memeriksa apakah ada data sensitif ....
```

Memeriksa cache

```bash
$ cat cache/*
```

Memeriksa Shared Preference

```bash
$ cat shared_prefs/*.xml
```

Memeriksa assets

```bash
$ ls files
```

**MSTG-STORAGE-4**

Di Bagian ini kita harus memeriksa apakah log debug masih diaktifkan oleh software engineer dan mengekspos data sensitif ? Pengujian bisa dilakukan dengan dinamis (APKStudio) namun karena tidak semua peserta menguasai Java Programming maka di materi ini kita akan gunakan dynamic analysis.

Langkah awal kita harus merekam log dari aplikasi agar muncul ke terminal dengan perintah berikut :

```bash
$ adb logcat | grep "$(adb shell ps | grep <package id> | awk '{print $2}')"
```

Jalankan aplikasi android DIVA dan cobalah untuk mengakses semua fitur yang ada. Apabila kalian sudah menjalankan semua fitur. Kemudian silahkan kembali ke terminal dan periksalah apakah ada data sensitif ?

**MSTG-STORAGE-5**

Pada pengujian ini kita akan memeriksa apakah keyboard memberikan atau merekam data sensitif saat pengguna memasukkan data sensitif. Keyboard android bisa menggunakan bawaan yang tersedia maupun keyboard dari pihak ketiga.

Selain itu keyboard memiliki fitur suggestion ataupun merekam apa yang kita ketik untuk disimpan ke suggestion. Bahkan tidak menutup kemungkinan apa yang kita ketik tersimpan dan diunggah di server pihak ketiga. Seperti terlihat keylogger bukan ?

Berikut berita yang berkaitan dengan penyalahgunaan aplikasi keyboard [https://s.id/lAsln](https://s.id/lAsln).

Untuk menguji aplikasi kita bisa membuka halaman yang mengharuskan pengguna memasukkan data sensitif seperti login. Contohnya sebagai berikut :

[https://lh5.googleusercontent.com/CemsRclEbCwMnSZ3-CWgJADfxAJfXHA-zRdMEpXJQGT2y4j1SBo_Xk9x8SEScBN3Afj5RZSXh9yETYuTpG7VwPDm9t8I9NHNKE19BhDna7BQS2wOOnKln-8bwJ2ihgpX3S8fgRxJlmFp-GJ4VdEeTjuGQdU](https://lh5.googleusercontent.com/CemsRclEbCwMnSZ3-CWgJADfxAJfXHA-zRdMEpXJQGT2y4j1SBo_Xk9x8SEScBN3Afj5RZSXh9yETYuTpG7VwPDm9t8I9NHNKE19BhDna7BQS2wOOnKln-8bwJ2ihgpX3S8fgRxJlmFp-GJ4VdEeTjuGQdU)

Gambar: Suggestion muncul pada area yang dilingkari

Bisa kalian bayangkan jika form tersebut untuk memasukkan kartu kredit ? Malicious keyboard atau keyboard pihak ketiga bisa dengan mudah merekam kartu kredit yang kalian ketik.

Hasilnya fitur suggestion ketika mode password dinonaktifkan menjadi aktif. Hal ini bisa disimpulkan bahwa aplikasi tidak lolos pada pengujian MSTG-STORAGE-5.

## ***Cryptographic***

Pada dasarnya peninjauan keamanan pada bagian ini bisa mudah dilakukan dengan static analysis. Tujuan dari pengujian ini sebagai berikut :

1. Kunci enkripsi tidak dimuat secara hardcode pada source code
2. Aplikasi tidak menggunakan kriptografi yang primitif
3. Aplikasi yang menggunakan kriptografi yang primitif harus dikonfigurasi sesuai dengan best practice tertentu

Untuk memeriksa kunci kita bisa mencarinya dengan cara reverse engineering dengan tool APK Studio yang sudah kita coba pada pertemuan sebelumnya.

Sedangkan untuk klasifikasi enkripsi atau hash primitif yang tidak direkomendasikan menurut OWASP sebagai berikut :

1. DES atau 3DES
2. RC4
3. MD5 dan SHA1
4. Broken random number (Dual_EC_DRBG dan SHA1PRNG)

Dan untuk rekomendasi enkripsi atau hash yang saat ini jadi pilihan terbaik adalah sebagai berikut :

- Confidentiality algorithms: AES-GCM-256 or ChaCha20-Poly1305
- Integrity algorithms: SHA-256, SHA-384, SHA-512, Blake2, the SHA-3 family
- Digital signature algorithms: RSA (3072 bits and higher), ECDSA with NIST P-384
- Key establishment algorithms: RSA (3072 bits and higher), DH (3072 bits or higher), ECDH with NIST P-384

Untuk lebih detail mengenai daftar peninjauan yang harus diperiksa kalian bisa membuka link [https://s.id/lABPk](https://s.id/lABPk).

## ***Network API***

Pada network communication pengujian dilakukan seperti pertemuan sebelumnya dari konsep intercept pada Burp hingga API Security testing.

Bagian yang perlu kita periksa sebagai berikut :

- Aplikasi menerapkan enkripsi pada transmisi data untuk mengamankan pengguna dari jaringan publik.
- Aplikasi harus memeriksa bahwa sertifikat yang digunakan terpercaya oleh CA
- Konfigurasi TLS harus memenuhi kriteria best practice

Untuk lebih detail kalian bisa membuka referensi [https://s.id/lAF0A](https://s.id/lAF0A).

## ***Authentication and Session Management***

Bagian ini pengujian dilakukan dengan memeriksa proses autentikasi dan penerapan session pada interaksi aplikasi dan server.

1. Proses validasi username dan password berada di backend API.
2. Jika menggunakan konsep stateful, server memberikan session yang dibangkitkan secara acak tanpa memberikan kredensial lengkap milik pengguna.
3. Jika menggunakan konsep stateless, server memberikan token yang sudah di tanda tangani dengan algoritma yang aman.
4. Ketika logout maka semua token yang terdaftar pada perangkat tersebut harus dinonaktifkan.
5. Server harus membatasi kesalahan autentikasi dengan batas maksimal tertentu.
6. Menerapkan persyaratan password yang kuat sesuai best practice tertentu.
7. Sesi dinonaktifkan ketika user tidak aktif selama waktu tertentu dan ketika token sudah tidak berlaku.
8. Ketika pengguna mengganti password maka semua sesi dan token sebelumnya yang tersedia di perangkat lain seharusnya dinonaktifkan.

## ***Platform API***

Seperti yang kita ketahui bahwa android sudah cukup memiliki pengamanan yang bagus. Akan tetapi jika software developer tidak menerapkan keamanan sesuai dengan best practice tentu akan menimbulkan celah-celah.

**MSTG-PLATFORM-1**

Permissions pada aplikasi seharusnya sesuai dengan kebutuhan. Kalian bisa mencoba aplikasi dengan menjalankan semua fitur dan membandingkannya dengan definisi permissions pada aplikasi. Sebagai contoh fitur tidak memerlukan permissions untuk mengakses kontak akan tetapi pada aplikasi meminta permission tersebut.

Untuk memeriksa permissions pada aplikasi kita bisa gunakan perintah berikut :

```bash
$ adb shell dumpsys package <package id> | grep permission
```

**MSTG-PLATFORM-2**

Pengujian terhadap injeksi perlu kita coba. Pada percobaan ini kita menggunakan aplikasi MSTG Playground. Perlu kalian ketahui bahwa aplikasi android mendukung skema URL dimana ketika kita membuat ekstensi atau URL tertentu akan terlempar ke aplikasi yang ada.

Sebagai contoh ketika kalian buka [www.youtube.com](http://www.youtube.com/) melalui chrome tiba-tiba akan terbuka aplikasi youtube. Beberapa jenis skema URL pada android dikategorikan sebagai berikut :

1. Intents, Binders, Android Shared Memory (ASHMEM), or BroadcastReceivers
2. Melalui UI

Untuk praktik kali ini silahkan buka aplikasi MSTG-Playground. Lalu buka halaman **OMTG-CODING-003_SQL_INJECTION_CONTENT_PROVIDER**, tambahkan data terlebih dahulu pada halaman ini :

[https://lh4.googleusercontent.com/zRMnFuF2umt0BmL-od2sRI0Mq2nqwTFuqfKKVkWNREohxgZtwO1fIKTOgU3TjxWQSQneIq9RM0Nimy1ZCfLVTYKqJPPqZetEKPhtk8zBvcYUWQOUlUDzyfQS_WKqQNBkc3lP_eGIYLGHRHqDOgf0YBJxg4I](https://lh4.googleusercontent.com/zRMnFuF2umt0BmL-od2sRI0Mq2nqwTFuqfKKVkWNREohxgZtwO1fIKTOgU3TjxWQSQneIq9RM0Nimy1ZCfLVTYKqJPPqZetEKPhtk8zBvcYUWQOUlUDzyfQS_WKqQNBkc3lP_eGIYLGHRHqDOgf0YBJxg4I)

Menguji SQL Injection pada Content Provider bisa dilakukan dengan perintah :

```bash
$ adb shell
$ content query --uri content://sg.vp.owasp_mobile.provider.College/students
$ content query --uri content://sg.vp.owasp_mobile.provider.College/students --where "name='danang') OR 1=1--''"
$ content query --uri content://sg.vp.owasp_mobile.provider.College/students --where "name='danang') OR 1=2--''"
```

Untuk langkah setelahnya kalian bisa melakukan teknik SQL Injection seperti sebelumnya. Hanya saja karena android menggunakan SQLite maka perintah injection sedikit berbeda.

**MSTG-PLATFORM-3**

Bagian ini kita perlu memeriksa skema URL pada android tidak boleh mengekspor informasi sensitif kecuali jika aplikasi memiliki mekanisme proteksi.

```bash
dz> run scanner.activity.browsable -a com.android.messaging
Package: com.android.messaging
  Invocable URIs:
	sms://
	mms://
  Classes:
	.ui.conversation.LaunchConversationActivity

dz> run app.activity.start  --action android.intent.action.VIEW --data-uri "sms://0123456789"
```

Perintah diatas hanya sebagai contoh. Pada aplikasi yang menjadi target pengujian kita apabila memiliki skema URL yang sudah terdaftar ada salahnya kita periksa dan dicari apakah ada kerentanan disana.

## ***Code Quality and Build Settings***

Pada materi ini kita akan memeriksa apakah konfigurasi saat membangun aplikasi ditahap production sudah sesuai.

**MSTG-CODE-1**

Aplikasi yang akan diunggah ke publik harus ditandatangani dengan skema V1 dan V2. Namun akan lebih baik jika v3 juga dilakukan.

```bash
$ apksigner verify --verbose ContohApp.apk               	 
Verifies
Verified using v1 scheme (JAR signing): true
Verified using v2 scheme (APK Signature Scheme v2): false
Verified using v3 scheme (APK Signature Scheme v3): false
Number of signers: 1
```

**MSTG-CODE-2**

Pastikan aplikasi yang akan diunggah ke public (playstore) tidak dalam mode debug.

```bash
dz> run app.package.debuggable -f <package id>
```

Jika tidak muncul apa-apa bisa dipastikan bahwa mode debug tidak aktif pada aplikasi tersebut.

**MSTG-CODE-3**

Pada aplikasi yang sudah dalam mode production seharusnya log error pada logcat musti dinonaktifkan. Kita bisa memeriksanya dengan perintah :

```bash
$ adb logcat | grep "$(adb shell ps | grep <package id> | awk '{print $2}')"
```

**MSTG-CODE-6 and MSTG-CODE-7**

Aplikasi production seharusnya tidak boleh mengalami crash sehingga penerapan exception handling harus ada. Indikatornya apabila tidak ada exception handling maka aplikasi akan keluar secara tiba-tiba ketika kita menjalankan fitur tertentu baik kita sengaja maupun tidak.

**MSTG-CODE-9**

Bagian ini kalian harus decompile aplikasi menggunakan APK Studio dan periksa apakah method function sudah di obfuscated atau tidak. Indikatornya adalah nama method menjadi huruf yang susah kita persepsikan kegunaannya seperti apa. Contoh :

```java
package com.a.a.a;

import com.a.a.b.a;
import java.util.List;

class a$b
  extends a
{
  public a$b(List paramList)
  {
	super(paramList);
  }

  public boolean areAllItemsEnabled()
  {
	return true;
  }

  public boolean isEnabled(int paramInt)
  {
	return true;
  }
}
```

Selain pembahasan ini sebenarnya masih banyak yang belum kita bahas, mengingat waktu kita sangat terbatas materi bisa kalian pelajari lebih dalam di link berikut :

- [https://github.com/OWASP/owasp-mstg](https://github.com/OWASP/owasp-mstg)