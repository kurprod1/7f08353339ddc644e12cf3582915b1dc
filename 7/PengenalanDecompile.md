# Pengenalan Decompile & Patching dengan APK Studio

Created: June 22, 2022 1:17 PM

Decompile merupakan teknik mengonversi kode program yang dapat dieksekusi (siap dijalankan) (kadang-kadang disebut kode objek) menjadi beberapa bentuk bahasa pemrograman tingkat tinggi sehingga dapat dibaca oleh manusia.

Teknik patching ini cenderung masuk ke kategori cracking bukan lagi hacking. Alasannya kita merusak struktur aplikasi agar bisa menyesuaikan kebutuhan kita. Sebagai contoh kita akan memodifikasi aplikasi DIVA. Aplikasi dapat diunduh di link berikut : [http://www.payatu.com/wp-content/uploads/2016/01/diva-beta.tar.gz](http://www.payatu.com/wp-content/uploads/2016/01/diva-beta.tar.gz)

Install aplikasi DIVA ke dalam emulator android melalui perintah terminal :

```bash
$ adb install diva-beta.apk
```

Jalankan aplikasi DIVA, perlu teman-teman ketahui aplikasi DIVA atau sering dikenal juga dengan sebutan Damn Insecure and Vulnerable Apps merupakan aplikasi mobile yang dibuat untuk belajar keamanan seputar aplikasi mobile. Sehingga bisa dipastikan aplikasi didalamnya sangat tidak aman.

[https://lh5.googleusercontent.com/xB0sKyPTmIvyHbYQLx0DaXGxVOZlN_MZC9PYPT6jILSEc12byIDgiZaqzQlGZBaMgqG04G9D9cHrEd0qAFm2eNT95QnYUhdA9EI2EjEH3HPFESwJslVbdO6AGBH0wUDEvUA96LcdAxlDgy0aTH9I7WkGnzA](https://lh5.googleusercontent.com/xB0sKyPTmIvyHbYQLx0DaXGxVOZlN_MZC9PYPT6jILSEc12byIDgiZaqzQlGZBaMgqG04G9D9cHrEd0qAFm2eNT95QnYUhdA9EI2EjEH3HPFESwJslVbdO6AGBH0wUDEvUA96LcdAxlDgy0aTH9I7WkGnzA)

Klik pada tombol “HARD CODING ISSUE - PART 1”, didalamnya terdapat halaman login namun kita tidak mengetahui passwordnya.

[https://lh5.googleusercontent.com/rVWH1aE5AFxbhO5fVLBuZygnxPFZNGqDG-PDRDgagUU-ff-63wfbGswI-fFzUTXFbBI-r5NuLJOrPUoLu9myrPu8lvRggvmWiL7_nVT6Vf_4gRkZqdwp1ImoUxRgin5392IgJSUk0b5bg2w66pxBwahUpXI](https://lh5.googleusercontent.com/rVWH1aE5AFxbhO5fVLBuZygnxPFZNGqDG-PDRDgagUU-ff-63wfbGswI-fFzUTXFbBI-r5NuLJOrPUoLu9myrPu8lvRggvmWiL7_nVT6Vf_4gRkZqdwp1ImoUxRgin5392IgJSUk0b5bg2w66pxBwahUpXI)

Untuk mengetahui password kita bisa mulai jalankan APK Studio. Kemudian klik icon android yang ada pada posisi kiri dan pilih apk file dilokasi komputer kalian.

[https://lh6.googleusercontent.com/Y4lccjQL3Q5lUr3Fd8rCKt4bXC_6a_iAK8N-nermKgDOXO7G4yWmqZ8cjYrbSn6_AlUXF0SSiwHa5x3h8Ad3LIqIin2tQ4Pmj6AphZGnnyq_mGCJ9yxPRUid_XchxJsXIgenHzs8U5tu2y3CQvhhgkFg40k](https://lh6.googleusercontent.com/Y4lccjQL3Q5lUr3Fd8rCKt4bXC_6a_iAK8N-nermKgDOXO7G4yWmqZ8cjYrbSn6_AlUXF0SSiwHa5x3h8Ad3LIqIin2tQ4Pmj6AphZGnnyq_mGCJ9yxPRUid_XchxJsXIgenHzs8U5tu2y3CQvhhgkFg40k)

Kemudian popup window akan muncul checklist semua termasuk Decompile Java. Sedangkan smali merupakan bahasa assembler dalam format yang dimengerti oleh Dalvik. Jika sudah jangan lupa untuk klik Decompile.

[https://lh4.googleusercontent.com/PmClNlvL4D-S1Q7zeT5vCXBTyOOtIJ1CJTb-Gmkc8ucpoSAAagstuvGCKkI70YDBr2zEagDGioIkJHpjAIT38nr576W2_Y9XAF3JRSICbg6TK84WeyTmp1ejhqGes1B241ALr0-5H7NokhB6enJBr0nRiF8](https://lh4.googleusercontent.com/PmClNlvL4D-S1Q7zeT5vCXBTyOOtIJ1CJTb-Gmkc8ucpoSAAagstuvGCKkI70YDBr2zEagDGioIkJHpjAIT38nr576W2_Y9XAF3JRSICbg6TK84WeyTmp1ejhqGes1B241ALr0-5H7NokhB6enJBr0nRiF8)

Proses decompile ini membutuhkan waktu yang tidak terlalu lama, kalian harus menunggu hingga proses ini selesai. Nah sambil menunggu prosesnya kita pelajari dulu fundamental android sehingga kita tahu apa yang harus kita lakukan dari awal hingga akhir.

# **Android Manifest**

Android Manifest (Nama file: AndroidManifest.xml) adalah sebuah xml yang berisi informasi mengenai aplikasi Seperti nama package, level SDK yang digunakan, beserta icon dan nama yang diberikan untuk aplikasi. Selain itu di dalam file tersebut akan terdefinisikan Class mana yang akan dieksekusi pertama kali. Sekedar tambahan informasi juga bahwa permission juga dilampirkan di dalam file tersebut.

AndroidManifest.xml pada DIVA :

```xml
<?xml version="1.0" encoding="utf-8" standalone="no"?><manifest xmlns:android="http://schemas.android.com/apk/res/android" package="jakhar.aseem.diva" platformBuildVersionCode="23" platformBuildVersionName="6.0-2166767">
   <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
   <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
   <uses-permission android:name="android.permission.INTERNET"/>
   <application android:allowBackup="true" android:debuggable="true" android:icon="@mipmap/ic_launcher" android:label="@string/app_name" android:supportsRtl="true" android:theme="@style/AppTheme">
   	<activity android:label="@string/app_name" android:name="jakhar.aseem.diva.MainActivity" android:theme="@style/AppTheme.NoActionBar">
       	<intent-filter>
           	<action android:name="android.intent.action.MAIN"/>
           	<category android:name="android.intent.category.LAUNCHER"/>
       	</intent-filter>
   	</activity>
   	<activity android:label="@string/d1" android:name="jakhar.aseem.diva.LogActivity"/>
   	<activity android:label="@string/d2" android:name="jakhar.aseem.diva.HardcodeActivity"/>
   	<activity android:label="@string/d3" android:name="jakhar.aseem.diva.InsecureDataStorage1Activity"/>
   	<activity android:label="@string/d4" android:name="jakhar.aseem.diva.InsecureDataStorage2Activity"/>
   	<activity android:label="@string/d5" android:name="jakhar.aseem.diva.InsecureDataStorage3Activity"/>
   	<activity android:label="@string/d6" android:name="jakhar.aseem.diva.InsecureDataStorage4Activity"/>
   	<activity android:label="@string/d7" android:name="jakhar.aseem.diva.SQLInjectionActivity"/>
   	<activity android:label="@string/d8" android:name="jakhar.aseem.diva.InputValidation2URISchemeActivity"/>
   	<activity android:label="@string/d9" android:name="jakhar.aseem.diva.AccessControl1Activity"/>
   	<activity android:label="@string/apic_label" android:name="jakhar.aseem.diva.APICredsActivity">
       	<intent-filter>
           	<action android:name="jakhar.aseem.diva.action.VIEW_CREDS"/>
           	<category android:name="android.intent.category.DEFAULT"/>
       	</intent-filter>
   	</activity>
   	<activity android:label="@string/d10" android:name="jakhar.aseem.diva.AccessControl2Activity"/>
   	<activity android:label="@string/apic2_label" android:name="jakhar.aseem.diva.APICreds2Activity">
       	<intent-filter>
           	<action android:name="jakhar.aseem.diva.action.VIEW_CREDS2"/>
           	<category android:name="android.intent.category.DEFAULT"/>
       	</intent-filter>
   	</activity>
   	<provider android:authorities="jakhar.aseem.diva.provider.notesprovider" android:enabled="true" android:exported="true" android:name="jakhar.aseem.diva.NotesProvider"/>
   	<activity android:label="@string/d11" android:name="jakhar.aseem.diva.AccessControl3Activity"/>
   	<activity android:label="@string/d12" android:name="jakhar.aseem.diva.Hardcode2Activity"/>
   	<activity android:label="@string/pnotes" android:name="jakhar.aseem.diva.AccessControl3NotesActivity"/>
   	<activity android:label="@string/d13" android:name="jakhar.aseem.diva.InputValidation3Activity"/>
   </application>
</manifest>
```

Jika kita amati lebih dalam dari source code diatas, bisa dijelaskan bahwa MainActivity memiliki intent-filter dengan kategori sebagai launcher dan action sebagai main. Artinya MainActivity yang terletak pada folder jakhar/aseem/diva/MainActivity.java adalah Class yang dieksekusi pertama kali.

```xml
<activity android:label="@string/app_name" android:name="jakhar.aseem.diva.MainActivity" android:theme="@style/AppTheme.NoActionBar">
       	<intent-filter>
           	<action android:name="android.intent.action.MAIN"/>
           	<category android:name="android.intent.category.LAUNCHER"/>
       	</intent-filter>
 </activity>
```

# **Activity**

Activity adalah komponen pada aplikasi Android yang menampilkan dan mengatur halaman aplikasi sebagai tempat interaksi antara pengguna dengan aplikasi. Dalam hal ini, halaman Insecure Logging terdapat di lokasi jakhar/aseem/diva/HardcodeActivity.java sesuai dengan kutipan baris berikut :

```xml
<activity android:label="@string/d2" android:name="jakhar.aseem.diva.HardcodeActivity"/>
```

Selanjutnya kalian bisa membuka file tersebut melalui APK Studio:

[https://lh5.googleusercontent.com/zlCud3M9eio_kq1fcK09FNflEt1kPaNRGJjfHvAURbWZNzDlYlHazJV19Er49bhMzkuLLjx2J2GZ-AaqOr6fOHf_VHQGGHMRx5fpYZeFb0RIbzENuH6fQ3-4iClI3dYLr2SbGlNU5PLioR_ClNBAD_cF0dM](https://lh5.googleusercontent.com/zlCud3M9eio_kq1fcK09FNflEt1kPaNRGJjfHvAURbWZNzDlYlHazJV19Er49bhMzkuLLjx2J2GZ-AaqOr6fOHf_VHQGGHMRx5fpYZeFb0RIbzENuH6fQ3-4iClI3dYLr2SbGlNU5PLioR_ClNBAD_cF0dM)

Gambar: Password ditemukan di HardcodeActivity.java

Bisa kalian lihat password secara jelas tertulis sebagai **vendorsecretkey**. Bisa kalian coba langsung di android benar dan tidaknya password tersebut.

# **Smali**

Teknik selanjutnya kita akan melakukan patching atau cracking aplikasi untuk mengganti password **vendorsecretkey** menjadi **sekolahhacker**. Kita akan melakukannya dengan memodifikasi source code HardcodeActivity.smali. Sangat berbeda sekali jika HardcodeActivity versi smali jika dibuka dibanding versi java pada materi sebelumnya.

Singkatnya ketika source code sudah kita compile menjadi apk maka source code Java sudah berubah menjadi *.dex dan didalamnya terdapat Dalvik bytecode. Sebagai manusia kita akan kesulitan dalam memahami file binary tersebut. Untuk itulah smali ditemukan agar kita bisa mempermudah kode-kode apa yang dijalankan Dalvik VM. Jika kalian ada muncul pertanyaan kenapa bukan hasil decompile Java aja ? Jawabannya terkadang tidak semua file binary bisa kita ubah kedalam bahasa Java secara utuh.

[https://lh6.googleusercontent.com/qZ5VL4F4dbwOVqPpfxCPWfJl0kTt_jx7oTHLGjSHP4MFjG6to8yRj6NbHi-g7wpySVqWC91-cZknnVAHyq6hFD9ecJmRJrtPblgMZNV1_NegOUY0GVN1wUH051bVprPUp8yFP1PdPOhLMqlo2jLltQdq5zg](https://lh6.googleusercontent.com/qZ5VL4F4dbwOVqPpfxCPWfJl0kTt_jx7oTHLGjSHP4MFjG6to8yRj6NbHi-g7wpySVqWC91-cZknnVAHyq6hFD9ecJmRJrtPblgMZNV1_NegOUY0GVN1wUH051bVprPUp8yFP1PdPOhLMqlo2jLltQdq5zg)

Cuman tidak perlu khawatir kita akan analisis kedua Java vs Smali agar kita tahu bagian mana yang perlu diubah. Kita mulai dengan activity (java), secara konsep memiliki method yang wajib ada bernama onCreate termasuk di dalam file HardcodeActivity.java.

```java
public void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
	setContentView((int) R.layout.activity_hardcode);
}
```

```java
public void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView((int) R.layout.activity_hardcode);
}
```

Sedangkan pada Smali sebagai berikut :

```java
.method protected onCreate(Landroid/os/Bundle;)V
   .locals 1
   .param p1, "savedInstanceState"	# Landroid/os/Bundle;

   .prologue
   .line 12
   invoke-super {p0, p1}, Landroid/support/v7/app/AppCompatActivity;->onCreate(Landroid/os/Bundle;)V

   .line 13
   const v0, 0x7f04001f

   invoke-virtual {p0, v0}, Ljakhar/aseem/diva/HardcodeActivity;->setContentView(I)V

   .line 14
   return-void
.end method
```

Penjelasan kode smali :

- **.locals 1 :** Mengindikasikan bahwa ada 1 argumen yang akan didefinisikan sebagai **v0**.
- **.param p1, "savedInstanceState" :** Mendefinisikan parameter dari argumen pertama disimpan kedalam register p1.
- **.prologue :** Mengakhiri perkenalan / prolog
- **.line 12 :** Sebagai penanda ketika akan melakukan breakpoint
- **invoke-super {p0, p1}, … :** digunakan untuk memanggil method tertentu dari class induk java.
- **const v0,** 0x7f04001f : Mendefinisikan address memory pada address 0x7f04001f ke variabel v0. Resource tersebut adalah R.layout.activity_hardcode.
- **invoke-virtual {p0, v0}, …** : Pada baris ini memanggil method setContentView dengan parameter v0 (R.layout.activity_hardcode) dan return dari pemanggilan tersebut disimpan ke variabel p0
- **Return-void :** Mengindikasikan bahwa method onCreate tidak memberikan return apapun

Referensi Smali :

- [https://github.com/JesusFreke/smali/wiki/Registers](https://github.com/JesusFreke/smali/wiki/Registers)
- [https://www.aldeid.com/wiki/Category:Architecture/Android/smali](https://www.aldeid.com/wiki/Category:Architecture/Android/smali)
- [http://www.syssec-project.eu/m/page-media/158/syssec-summer-school-Android-Code-Injection.pdf](http://www.syssec-project.eu/m/page-media/158/syssec-summer-school-Android-Code-Injection.pdf)

Diatas merupakan penjelasan smali dari setiap baris pada method onCreate. Untuk mengganti password teman-teman cukup modifikasi pada bagian berikut :

```java
move-result-object v1
const-string v2, "vendorsecretkey"
invoke-virtual {v1, v2}, Ljava/lang/String;->equals(Ljava/lang/Object;)Z
```

Kita ubah **vendorsecretkey** dengan password **sekolahhacker** dan simpan menekan CTRL+S**.** Langkah selanjutnya kita perlu melakukan compile ulang dengan klik project > build. Jika didapatkan output console tanpa error seperti dibawah artinya kemungkinan modifikasi kita sukses.

[https://lh5.googleusercontent.com/ziz0QkeiqAj0bHo7Q-v-WzPCL62zf9ylpB4JYmfyUwNmhOjc70C0_2WSsga2Yg5wh5tOkwkqASoXar4aIEu0x80zdm0X1G5Z8Tf_AnshZkzofCF8_1VYTblINL6y4OzqfjR3qX1UT7GYEQGSwKFLWj2K55Q](https://lh5.googleusercontent.com/ziz0QkeiqAj0bHo7Q-v-WzPCL62zf9ylpB4JYmfyUwNmhOjc70C0_2WSsga2Yg5wh5tOkwkqASoXar4aIEu0x80zdm0X1G5Z8Tf_AnshZkzofCF8_1VYTblINL6y4OzqfjR3qX1UT7GYEQGSwKFLWj2K55Q)

Gambar: Console log di kiri bawah APK Studio

Berikutnya kita perlu mempersiapkan APK certificate untuk menandatangani file APK. Buka terminal lalu jalankan perintah dibawah ini :

```bash
$ keytool -genkey -v -keystore danang.key -alias danang -keyalg RSA -keysize 2048 -validity 365
Enter keystore password:  
Re-enter new password:
What is your first and last name?
  [Unknown]:  DANANG HERIYADI
What is the name of your organizational unit?
  [Unknown]:  SekolahHacker
What is the name of your organization?
  [Unknown]:  Cilsy.ID
What is the name of your City or Locality?
  [Unknown]:  Denpasar
What is the name of your State or Province?
  [Unknown]:  Bali
What is the two-letter country code for this unit?
  [Unknown]:  ID
Is CN=DANANG HERIYADI, OU=SekolahHacker, O=Cilsy.ID, L=Denpasar, ST=Bali, C=ID correct?
  [no]:  yes
 
Generating 2,048 bit RSA key pair and self-signed certificate (SHA256withRSA) with a validity of 365 days
	for: CN=DANANG HERIYADI, OU=SekolahHacker, O=Cilsy.ID, L=Denpasar, ST=Bali, C=ID
[Storing danang]
```

File baru dengan nama danang.key akan terbuat. Kita buka kembali APK Studio > klik project > Sign / Export. Isi sesuai dengan data yang sudah kalian masukkan sebelumnya.

[https://lh3.googleusercontent.com/TKKqSq4K6qunHmsfXKwdPD7oF5qnUFy4Krp7BeQkk9sccYimumQrmE_yN9buZY104us0CbsRPddm8J-XVS6O8An82NrAOHY7HDtXCZGOt84B9QasXpdBooNl1IFk2kQoP5-NRCA379UqegAQh63I9AV1Zj4](https://lh3.googleusercontent.com/TKKqSq4K6qunHmsfXKwdPD7oF5qnUFy4Krp7BeQkk9sccYimumQrmE_yN9buZY104us0CbsRPddm8J-XVS6O8An82NrAOHY7HDtXCZGOt84B9QasXpdBooNl1IFk2kQoP5-NRCA379UqegAQh63I9AV1Zj4)

Tekan **Sign** untuk melanjutkan proses penandatanganan file APK. Jika, proses ini sudah dilakukan file APK akan disimpan di folder dist.