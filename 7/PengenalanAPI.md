# Pengenalan API

Created: June 22, 2022 1:17 PM

Pada era modern ini banyak masyarakat menggunakan smartphone untuk menyelesaikan urusan mereka. Dari mulai pemesanan makanan (Go-Food) hingga investasi yang bisa kita kendalikan melalui ponsel pintar ini.

![Untitled](Pengenalan%20API%20bd1f335f1ad44ef4a144499cf45dc508/Untitled.png)

Tentunya era ini sangat berubah total jika kita bandingkan dengan di tahun 2012 dimana internet masih sedikit dipergunakan untuk kebutuhan sehari-hari. Dengan mudahnya kita menggunakan akses internet dan harga yang terjangkau, inovasi bisa berkembang pesat hingga memudahkan komunikasi antar sistem ataupun manusia.

Salah satu inovasi tersebut yakni penggunaan konsep API (*Application Programming Interface*). Penggunaan konsep tersebut memungkinkan antar sistem yang berbeda bisa saling terhubung dan berkomunikasi secara harmonis.

Sebagai contoh aplikasi Go-Food di android ketika pengguna memesan makanan maka di belakang layar aplikasi tersebut akan menghubungi Backend Server. Komunikasi tersebut tentunya menggunakan konsep API agar aplikasi go-food bisa mengirimkan instruksi kepada server untuk memesan makanan pada restoran yang terdaftar di database. Kemudian server tersebut akan memperbarui data dan menginformasikan ke aplikasi driver dan pemilik restoran.

Menarik bukan? Instruksi tersebut bisa dengan mudahnya di proses secara efisien.

Nah untuk jenisnya sendiri ada banyak tapi kita akan spesifik membahas tentang dua hal yakni REST, dan GraphQL.

# **REST API**

REST atau sering dikenal dengan **RE**presentational **S**tate **T**ransfer saat ini populer digunakan dikalangan startup. Biasanya untuk disebut REST API perlu memenuhi prinsip sebagai berikut :

- **Client-server** - Yang ini sangat jelas bahwa REST harus memiliki konsep aplikasi klien dan aplikasi server. Pembagian dua jenis aplikasi tersebut memungkinkan kita untuk skalabilitas yang mudah dan mendukung untuk kolaborasi dengan platform yang berbeda. Sebagai contoh kolaborasi aplikasi android dengan backend berbasis PHP.
- **Stateless** - Pada konsep stateless setiap permintaan harus memiliki informasi yang bisa dipahami untuk melakukan permintaan.

Contoh: SSH merupakan stateful application karena untuk bisa mengirim instruksi shell kita harus login dan selama koneksi kita terjadi kita masih memiliki session yang valid. Sedangkan jika koneksi kita terputus otomatis session kita timeout dan harus login SSH kembali. Berbeda dengan konsep stateless dimana session disimpan pada setiap permintaan misal terdapat di HTTP header. Sehingga ketika permintaan selesai dan koneksi terputus selama session ID kita masih valid maka kita masih bisa melakukan permintaan.

- **Cacheable** Jika respon dapat di-cache (disimpan sementara) maka REST akan merespon permintaan sama berulang-ulang dengan data yang disimpan sementara tanpa harus membebani backend.
- **Uniform interface** - Penggunaan URI untuk memisahkan dan mengidentifikasi resource pada server. Sebagai contoh untuk login maka URI nya http://contoh.com/**api/login** sedangkan untuk register adalah **/api/register**.
- **Layered system** Klien yang meminta tidak perlu tahu apakah itu berkomunikasi dengan server yang sebenarnya, proxy, atau perantara lainnya.

Sedangkan protokol yang digunakan untuk REST hanya mendukung HTTP atau HTTPS. Artinya sejauh ini tidak ada protokol yang yang bisa digunakan untuk menerapkan REST. Dan untuk format data yang digunakan untuk REST yakni JSON.

Jika teman-teman terbiasa menggunakan tipe data object pada programming, maka JSON hampir sama formatnya karena berbasis key dan value.

```bash
{
   "username":"admin",
   "password":"admin123"
}
```

Nah **username** pada json diatas disebut sebagai key, tentunya yang **password** juga sama. Sedangkan **admin** dan **admin123** bisa disimpulkan bahwa itu adalah value.

# **GraphQL**

Nah konsep GraphQL tergolong masih baru dalam konsep membangun API. GraphQL dibangun oleh Facebook dan implementasinya di sisi server. Masih ada kesamaan bahwa konsep ini membutuhkan klien dan server juga. Selain itu penggunaan GraphQL merupakan antarmuka dalam akses ke Database dan tidak terbatas DBMS yang digunakan apa.

Hal ini dikarenakan GraphQL mendukung DBMS SQL maupun NoSQL. Selain itu dukungan seperti konsep middleware dengan sebutan resolver.

[https://lh4.googleusercontent.com/seejMHU3lJHwloaUruCRrrEN9JnsrPk9RcSxHtBTHfj8yMkI-rmb0xhwYPA-kVMWdGbhwEe9lLLaD7jdUGkps2RptdIbF8Mvn_24p_3nzE8fBA9GWLgQ8CS5rD1wnyeDKdx3oUVl0xeQYcfI22H1WESeLC8](https://lh4.googleusercontent.com/seejMHU3lJHwloaUruCRrrEN9JnsrPk9RcSxHtBTHfj8yMkI-rmb0xhwYPA-kVMWdGbhwEe9lLLaD7jdUGkps2RptdIbF8Mvn_24p_3nzE8fBA9GWLgQ8CS5rD1wnyeDKdx3oUVl0xeQYcfI22H1WESeLC8)

Selain itu GraphQL memiliki 2 jenis operasi yang sering disebut query. Contoh yang bisa divisualisasikan adalah gambar diatas.

- **Query** merupakan tipe operasi untuk mengakses informasi pada database.
- **SiteInformation** merupakan nama operasi yang sudah didefinisikan di server.
- Dan untuk warna biru merupakan **Fields** berisi data apa saja yang ingin diakses.

Sedangkan tipe operasi kedua adalah mutation. Operasi ini bisa digunakan untuk mutasi data seperti create, update, delete di database.

[https://lh5.googleusercontent.com/gZPXVUzC6evDv9v1SzoA5Y4CDzaXMPMqfKnLMy3LkB3B4UcUTEIeuvOR8GxCN1pUyuSNzQOpk84Aj9icm2rImZ5MdtKlj16qeu4PCO-_EEa517aMXkg9ueNN828evgLjrByHS1CZUpRc3b366UkurPsd--Q](https://lh5.googleusercontent.com/gZPXVUzC6evDv9v1SzoA5Y4CDzaXMPMqfKnLMy3LkB3B4UcUTEIeuvOR8GxCN1pUyuSNzQOpk84Aj9icm2rImZ5MdtKlj16qeu4PCO-_EEa517aMXkg9ueNN828evgLjrByHS1CZUpRc3b366UkurPsd--Q)

Nah seperti yang kalian perhatikan pada gambar diatas CreateBook memiliki parameter sebagai berikut :

1. title
2. authorID
3. publicationDate
4. genre

Value dari key diatas merupakan data yang akan disimpan ke dalam database. Sedangkan untuk informasi yang didapatkan didefinisikan pada bagian berikut :

```bash
{
  id
  title
}
```

Sudah jelas bukan untuk jenis dan pembagian GraphQL request diatas ?