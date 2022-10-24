# Linux Basic Command

Created: October 19, 2022 12:47 PM

Pada dasarnya, Linux merupakan sistem operasi yang berbasiskan pada   text   (Text   Bases)   dalam   sistem   kerjanya.   Bila   ingin   melakukan sesuatu terhadap komputer, user bisa mengetikkan perintah-perintah yang kemudian dieksekusi oleh komputer. Sehingga mode teks terus melekat dengan Linux sampai saat ini, walaupun sekarang tampilan GUI (Graphical User   Interface)   Linux   sudah   semakin   bagus   dan   memudahkan   user. Perintah-perintah yang diketikkan itu biasa disebut Command Line. Untuk perintah-perintah dasar, biasa disebut Basic Command Line.

**“Bila sudah ada GUI, Kenapa harus menggunakan Perintah Dasar?”**

Pertanyaan bagus.. Saat ini, Anda bisa melakukan banyak hal di GUI. Untuk melakukan manajemen file dan direktori tinggal klik sudah beres. Mau putar lagu, nonton film, edit document, edit gambar, add remove aplikasi, konfigurasi desktop dsb., semua bisa dilakukan dengan mudah dari   GUI   dengan   menggunakan   mouse.   Tetapi,   bila   anda   menguasai perintah dasar linux ada beberapa hal yang lebih mudah dan cepat bila dilakukan dari mode teks, bahkan ada beberapa hal yang hanya bisa dilakukan dengan Command Line. Semakin menarik kan..? :-)

# **Cara Mengakses Terminal**

Untuk mempelajari atau mencoba perintah dasar Linux, Adan bisa membuka Terminal atau Console. Biasanya, di PC/laptop yang baru saja diinstallkan Ubuntu, terminal ada di bagian start menu dan juga ada pada desktop bar yang tersedia. Apabila Anda ingin mengkases dengan cepat, Anda dapat menggunakan shortcut yaitu dengan menekan tombol **CTRL + Alt + T** pada keyboard Anda secara bersamaan.

## **Komponen-Komponen Terminal**

Setelah muncul tampilan Terminal seperti yang ditunjukkan gambar sebelumnya, kita dapat melihat beberapa komponen atau bagian dari Terminal ini. Berikut ada alah beberapa penjelasan mengenai komponen-komponen pada terminal.

