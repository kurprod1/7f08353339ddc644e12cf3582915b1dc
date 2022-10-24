# Footprinting & Fingerprinting

# **Footprinting**

Footprinting adalah segala kegiatan mengumpulkan informasi target yang akan diekploitasi sistemnya sebelum melakukan penguasaan sistem sesungguhnya atau Footprinting juga dapat disebut sebagai seni mencari/mengumpulkan informasi yang berkaitan dengan target yang akan diserang.

Footprinting dapat dibagi 2 yaitu :

- Inner footprinting.
    
    Inner footprinting adalah pencarian informasi terhadap suatu target dimana Anda sudah berada di dalam jaringan komputer tersebut (Anda sudah berada di dalam gedungnya dan menggunakan fasilitas internet gratis).
    
    Tools yang dapat digunakan untuk melakukan inner footprinting antara lain[*] :
    
    - Nmap / Zenmap
    - AngryIP Scanner
    - MyLAN View (Windows Only)
- Outer footprinting.
    
    Outer Footprinting adalah pencarian informasi terhadap suatu situs dimana Anda tidak berada di dalam jaringan komputer target (Anda berada jauh dari komputer target).
    
    Tools yang dapat digunakan untuk melakukan inner footprinting antara lain :
    
    - Nmap
    - dig
    - whois
    - nslookup

## Other References

- [Understanding the Steps of Footprinting: A Guide for Penetration Testers](https://eccouncil.org/cybersecurity-exchange/penetration-testing/footprinting-steps-penetration-testing/)

# **Fingerprinting**

Sidik jari di dunia digital mirip dengan sidik jari manusia di dunia nyata. Sederhananya, sidik jari adalah sekelompok informasi yang dapat digunakan untuk mendeteksi perangkat lunak, protokol jaringan, sistem operasi atau perangkat perangkat keras.

Sidik jari adalah seni menggunakan informasi itu untuk menghubungkan set data untuk mengidentifikasi — dengan probabilitas tinggi — layanan jaringan, nomor dan versi sistem operasi, aplikasi perangkat lunak, basis data, konfigurasi, dan banyak lagi.

Sebagian besar teknik sidik jari digital didasarkan pada pendeteksian pola dan perbedaan tertentu dalam paket jaringan yang dihasilkan oleh sistem operasi.

Teknik sidik jari sering menganalisis berbagai jenis paket dan informasi seperti ukuran Jendela TCP, Opsi TCP dalam paket TCP SYN dan SYN + ACK, permintaan ICMP, paket HTTP, permintaan DHCP, nilai IP TTL serta nilai ID IP, dll.

1. **Active Fingerprinting**
    
    Active Fingerprinting adalah jenis sidik jari paling populer yang digunakan. Ini terdiri dari mengirim paket ke korban dan menunggu balasan korban untuk menganalisis hasilnya.
    
    Ini seringkali merupakan cara termudah untuk mendeteksi OS, jaringan, dan layanan jarak jauh. Ini juga yang paling berisiko karena dapat dengan mudah dideteksi oleh sistem deteksi intrusi (IDS) dan firewall packet filtering.
    
    Platform populer yang digunakan untuk meluncurkan tes sidik jari aktif adalah Nmap[*]. Alat praktis ini dapat membantu Anda mendeteksi sistem operasi spesifik dan aplikasi layanan jaringan ketika Anda meluncurkan paket TCP, UDP atau ICMP terhadap target yang diberikan.
    
    Dengan menggunakan aturan skrip internal, Nmap menganalisis hasil dari balasan korban, lalu mencetak hasilnya — yang 99% akurat dari waktu.
    
2. **Passive Fingerprinting**
    
    Passive Fingerprinting adalah pendekatan alternatif untuk menghindari deteksi saat melakukan kegiatan pengintaian Anda.
    
    Perbedaan utama antara sidik jari aktif dan pasif adalah bahwa sidik jari pasif tidak secara aktif mengirim paket ke sistem target. Sebaliknya, ia bertindak sebagai pemindai jaringan dalam bentuk sniffer, hanya menonton data lalu lintas di jaringan tanpa melakukan perubahan jaringan.
    
    Setelah penyerang mengendus informasi yang cukup, dapat dianalisis untuk mengekstrak pola yang akan berguna untuk mendeteksi sistem operasi dan aplikasi.
    
    Meskipun jenis teknik ini dapat mem-bypass teknik deteksi intrusi jaringan yang umum, teknik ini tidak dijamin untuk menyembunyikan keberadaan jaringan Anda saat mengendus lalu lintas.
    
    Tool popular dalam kategori ini adalah **p0f**, p0f sendiri adalah alternatif yang bagus untuk Nmap, alat sidik jari pasif yang digunakan untuk menganalisis lalu lintas jaringan dan mengidentifikasi pola di balik komunikasi berbasis TCP/IP yang sering diblokir untuk teknik sidik jari aktif Nmap.
    
    Ini mencakup fitur-fitur sidik jari tingkat jaringan yang kuat, serta fitur yang menganalisis muatan tingkat aplikasi seperti HTTP. Ini juga berguna untuk mendeteksi pengaturan NAT, Proxy, dan load balancer.