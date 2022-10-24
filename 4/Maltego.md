# Maltego


Maltego adalah perangkat lunak aplikasi yang digunakan untuk intelijen open-source dan forensik dan dikembangkan oleh Paterva . Ini berfokus pada penyediaan perpustakaan transformasi untuk penemuan data dari sumber terbuka dan memvisualisasikan informasi itu dalam format grafik yang cocok untuk analisis tautan dan penggalian data.

Bayangkan semua informasi yang dapat diperoleh dari server pencarian whois, atau informasi yang dapat diperoleh oleh alat pencarian DNS dari server DNS publik, atau bahkan email dan nama host yang dapat diperoleh dari TheHarvester (menggunakan Google dan Bing). Maltego melakukan semua itu ditambah lebih banyak lagi, menggunakan sumber terbuka yang sama dengan bantuan transformasi, kemudian mewakili semuanya dalam satu aplikasi dan dengan cara grafis yang mudah divisualisasikan.

Paterva menyediakan dua lisensi yang dapat digunakan, versi komersial dan versi gratis. Kita akan fokus pada versi gratis, atau disebut sebagai "Edisi Komunitas." Versi ini sudah diinstal sebelumnya dalam Kali Linux, Jika kalian menggunakan sistem operasi lainnya silahkan kunjungi website resmi [Paterva](https://www.paterva.com/buy/maltego-clients/maltego-ce.php) untuk mengunduh versi terbaru dari Maltego.

Untuk meluncurkan Maltego di terminal Kali Linux, ketik ***maltego*** dan tekan "enter" seperti yang ditunjukkan di bawah ini:

![https://lh3.googleusercontent.com/sq8SKVkd_MoJEMi5Sft0baqvRz0x3wSORrJM6nymUHmbdDep2qe8p6W6jIf_QRlgHGa5sekYJ5FnKPKYy4zieHwHxz92RFcKmjkXsjxh4WxxkkgD1AnlUEE96_ePfMn3lZEEG_s2aFwuwc0oiw](https://lh3.googleusercontent.com/sq8SKVkd_MoJEMi5Sft0baqvRz0x3wSORrJM6nymUHmbdDep2qe8p6W6jIf_QRlgHGa5sekYJ5FnKPKYy4zieHwHxz92RFcKmjkXsjxh4WxxkkgD1AnlUEE96_ePfMn3lZEEG_s2aFwuwc0oiw)

Silahkan pilih Maltego CE (Versi Komunitas), kita akan diminta login terlebih dahulu, jika kita belum memiliki akun silahkan pilih register terlebih dahulu. Setelah berhasil login kita bisa lanjutkan ke proses berikutnya, yaitu install transformasi , transformasi akan diperbarui dan kita akan mendapatkan hasil yang mirip dengan yang di bawah ini:

![https://lh5.googleusercontent.com/Lxw33DeJYepQ0o_p16zge9IchSjrvEcNoswaqIOij_8ps-dTRv9bArLZn0MSW4vapizQbrg8YU7ixMpD_UVKfhSxpti9kbKn271HqvXbnRAzjIoEhBbJGzcqAiKSB8WZiuaX934GF_zo9CqhkypFJLUAVNg](https://lh5.googleusercontent.com/Lxw33DeJYepQ0o_p16zge9IchSjrvEcNoswaqIOij_8ps-dTRv9bArLZn0MSW4vapizQbrg8YU7ixMpD_UVKfhSxpti9kbKn271HqvXbnRAzjIoEhBbJGzcqAiKSB8WZiuaX934GF_zo9CqhkypFJLUAVNg)

Tekan "Next" dan kita akan memiliki layar yang meminta kita untuk membantu Maltego dengan mengirimkan laporan kesalahan. Tekan "Next" lagi dan pilih mode privasi kita. Kita akan memilih "Normal" untuk memiliki pengalaman Maltego terkaya. Lihat tangkapan layar di bawah ini:

![https://lh5.googleusercontent.com/0V_nq14Hf50TkJ0SkpJB_1WjQg9RymlrvQvNs61yi7H9CrKYsV8xZtpgHoif2GmIZ-iwRzUnzXQRyoNTPFAbyVt3jSH879SvgSdxja31Srgn0N8gN6fxKEzV7OMJewoGg1vPnfaf-nMnu-5XkUNnr2MDSHQ](https://lh5.googleusercontent.com/0V_nq14Hf50TkJ0SkpJB_1WjQg9RymlrvQvNs61yi7H9CrKYsV8xZtpgHoif2GmIZ-iwRzUnzXQRyoNTPFAbyVt3jSH879SvgSdxja31Srgn0N8gN6fxKEzV7OMJewoGg1vPnfaf-nMnu-5XkUNnr2MDSHQ)

kita kemudian akan disajikan dengan layar di bawah ini. kita dapat memilih untuk membuka grafik kosong, membuka contoh grafik atau mengabaikan keduanya dan melanjutkan.

![https://lh4.googleusercontent.com/yngGCTemtvkOWo8v9IY43ub9g3K5hElJlVS3WmOhdRyhU9GoIpcoz4t-ZrsY4k-TMi9BKLh73sITRIiBzlULp9JtJYZCq82u81VjfS4w8WrRrsleNVfA41tkWA4gf0iUC9jaIAoiJc8SAKJzegfMxJSjyG0](https://lh4.googleusercontent.com/yngGCTemtvkOWo8v9IY43ub9g3K5hElJlVS3WmOhdRyhU9GoIpcoz4t-ZrsY4k-TMi9BKLh73sITRIiBzlULp9JtJYZCq82u81VjfS4w8WrRrsleNVfA41tkWA4gf0iUC9jaIAoiJc8SAKJzegfMxJSjyG0)

hingga tampil layar kerja seperti berikut :

![https://lh5.googleusercontent.com/hQMCih-1t8X0RD7Uy8L6eTGTyuR7cMV0-DB7RT5iUV5woURb_0eNIt1LB_QO97YTp9sPaUw9KgCn5jrh8EkbXomS3D5Vw7m80oerJSy-JPgliAppYTIhWTKm2pIFVHC6wUjhr4bnANzuicZJFmqGxfiQ34k](https://lh5.googleusercontent.com/hQMCih-1t8X0RD7Uy8L6eTGTyuR7cMV0-DB7RT5iUV5woURb_0eNIt1LB_QO97YTp9sPaUw9KgCn5jrh8EkbXomS3D5Vw7m80oerJSy-JPgliAppYTIhWTKm2pIFVHC6wUjhr4bnANzuicZJFmqGxfiQ34k)

## **Mengenal Transformasi**

Transformasi adalah potongan kode yang mengambil informasi terkait untuk input yang diberikan. Input yang diambil kemudian diformat dan dikembalikan sebagai entitas ke Maltego.

Untuk menjalankan transformasi, kita hanya perlu menarik dan melepaskan (*drag and drop*) item dari palet di paling kiri ke tab Maltego yang baru diluncurkan. Item dapat berupa salah satu dari banyak sub kategori di sebelah kiri, mis. Infrastruktur, pribadi, lokasi, dan sebagainya.

Setelah item tersimpan di workspace, kita dapat dengan mudah mengubah nilai / nama dengan mengklik dua kali padanya dan mengetikkan nilai yang diinginkan - katakanlah, dengan mengubah domain ke domain target kita.

Di bawah bagian infrastructure, kita pilih Domain dan memberi feed di cilsy.id, menggantikan paterva.com. Lihat tangkapan layar di bawah ini:

![https://lh5.googleusercontent.com/LPHjhPC6uvEc-gyh4WUmXP2V22OgGmkHelCgTtAS5L5tNitW6eYTsvzfW26PDMjG8h67JDdcN5J_kOqjLDUMipVYFvSfecwcc-vU-g5POPJRPVU2a0jrHWNBeKcv_VPPtfjfTuIY5SFM_219ixg6yQh-mjY](https://lh5.googleusercontent.com/LPHjhPC6uvEc-gyh4WUmXP2V22OgGmkHelCgTtAS5L5tNitW6eYTsvzfW26PDMjG8h67JDdcN5J_kOqjLDUMipVYFvSfecwcc-vU-g5POPJRPVU2a0jrHWNBeKcv_VPPtfjfTuIY5SFM_219ixg6yQh-mjY)

Untuk menjalankan transformasi, cukup klik kanan di mana saja di dalam ruang kerja saat ini dan pilih transformasi pilihan kita. Maltego akan melakukan itu dan membalas dengan tampilan grafis pada temuan serta hubungannya. Pada contoh dibawah kita akan mengklik kanan pada domain kami dan memilih "semua transformasi." Ini ditunjukkan di bawah ini:

![https://lh3.googleusercontent.com/VQhK1mbG4lrj_K1lRxLWlzDaQrI-ZnafXBzjGEr109mOSMxzE_jnV_K0msUgDgl_jBZCXzhzVI-On2duZxGdt7OWTTz3IchOb7_KlyEQQ0YXAVbpdBnqTPayITJjRlQYichNjyzQ93V5HTVsNoUsEcOzLzk](https://lh3.googleusercontent.com/VQhK1mbG4lrj_K1lRxLWlzDaQrI-ZnafXBzjGEr109mOSMxzE_jnV_K0msUgDgl_jBZCXzhzVI-On2duZxGdt7OWTTz3IchOb7_KlyEQQ0YXAVbpdBnqTPayITJjRlQYichNjyzQ93V5HTVsNoUsEcOzLzk)

Untuk hasil pencarian lebih terstruktur tidak disarankan untuk langsung menggunakan mode all transform, silahkan gunakan pencarian satu per satu dimulai dari enumerasi DNS hingga terakhir hal lainnya menggunakan transform expander , silahkan klik tanda **(+)** pada tab transform saat kita klik kanan pada item domain hingga muncul tampilan seperti dibawah ini :

![https://lh5.googleusercontent.com/NwnlYLBn0Y8uoHgZgZj9P0RvP678G2bTkoY3vU5eyxf8VEsa1ZV0F791x1Pdcz8tMA49NCSUTwcdkgmbYysNBSskXTmTNhBLNWmeHLHIMaA0eyPM_VoICDlYu4xFzkPNNHip38MQYrGCyyULcR_O9g8Xmsk](https://lh5.googleusercontent.com/NwnlYLBn0Y8uoHgZgZj9P0RvP678G2bTkoY3vU5eyxf8VEsa1ZV0F791x1Pdcz8tMA49NCSUTwcdkgmbYysNBSskXTmTNhBLNWmeHLHIMaA0eyPM_VoICDlYu4xFzkPNNHip38MQYrGCyyULcR_O9g8Xmsk)

Beberapa target yang berupa domain yang dimiliki perusahaan besar terkadang memiliki sistem yang kompleks , untuk itu disarankan untuk menggunakan all transform mode, selain akan memakan waktu yang lama, hal tersebut juga membuat Kita kesulitan untuk menentukan informasi apa saja yang benar-benar dibutuhkan.

## Documentation

- [Maltego](https://docs.maltego.com/support/home)