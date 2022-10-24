# Dasar Penggunaan Frida

Created: June 22, 2022 1:17 PM

Jika teman-teman sudah belajar untuk memodifikasi alur program dengan teknik patching. Kali ini kita akan merubah value dengan teknik tamper code. Dan untuk target kali ini kita akan gunakan UnCrackable Level 1.

```bash
$ wget https://raw.githubusercontent.com/OWASP/owasp-mstg/master/Crackmes/Android/Level_01/UnCrackable-Level1.apk
$ adb install UnCrackable-Level1.apk
```

[https://lh6.googleusercontent.com/uPEZoDK5wjyQTJEnIVXnpZcAyd7r1JW-5EUR6prLJ3O4Dz2Kfbh6ZbA2opvyxonxANAS1FoOyG23iQxDFYJu6egcDfmfSRT3HgD-G2s3JFSaKqOoRdBRoWU5FswjtyuSPCObelVpAhzz_XwZdjxsqxt_BFk](https://lh6.googleusercontent.com/uPEZoDK5wjyQTJEnIVXnpZcAyd7r1JW-5EUR6prLJ3O4Dz2Kfbh6ZbA2opvyxonxANAS1FoOyG23iQxDFYJu6egcDfmfSRT3HgD-G2s3JFSaKqOoRdBRoWU5FswjtyuSPCObelVpAhzz_XwZdjxsqxt_BFk)

Ketika adb install selesai dijalankan, kalian bisa mencoba membuka aplikasinya. Sebelumnya teman-teman sudah berhasil melakukan patching APK untuk merubah alur aplikasi agar sesuai dengan keinginan kita. Kali ini kita akan merubah alur program tanpa merusak file APK tersebut menggunakan teknik tamper dan injeksi code dengan Frida.

Untuk bisa melewati perimeter keamanan **root detection** kita bisa melihat java source code terlebih dahulu menggunakan APK Studio.

1. **MainActivity.java**

Pada method onCreate terdapat conditional statement, yang mana jika c.a(), c.b(), dan c.c() salah satu menghasilkan nilai **true** maka akan muncul popup “Root detected”. Artinya jika merubah nilai dengan menggunakan teknik patching ataupun injeksi code dengan Frida maka kita akan bisa melewati perimeter pertama.

```java
public void onCreate(Bundle bundle) {
   	if (c.a() || c.b() || c.c()) {
       	a("Root detected!");
   	}
   	if (b.a(getApplicationContext())) {
       	a("App is debuggable!");
   	}
   	super.onCreate(bundle);
   	setContentView(R.layout.activity_main);
   }
```

Sebelum itu jika kita amati lebih lanjut c.a(), c.b(), dan c.c() di import melalui baris ini:

```java
import sg.vantagepoint.a.c;
```

Dan dalam c.java terdapat kode sumber yang berfungsi untuk mendeteksi **root**.

c.java

```java
package sg.vantagepoint.a;
import android.os.Build;
import java.io.File;

public class c {
   public static boolean a() {
   	for (String file : System.getenv("PATH").split(":")) {
       	if (new File(file, "su").exists()) {
           	return true;
       	}
   	}
   	return false;
   }

   public static boolean b() {
   	String str = Build.TAGS;
   	return str != null && str.contains("test-keys");
   }

   public static boolean c() {
   	for (String file : new String[]{"/system/app/Superuser.apk", "/system/xbin/daemonsu", "/system/etc/init.d/99SuperSUDaemon", "/system/bin/.ext/.su", "/system/etc/.has_su_daemon", "/system/etc/.installed_su_daemon", "/dev/com.koushikdutta.superuser.daemon/"}) {
       	if (new File(file).exists()) {
           	return true;
       	}
   	}
   	return false;
   }
}
```

Langkah awal untuk hook pada method a, b, c dalam class c.java bisa dilakukan dengan script berikut :

```java
Java.perform(function () {
  console.log("Frida script is runnning");
  var c = Java.use('sg.vantagepoint.a.c');
  c.c.implementation = function () {
    console.log("Inside c.c()");
    return this.c.call(this);
  }
  c.b.implementation = function () {
    console.log("Inside c.b()");
    return this.b.call(this);
  }
  c.a.implementation = function () {
    console.log("Inside c.a()");
    return this.a.call(this);
  }
});
```

Simpan source code diatas dengan nama uncrackablehook1.js. Kita bisa menjalankannya dengan perintah dibawah ini :

```java
$ frida -U -l uncrackablehook1.js -f owasp.mstg.uncrackable1 --no-pause
[Mobile App Pentest::owasp.mstg.uncrackable1]-> Frida script is runnning
Inside c.a()
```

Nah muncul log “Inside c.a()”, yang berarti **c.c.implementation = function(){...}** berhasil terpicu di halaman pertama. Sehingga jika kita ingin memaksa mengembalikan nilai **false** kita bisa ganti **return this.a.call(this)** menjadi **return false;**

```java
Java.perform(function () {
  console.log("Frida script is runnning");
  var c = Java.use('sg.vantagepoint.a.c');
  c.c.implementation = function () {
    console.log("Inside c.c()");
    return this.c.call(this);
  }
  c.b.implementation = function () {
    console.log("Inside c.b()");
    return this.b.call(this);
  }
  c.a.implementation = function () {
    console.log("Inside c.a()");
    return false;
  }
});
```

Jalankan script diatas maka akan keluar output yang berbeda, bisa teman-teman lihat di tangkapan layar di bawah ini.

[https://lh3.googleusercontent.com/bzuWP92ItQPLLRF5bm-DWzH099_56MMImTfsZxRcInXeUIHch2HTRZ6mYZBn72ILVoD-7hYZhycAaJyjrjRvg7PYBD-tGZhlsEo-6ClCPNLNDuQCML60v35xD9JPQAfFYjK7Mp4N8vbas13beoPuwy6fKkU](https://lh3.googleusercontent.com/bzuWP92ItQPLLRF5bm-DWzH099_56MMImTfsZxRcInXeUIHch2HTRZ6mYZBn72ILVoD-7hYZhycAaJyjrjRvg7PYBD-tGZhlsEo-6ClCPNLNDuQCML60v35xD9JPQAfFYjK7Mp4N8vbas13beoPuwy6fKkU)

Nah sekarang muncul pesan “Inside c.a()”. Kita akan lakukan cara sama untuk membuat method c.a() memberikan kembalian **false** begitu pula method yang c.b().

```java
Java.perform(function () {
  console.log("Frida script is runnning");
  var c = Java.use('sg.vantagepoint.a.c');
  c.c.implementation = function () {
    console.log("Inside c.c()");
    return false;
  }
  c.b.implementation = function () {
    console.log("Inside c.b()");
    return false;
  }
  c.a.implementation = function () {
    console.log("Inside c.a()");
    return false;
  }
});
```

Jika script diatas dijalankan akan mengeluarkan output yang berbeda pada layar android. Hal ini disebabkan karena kita sudah berhasil melewati perimeter keamanan pertama.

[https://lh6.googleusercontent.com/Br9YHWcDeBtuAMMcJtAD1NT7YUQmS_oqN5XDDMOIRpCNCvZ4jGNfEj0ybejMEHfIWPoZMGCG1qELFoeLQmKwn2LKu4Mg8Nja-fFvwpjWN9RXN4E0CYKjMoPpxzqFpfAN3XW1SGo60LaX7Fk38PpKGn45neA](https://lh6.googleusercontent.com/Br9YHWcDeBtuAMMcJtAD1NT7YUQmS_oqN5XDDMOIRpCNCvZ4jGNfEj0ybejMEHfIWPoZMGCG1qELFoeLQmKwn2LKu4Mg8Nja-fFvwpjWN9RXN4E0CYKjMoPpxzqFpfAN3XW1SGo60LaX7Fk38PpKGn45neA)

Yap, akhirnya kita berhasil melewati perimeter pertama. Dan sudah tidak muncul lagi pesan **root detected**.

# **Exercises**

- Jika pada materi sebelumnya kalian sudah bisa menggunakan Frida untuk melewati perimeter keamanan **root detection**. Tugas pertama, kalian harus menggunakan teknik patching untuk melewati deteksi root dengan APK Studio. Dokumentasikan prosesnya!
- Gunakan Frida untuk mendapatkan Secret String. Dokumentasikan prosesnya!