# Kenapa Perlu Automation ?

Created: June 22, 2022 1:17 PM

Materi selanjutnya kita akan belajar mendokumentasikan dan menguji API dengan aplikasi Postman. Tentunya kita akan mempraktekkan bagaimana menggunakan Postman untuk membuat automation security testing.

Perlu teman-teman ketahui pemahaman dan penggunaan seputar automation diperlukan untuk mengurangi effort kita dalam mengerjakan proyek security testing. Tentunya bertujuan untuk memudahkan kalian agar ketika diminta untuk reproduce atau memvalidasi apakah bug masih ada atau tidak bisa dilakukan hanya dengan satu tombol.

Realitanya di dalam internal perusahaan terkadang temuan celah keamanan kalian tidak bisa langsung di perbaiki. Hal ini disebabkan kultur perusahaan yang berkolaborasi antar departemen yang berbeda. Sehingga bukan berarti temuan kalian itu diabaikan hanya karena belum diperbaiki, tetapi bisa jadi semua software engineer diprioritaskan untuk mengerjakan fitur yang sangat penting dalam kelangsungan hidup perusahaan.

Bisa dikatakan bahwa tim yang terbatas dengan antrian pekerjaan yang begitu banyak tidak akan bisa diselesaikan. Sehingga jalan yang paling mudah adalah mengerjakan pekerjaan berdasarkan level prioritas.

Security bug bisa diprioritaskan dari rendah hingga kritis, namun belum tentu di sudut pandang departemen lain tingkat kritis pada security merupakan prioritas yang diutamakan. Bisa jadi ada peningkatan fitur yang harus diselesaikan bulan ini sehingga prioritas fitur diutamakan ? Mungkin kalian bisa bertanya-tanya kenapa. Dan bukankah security itu penting ?

[https://lh6.googleusercontent.com/wx4ThRcb-eC3rX12VOJYoIKPlnqWlovLDO5tzKkFD5Z0PstCBKbB6GQo3doZI_Dq_pbEgBR2gdTQDUPvQ96LH5GMHxudO44e4hgezEKRXnIenPPkrXo-MmJm96JsMokWM3squaohl__7WMdV8PeiBdnLoTM](https://lh6.googleusercontent.com/wx4ThRcb-eC3rX12VOJYoIKPlnqWlovLDO5tzKkFD5Z0PstCBKbB6GQo3doZI_Dq_pbEgBR2gdTQDUPvQ96LH5GMHxudO44e4hgezEKRXnIenPPkrXo-MmJm96JsMokWM3squaohl__7WMdV8PeiBdnLoTM)

Hal tersebut relatif jika kita melihat kondisi dan tujuan kuartal perusahaan. Bisa jadi perusahaan mengejar fitur agar bisa didemonstrasikan di depan investor ? Bisa jadi fitur tersebut jadi penentu untuk mendapatkan pendanaan kelangsungan hidup perusahaan selanjutnya ? Jadi menurut kalian lebih kritis yang mana ?

Nah karena di perusahaan rintisan hal tersebut harus dianggap sebagai hal yang lumrah. Sehingga masalah penundaan perbaikan harus juga kita maklumi. Tanpa adanya automation bisa jadi kita sudah lupa bagaimana proses untuk memicu kerentanan yang sudah kita temukan berbulan-bulan yang lalu bukan ? Artinya jika kita punya automation security testing, kita hanya cukup menekan satu tombol untuk memastikan celah tersebut masih ada atau tidak.

Kesimpulannya terkadang banyak hal yang menyangkut bisnis tidak dipahami oleh kita. Namun kita harus percaya yang kita tahu mungkin hanya sebagian kecil dari seluruh informasi yang ada. Sehingga informasi kecil yang kita miliki tentunya akan membangun sudut pandang kita seolah security diabaikan. Jadi jangan berkecil hati, stay positive akan selalu ada cara untuk berkolaborasi secara intens dengan departemen lain di Perusahaan Startup !