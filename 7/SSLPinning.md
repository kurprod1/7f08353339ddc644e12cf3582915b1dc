# SSL Pinning

Created: June 22, 2022 1:17 PM

Sampai tahap ini pasti kalian sudah mengetahui ternyata enkripsi bisa dipatahkan dengan mudah di materi sebelumnya. Hal ini menjadi PR besar seorang security engineer untuk mengatasi teknik intersepsi sertifikat yang ternyata bisa disabotase dengan memasang sertifikat root CA pada perangkat. Akhirnya user bisa tahu permintaan dan respon yang terjadi antara aplikasi dan server.

Pengamanan permintaan dan respon dari API Server adalah salah satu pertahanan awal dimana jika penyerang bisa mendapatkan informasi tersebut akan memudahkan mereka dalam mengidentifikasi kerentanan pada aplikasi mobile ataupun aplikasi web yang melayani API.

Untuk itulah konsep SSL Pinning muncul, SSL Pinning merupakan teknik untuk validasi sertifikat disisi aplikasi mobile. Untuk teknis penerapan ada banyak sekali metode, misalkan saja verifikasi signature hingga menanamkan sertifikat kunci publik dalam aplikasi android. Imbasnya dengan teknik SSL Pinning lalu lintas data yang tadinya muncul di Burp menjadi tidak tertangkap lagi.