![https://static.javatpoint.com/tutorial/kali-linux/images/kali-linux-commands.png](https://static.javatpoint.com/tutorial/kali-linux/images/kali-linux-commands.png)

**Title Bar (Baris Judul)**

Merupakan bagian paling atas window, biasanya menampilkan informasi direktori yang sedang aktif.

**Menu Bar (Baris Menu)**

Merupakan baris yang urutannya dibawah judul. Bagian ini berisimenu-menu yang bisa Anda pilih sesuai dengan kebutuhan.

Menu yang bisa Anda Pilih adalah:

**File**

Anda bisa memilih menu ini bila ingin membuka shell baru, membuka window baru, melakukan print screen, menutup shell   dan   menutup   window.

**Edit**

Di menu ini anda bisa melakukan copy, paste, membersihkanlayar   dengan   clear terminal,   mencari   perintah-perintah terdahulu , dll.

**View**

Menu ini berkaitan dengan tampilan window konsole anda.

**Terminal**

**Tabs**

**Help**

Anda bisa mendapatkan bantuan mengenai pemakaian konsole secara lengkap di sub menu ini.

**Terminal Area**

Didalamnya terdapat prompt yang diakhiri dengan kursor dimana kita bisa mengetikkan perintah yang kita inginkan. Di area ini juga akan ditampilkan hasil dari perintah-perintah yang kita ketikkan.

### **Prompt**

Di dalam terminal area akan tampil tulisan yang bisa kita sebut **prompt**, dimana di bagian akhir prompt ada kursor yang berkedip, disini Anda   bisa   mulai   menuliskan   perintah   dasar.   Pada   saat   pertama   kali membuka window terminal, secara default prompt akan seperti dibawah ini.

```
user@kali: -$
```

Keterangan:

**user** → nama user yang aktif saat ini.

**kali** →  nama komputer/hostname

**~ →**  direktori/folder yang sedang aktif, tanda ~ menunjukkan bahwa anda sedang berada di direktori/home

**$ →** menunjukkan bahwa user yang sedang aktif adalah user biasa, tanda $ akan berubah menjadi **#** bila user yang aktif adalah root.

Biasanya   window   konsole   memiliki   background   berwarna   hitam. Mungkin Anda pernah membaca poster salah satu sistem operasi yang lisensinya berbayar, bila Anda menggunakan software bajakan dari sistem operasi tersebut, anda akan memasuki mode fungsi terbatas (layar hitam) jika tidak diaktifasi dengan produk key asli. Jadi anda harus membeli lisensinya atau menginstall ulang software bajakan anda. Tapi kalau di Linux, justru saat masuk ke layar hitam anda memiliki “kemampuan tanpa batas”, karena di layar hitam ini anda bisa menjalankan perintah apapun sesuai dengan hak akses yang anda punya.

# **Format Penulisan Perintah di Linux**

Perintah dasar di linux ditulis dengan format dibawah ini

```
$ nama_perintah [ argument ]
```

Keterangan:

- **Prompt**: $ menunjukkan user biasa, dan # menunjukkan user root.
- **Nama perintah**: adalah perintah yang ingin anda jalankan
- **Argument**: sesuatu yang ditambahkan ke perintah dasar, pada umumnya argument terdiri dari OPTION dan PATH
- **OPTION**: adalah pilihan yang bisa anda gunakan untuk menghasilkan kondisi tertentu dari suatu perintah.
- **PATH** : adalah sesuatu yang akan diproses oleh perintah, misalnya nama file atau nama direktori.
- **Tanda [...]** pada argument menunjukkan kalau **argument bersifat optional**, jadi argument tidak harus ada dalam sebuah perintah dasar. Untuk perintah yang akan diberi OPTION aturan penulisannya adalah setelah nama perintah, sebelum OPTION ditambahkan tanda dash (-). Anda bisa menggunakan option lebih dari satu, sesuai dengan kebutuhan Anda. Contoh penulisan perintah bisa anda lihat pada contoh dibawah ini.

## Contoh penulisan perintah

Penulisan perintah tanpa menggunakan argument

```
ls
```

Penulisan perintah dengan menggunakan  argument berupa option

```
ls – l
```

Penulisan perintah dengan menggunakan argument berupa path

```
ls /etc
```

Penulisan perintah dengan menggunakan argument berupa option dan path

```
ls -l /etc
```

Pada saat menuliskan perintah, ada beberapa aturan yang harus kita ikuti,antara lain:

**Case Sensitive (penggunaan huruf besar dan huruf kecil).**

Dalam   menuliskan perintah   harus   diperhatikan   apakah   perintah tersebut   menggunakan   huruf besar  atau   huruf   kecil.   Karena   huruf besar dan huruf kecil diartikan berbeda. Bila ada kekeliruan perintah tidak mau dijalankan atau terjadi error.

**Penggunaan tanda baca dan spasi.**

Anda  harus  meneliti   penggunaan  titik  (.),   koma (,), slash (/) atau backslash (\). Begitu juga dengan spasi. Karena bila terjadi kesalahan dalam penggunaan tanda baca dan spasi, perintah juga tidak bisa dijalankan.

**Ejaan kata dari perintah yang digunakan**

Pastikan perintah anda sudah benar ejaan katanya. Perintah-perintahyang ada menggunakan bahasa inggris.

## Tips Memahami Perintah di Linux

Untuk mempermudah proses belajar kalian, ada beberapa hal yang bisa kamu lakukan, diantaranya:

- **Baca Manual Guide dari Perintah tersebut.** Caranya adalah dengan mengetikkan perintah man <spasi> [nama perintah yang ingin diketahui detailnya], maka akan muncul manual page dari perintah yang ingin dicari.
- **Buat "contekan" atau rangkuman perintah yang sering digunakan**. Hal ini akan memudahkan kalian untuk mengingat detail perintah apabila ada yang terlupa. Untuk cheatsheet linux command, kalian bisa download di file yang kami sematkan ya!

![Linux Cheatsheet](/3/Linux%20Basic%20Command%20762b529e9a684e22953e30e5653e6c02/Linux_Cheatsheet.png)

# Must Read Material

- [Basics of Linux](https://d00mfist.gitbooks.io/ctf/content/basics_of_linux.html)

# References

<center>

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</center>

- [Kali Docs | Kali Linux Documentation](https://www.kali.org/docs/)

- [Parrot Documentation](https://www.parrotsec.org/docs/)