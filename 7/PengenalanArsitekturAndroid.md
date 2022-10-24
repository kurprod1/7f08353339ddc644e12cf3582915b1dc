# Pengenalan Arsitektur Android

Created: June 22, 2022 1:17 PM

Banyak orang beranggapan bahwa arsitektur linux dan android sama meski memiliki basis OS Linux. OS Linux, penjelasan lebih tepatnya kernel Linux adalah OS paling populer sementara Android adalah Framework yang dibangun di atas kernel Linux. Jadi setiap perangkat Android menjalankan kernel Linux juga, tetapi setiap perangkat Linux tidak memiliki Android. Kita dapat menganggap kernel Linux sebagai dasar dimana Android dibangun. Juga Android tidak terbatas pada Mobiles saja.

[https://lh3.googleusercontent.com/0gNBLqtYdOjZDJQJJGwiQrrr9FfEg-n5K5AvQK5zmwKUvOCyHMjxCc2kLtIhDmWu4-doFKhkqpJziFvGP92eqZPhqrdAoIlrJGVZa82DpSacBC3glGzSt0NoE1-9nH5TX8VTX-JSz6RvW7PYoGUPBNDhuXE](https://lh3.googleusercontent.com/0gNBLqtYdOjZDJQJJGwiQrrr9FfEg-n5K5AvQK5zmwKUvOCyHMjxCc2kLtIhDmWu4-doFKhkqpJziFvGP92eqZPhqrdAoIlrJGVZa82DpSacBC3glGzSt0NoE1-9nH5TX8VTX-JSz6RvW7PYoGUPBNDhuXE)

Seperti yang kalian lihat pada gambar diatas bahwa aplikasi android terletak pada bagian teratas sedangkan pemanggilan API tertentu dijembatani oleh Android Framework. Kemudian Android Framework akan menghubungkan antara Aplikasi dengan Hal dan Linux Kernel melalui Android Runtime.

Jika sebelumnya kita membahas mengenai Guest OS pada virtualbox yang dijalankan oleh Hypervisor. Sedangkan Aplikasi Android dijalankan di atas Dalvik Virtual Machine.

# **Mempersiapkan Android Emulator**

Proyek android app penetration testing biasanya perlu menggunakan perangkat android baik perangkat hardware asli ataupun emulator. Hal ini diperlukan untuk menguji aplikasi secara fungsional. Perangkat yang digunakan juga harus dalam kondisi memiliki akses **root**.

Untuk mempersiapkan Android Emulator, kita akan menggunakan **Genymotion**, sebuah emulator Android source code yang dapat di unduh [di sini](https://www.genymotion.com/download/).

## **Installing Virtualbox**

Genymotion menggunakan **virtualbox** sebagai emulator androidnya. Maka dari itu, disarankan menggunakan versi terbaru dari Virtualbox.

[https://lh5.googleusercontent.com/R0Qd1aNevMSNAT1zXqF_t9jaAW4VvfB6egHjOLalhMcL2q8Hxo0V-9C2t6HtHeJ9kxHFul0g_SIZuRbw9Cj_VVNFITl3OyI8lcnCk-X69TlAqcXJe017mguq_YF3M_S6a071yzeTO2t9nwJabg](https://lh5.googleusercontent.com/R0Qd1aNevMSNAT1zXqF_t9jaAW4VvfB6egHjOLalhMcL2q8Hxo0V-9C2t6HtHeJ9kxHFul0g_SIZuRbw9Cj_VVNFITl3OyI8lcnCk-X69TlAqcXJe017mguq_YF3M_S6a071yzeTO2t9nwJabg)

Untuk platform Windows, Virtualbox dapat diunduh di [link berikut](https://download.virtualbox.org/virtualbox/6.1.26/VirtualBox-6.1.26-145957-Win.exe). Lalu install sesuai instruksi dari aplikasi

Untuk platform Linux, Virtualbox dapat diinstall dengan menggunakan langkah berikut.

```bash
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

$ sudo apt-get update
$ sudo apt-get install virtualbox-6.1
```

# **Installing Genymotion**

Untuk materi dengan waktu yang sangat singkat ini akan lebih mudah jika kita menggunakan emulator, karena akan memiliki kondisi yang sama dengan semua. Emulator yang akan kita gunakan adalah Genymotion bisa kalian mendaftar akun Desktop Sign in terlebih dahulu melalui situs resminya [https://www.genymotion.com](https://www.genymotion.com/).  Selanjutnya kalian bisa mengikuti step dibawah ini.

Download genymotion untuk linux :

```bash
$ curl -O https://dl.genymotion.com/releases/genymotion-3.2.1/genymotion-3.2.1-linux_x64.bin
$ chmod +x genymotion-3.2.1-linux_x64.bin
$ sudo ./genymotion-3.2.1-linux_x64.bin
```

[https://lh3.googleusercontent.com/NfSz54nTP-cDXfGUb10fR_YqRDVxC4EAI5k06TUERJH-DqMGL3FIz1Pin86DyTXkFHREtym2AJeCbi1C2LjjYLaeZBPIWTODHozcN2M6m_JScbX-zREG5NQ3UW3VQmTT6SizM9cx-tOVfVGdBw](https://lh3.googleusercontent.com/NfSz54nTP-cDXfGUb10fR_YqRDVxC4EAI5k06TUERJH-DqMGL3FIz1Pin86DyTXkFHREtym2AJeCbi1C2LjjYLaeZBPIWTODHozcN2M6m_JScbX-zREG5NQ3UW3VQmTT6SizM9cx-tOVfVGdBw)

Pada kasus ini misalnya, saya menginstal genymotion di directory **/opt/genymobile/genymotion**. Ketika ingin menjalankan Genymotion, kita bisa menggunakan perintah berikut.

```bash
/opt/genymobile/genymotion/genymotion
```

[https://lh4.googleusercontent.com/_efdaje3Fe5bmi99F8PU5NO17BdOLNkgHNJPlly6DQo6jaYy5-5_6gX99ZwT2xl0jMy7FFfls4t_w8f_wncj5bIv27E-a3Uwn8Nbsa6u3LMKs3ztfsmZh1bRv7keagfubKT73klCChhqgVTZfg](https://lh4.googleusercontent.com/_efdaje3Fe5bmi99F8PU5NO17BdOLNkgHNJPlly6DQo6jaYy5-5_6gX99ZwT2xl0jMy7FFfls4t_w8f_wncj5bIv27E-a3Uwn8Nbsa6u3LMKs3ztfsmZh1bRv7keagfubKT73klCChhqgVTZfg)

Jangan tutup tab terminal ini saat menggunakan Genymotion.

Jika laptop kalian menggunakan windows silahkan download versi Windows di situs resmi genymotion.

Setelah genymotion terinstal kalian bisa menjalankannya via menu baik itu di Windows ataupun di Ubuntu biasanya sudah muncul. Kemudian log-in sesuai dengan akun yang sudah kalian daftarkan sebelumnya.

[https://lh4.googleusercontent.com/v5Wg8Z3ZP5e6jy9are7VB-k0HhF__Ab_nRq97qEGHne0E7QJ3asCwRfylp5xCiYRganCrzS0RaFdxG-9m0TDFSE9UFt5xw1-viedAJ0vh8Ak0CDHrIY1AjxZMAON3ij_N7egVJNXES2sugRBZsb6IfMKHDY](https://lh4.googleusercontent.com/v5Wg8Z3ZP5e6jy9are7VB-k0HhF__Ab_nRq97qEGHne0E7QJ3asCwRfylp5xCiYRganCrzS0RaFdxG-9m0TDFSE9UFt5xw1-viedAJ0vh8Ak0CDHrIY1AjxZMAON3ij_N7egVJNXES2sugRBZsb6IfMKHDY)

Langkah selanjutnya kalian perlu menekan tombol (+) pada sisi kanan atas agar bisa menambahkan emulator android terbaru. Pilih “custom phone” dengan OS Android versi 9.0.

[https://lh6.googleusercontent.com/vx4WUjItzz-p62QTrPDSjpSh4KQXiGjo2BPnWAAzk_fyf0LyFFaP8Hxk2RyOpYfZx_kjdlaiqvG35bBoTUf2cZN9C59_JFAABpO4SVUWmY4R_GVhCSBAmmmOaMzRMpNtRTeyA0Rk4ukQUfd3ap3gwpCIPzI](https://lh6.googleusercontent.com/vx4WUjItzz-p62QTrPDSjpSh4KQXiGjo2BPnWAAzk_fyf0LyFFaP8Hxk2RyOpYfZx_kjdlaiqvG35bBoTUf2cZN9C59_JFAABpO4SVUWmY4R_GVhCSBAmmmOaMzRMpNtRTeyA0Rk4ukQUfd3ap3gwpCIPzI)

Gambar: Pilihan perangkat android

Sesuaikan RAM dan processor sesuai dengan kapasitas laptop kalian, namun perlu teman-teman ketahui agar android device berjalan sangat mulus minimal RAM harus diberikan adalah 1 GB.

[https://lh4.googleusercontent.com/hPlHcC4tVu0pdJhSuBMG_OXBtSc4KU8In5MV61mZYPA-lRbfaA3KDdX8fuDarLm6OJbGR_ujpD_8pVOvi7iXYWEv-s7bATmzcUmO7JlKjOaBhauOhnZ_hQKFDJGoe01lH7eYLJqnuFopiPf2CRSHxezCJWQ](https://lh4.googleusercontent.com/hPlHcC4tVu0pdJhSuBMG_OXBtSc4KU8In5MV61mZYPA-lRbfaA3KDdX8fuDarLm6OJbGR_ujpD_8pVOvi7iXYWEv-s7bATmzcUmO7JlKjOaBhauOhnZ_hQKFDJGoe01lH7eYLJqnuFopiPf2CRSHxezCJWQ)

Jika kalian sudah menekan tombol **INSTALL** pada tampilan tersebut maka proses selanjutnya genymotion akan mengunduh VDI dari server mereka. Step ini akan lebih efisien jika teman-teman mempersiapkan sebelum pelatihan dimulai karena file yang diunduh sangat besar.

[https://lh6.googleusercontent.com/8Wr6u0YN-OEMF6H6DYPQRF3u9zI83O2GETyS8-2dD0ib1UXpS0_Rm1CtZJ56bNDdTHdqNL1kVRGPz3hFm33WwEKZpg__0EExQiKBttWiqm8UKHutaMzohVayU_vh7W7efFhYeGvsACvyZ2KU4CsdYxFynB4](https://lh6.googleusercontent.com/8Wr6u0YN-OEMF6H6DYPQRF3u9zI83O2GETyS8-2dD0ib1UXpS0_Rm1CtZJ56bNDdTHdqNL1kVRGPz3hFm33WwEKZpg__0EExQiKBttWiqm8UKHutaMzohVayU_vh7W7efFhYeGvsACvyZ2KU4CsdYxFynB4)

Gambar: Proses mengunduh android VDI

Setelah proses download selesai, teman-teman bisa mengklik 2x pada item diatas untuk menjalankan emulator android.

[https://lh6.googleusercontent.com/3-U8ZPa4uGlnD281knCMoYVUeFn_x4C1Rq3eCgXWSSz3Pnlba7_oCuFmstEL_Rz8cyPi_F6TazmJAuRTUE5GW20VP1BapWO_buKQOyYBbVqSDgj2-EBiCpMRhq5NJ_iLCkjtbyVDihi3mMY3_sz7Lw1Wutc](https://lh6.googleusercontent.com/3-U8ZPa4uGlnD281knCMoYVUeFn_x4C1Rq3eCgXWSSz3Pnlba7_oCuFmstEL_Rz8cyPi_F6TazmJAuRTUE5GW20VP1BapWO_buKQOyYBbVqSDgj2-EBiCpMRhq5NJ_iLCkjtbyVDihi3mMY3_sz7Lw1Wutc)

Pastikan di laptop kalian menampilkan seperti screenshot diatas. Selanjutnya kita perlu menguji apakah sudah terdapat akses **root** pada emulator tersebut menggunakan terminal pada host utama kalian. Tapi pastikan terlebih dahulu **USB Debugging** sudah diaktifkan, bisa kalian cek di setting > Developer Options

[https://lh5.googleusercontent.com/6VFuXDxfcWTIcqNdolZ_vQexHxI0dyOfU2fWYVfCc9iUz7MY5n0IVl3tqaJi0BofazzDidtzkcCk3agL-zNnFSf_kcS9-prH1fThEOioX0i5DJRaJvhxxt-AEfHGJlvjz-MU0U52933bi0svJetkQbd-s8c](https://lh5.googleusercontent.com/6VFuXDxfcWTIcqNdolZ_vQexHxI0dyOfU2fWYVfCc9iUz7MY5n0IVl3tqaJi0BofazzDidtzkcCk3agL-zNnFSf_kcS9-prH1fThEOioX0i5DJRaJvhxxt-AEfHGJlvjz-MU0U52933bi0svJetkQbd-s8c)

Langkah selanjutnya adalah menghubungkan emulator dengan laptop menggunakan ADB.

Sekilas tentang ADB, Android Debug Bridge (adb) adalah tools yang memungkinkan berkomunikasi dengan device. Perintah adb memfasilitasi berbagai action untuk device, seperti menginstal dan men-debug aplikasi, dan menyediakan akses ke shell Unix yang dapat Anda gunakan untuk menjalankan berbagai perintah pada device.

Oh iya, Genymotion dibekali dengan tools tools yang diperlukan salah satunya adalah ADB itu sendiri. Pada Linux, tools adb ini berada di directory Genymotion diinstall. Dalam contoh ini, di **/opt/genymobile/genymotion/genymotion/tools/adb**

Tahapan untuk mengecek akses root bisa dilakukan dengan perintah berikut :

```bash
$ /opt/genymobile/genymotion/tools/adb devices
List of devices attached
192.168.57.102:5555	device

$ adb shell whoami
root
$ adb shell getprop ro.product.cpu.abi
```

[https://lh3.googleusercontent.com/_vG3oi3gLWkKjp90Hoo50mye-S4jZw1qI8QhjuhpqEeNw59H9lNRE6255_1byGU2Y0gOXcWw4D7Kuq14dWOqiFXDE4Ee6k2Qy6iOYB1qBoJKimnreJG9CPRoloOw9KqHiiTNmGBD4o6qOZv7Tw](https://lh3.googleusercontent.com/_vG3oi3gLWkKjp90Hoo50mye-S4jZw1qI8QhjuhpqEeNw59H9lNRE6255_1byGU2Y0gOXcWw4D7Kuq14dWOqiFXDE4Ee6k2Qy6iOYB1qBoJKimnreJG9CPRoloOw9KqHiiTNmGBD4o6qOZv7Tw)

Nah pada output perintah **whoami** bisa kita simpulkan bahwa kita memiliki akses bawaan sebagai root. Sedangkan perintah terakhir untuk melihat arsitektur prosesor android emulator yang kita gunakan.