[https://lh3.googleusercontent.com/bvAkCyY41-0dhBZ4y_E9GFFFhuRTgLpkWDFzqv9PCdbt4jQsn6rDdjHiOnHtvTASs01XJobKjLMHqXr2kUQ-S5yz-XIq5g5WhbQ00WMgB3wn1NxAsd-RaibK7fdzp4bkXPlhF4b31pA3cIaFv2SIJ4l5aEw](https://lh3.googleusercontent.com/bvAkCyY41-0dhBZ4y_E9GFFFhuRTgLpkWDFzqv9PCdbt4jQsn6rDdjHiOnHtvTASs01XJobKjLMHqXr2kUQ-S5yz-XIq5g5WhbQ00WMgB3wn1NxAsd-RaibK7fdzp4bkXPlhF4b31pA3cIaFv2SIJ4l5aEw)

Persiapkan sampel APK yang akan kita uji dengan perintah berikut :

```bash
$ git clone https://github.com/ne0z/AndroidSSLPinningByExample.git
```

# **SSL Pinning 1**

Metode SSL Pinning yang pertama menanamkan sertifikat kunci publik di dalam aplikasi. Kalian bisa membuka source code SSLPinning01 untuk menganalisa alur program.

MainActivity.java

```java
private SSLContext getPinnedSSLContext() throws IOException {
   InputStream input = null;
   try {
       input = getResources().openRawResource(
           getResources().getIdentifier("kakdeueoe",
               "raw", getPackageName()));
       return PinnedSSLContextFactory.getSSLContext(input);
   } finally {
       if (null != input) {
       input.close();
       }
   }
}
```

Pada MainActivity.java terdapat method **getPinnedSSLContext** yang menarik. Kita bisa melihat dari source code tersebut bahwa sertifikat terletak pada folder raw dan nama file sertifikatnya adalah kakdeueoe.

Artinya kita memiliki banyak teknik untuk meloloskan perimeter keamanan diatas, bisa dilakukan dengan patching APK, injeksi code dengan Frida, bahkan kalian bisa menemukan teknik lain.

## ***Patching APK***

Tekniknya cukup mudah teman-teman cukup menggunakan APK Studio lalu decompile APK tersebut. Selanjutnya ganti file kakdeueoe yang berada di folder raw dengan sertifikat pem.

[https://lh4.googleusercontent.com/a_n3b3lzrrcOcCDV5Ofo7BsGyOM4AswtMvMRTNdUSBjEFmXv0GgfdvJMNYSPzE4RbWZPSkGqsxLJRw4FjfAMixRd9ExJXcTxrGKgpiKxHKH_VU1b8jpNUHTS0Y2mr3aRLpqo7VLimlyF2fKZO7aHjO4sUmI](https://lh4.googleusercontent.com/a_n3b3lzrrcOcCDV5Ofo7BsGyOM4AswtMvMRTNdUSBjEFmXv0GgfdvJMNYSPzE4RbWZPSkGqsxLJRw4FjfAMixRd9ExJXcTxrGKgpiKxHKH_VU1b8jpNUHTS0Y2mr3aRLpqo7VLimlyF2fKZO7aHjO4sUmI)

Sertifikat PEM bisa dibangkitkan dengan menjalankan perintah dibawah ini di lokasi direktori tempat kalian membangkitkan sertifikat sebelumnya.

```bash
$ openssl x509 -inform DER -in ca.der -out ca.pem
$ cp ca.pem <lokasi file kakdeueoe.dat>
```

Setelah sertifikat bawaan APK diganti dengan sertifikat milik kalian. Selanjutnya build dengan APK Studio dan jangan lupa di tanda tangani di menu **Sign / Export**. Dan tinggal kalian install APK yang sudah dibuat biasanya tersimpan di folder **dist**.

[https://lh5.googleusercontent.com/rrMjH_2B45VnLGct9WRPAmRne9Cl-gDFCGLoFV0ij0S-vdk3PDYn0NITkoibya2M5zV7T5g8w79ARPEY5XqIKHag8Ogfo2o-Z246gMgXG3oDlNXsk3KSGV-Iwd_PjTccU8rPokn10bQlrr0VrYevVWKIKv0](https://lh5.googleusercontent.com/rrMjH_2B45VnLGct9WRPAmRne9Cl-gDFCGLoFV0ij0S-vdk3PDYn0NITkoibya2M5zV7T5g8w79ARPEY5XqIKHag8Ogfo2o-Z246gMgXG3oDlNXsk3KSGV-Iwd_PjTccU8rPokn10bQlrr0VrYevVWKIKv0)

Gambar: APK hasil patch tersimpan di folder dist

Jika ketika proses build memunculkan error :

- No resource identifier found for attribute 'compileSdkVersion' in package 'android'
- No resource identifier found for attribute 'compileSdkVersionCodename' in package 'android'
- No resource identifier found for attribute 'appComponentFactory' in package 'android'

Untuk menyelesaikan error di atas hanya perlu menghapus **android:compileSdkVersion="29"**, **android:compileSdkVersionCodename="10"**, dan **android:appComponentFactory="androidx.core.app.CoreComponentFactory"** pada AndroidManifest.xml.

Contoh setelah di edit :

```xml
<?xml version="1.0" encoding="utf-8" standalone="no"?><manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.danang.sslpinning01" platformBuildVersionCode="29" platformBuildVersionName="10">
    <uses-permission android:name="android.permission.INTERNET"/>
    <application android:allowBackup="true" android:extractNativeLibs="false" android:icon="@mipmap/ic_launcher" android:label="@string/app_name" android:roundIcon="@mipmap/ic_launcher_round" android:supportsRtl="true" android:theme="@style/AppTheme">
        <activity android:name="com.danang.sslpinning01.MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
    </application>
</manifest>
```

## **SSL Pinning 2**

Metode SSL Pinning yang kedua sangat berbeda dengan sebelumnya. Jika kalian lihat di dalam source code SSLPinning02 tidak menanamkan sertifikat. Tapi jika kalian jeli, pada source code MainActivity.java terdapat kode menarik.

MainActivity.java

```java
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    btnSend = (Button) findViewById(R.id.send);
    txtResponse = (TextView) findViewById(R.id.txtResponse);
    CertificatePinner certificatePinner = new CertificatePinner.Builder()
      .add(getDomainName(URL), getResources().getString(R.string.raw_data_01))
      .add(getDomainName(URL), getResources().getString(R.string.raw_data_02))
      .add(getDomainName(URL), getResources().getString(R.string.raw_data_03))
      .build();
```

Menurut source code diatas SSL Pinning dilakukan dengan memberikan string tertentu yang tersimpan di file strings.xml.

strings.xml

```xml
<resources>
   <string name="app_name">SSLPinning02</string>
   <string name="raw_data_01">sha256/J5XT698Ii2FMQ9STFztKZjeOOIABog90rejnAFGFi0w=</string>
   <string name="raw_data_02">sha256/4a6cPehI7OG6cuDZka5NDZ7FR8a60d3auda+sKfg4Ng=</string>
   <string name="raw_data_03">sha256/x4QzPSC810K5/cMjb05Qm4k3Bw5zBn4lTdO/nEW/Td4=</string>
</resources>
```

Seperti yang teman-teman perhatikan diatas, SSL diverifikasi berdasarkan hash signature base64. Sehingga jika teman-teman ingin melewati perimeter keamanan tersebut. Kalian harus mengubah Hash sertifikat asli dengan Hash sertifikat palsu Burp kita.

### ***Melewati Perimeter Hash***

Hash yang di encode dalam bentuk base64 diperlukan untuk bisa merubah nilainya sesuai dengan sertifikat milik kita. Perintah dibawah ini diperlukan untuk mendapatkan hash 256 dalam bentuk base64 :

```bash
$ openssl x509 -in ca.pem -pubkey -noout | openssl rsa -pubin -outform der | openssl dgst -sha256 -binary | openssl enc -base64
```

Pastikan anda menjalankan perintah diatas pada folder dimana kalian membangkitkan sertifikat sebelumnya. Pada laptop penulis didapatkan hashnya adalah **NRtnjrFfc1I7L1RfDA5lBppuhhSNmRnZ0OGptgUlbxg=** dan tinggal kita masukkan nilai hash ini dengan Patch ataupun dengan Frida.

# Exercise

1. Jika kalian sebelumnya sudah berhasil melewati perimeter pada aplikasi **SSLPinning01** dengan patch APK. Silahkan kalian bypass **SSLPinning01** dengan menggunakan Frida.
2. Buatlah dokumentasi proses SSL Pinning bypass pada aplikasi **SSLPinning02** dengan menggunakan teknik Patch maupun dan dengan Frida script.