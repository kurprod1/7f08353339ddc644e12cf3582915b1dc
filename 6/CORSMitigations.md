# CORS Mitigations

Created: June 22, 2022 1:17 PM

Kerentanan CORS muncul salah satunya karena misconfiguration. Oleh karena itu, pencegahan Bagian berikut menjelaskan beberapa pertahanan yang efektif terhadap serangan CORS. Ada beberapa cara untuk mencegah adanya exploit CORS diantaranya adalah :

# Konfigurasi yang tepat dari Cross-Origin request

Jika resource web berisi informasi sensitif, origin harus ditentukan dengan benar di header Access-Control-Allow-Origin.

# Hanya izinkan situs tepercaya

Ini mungkin tampak jelas tetapi asal yang ditentukan di header **Access-Control-Allow-Origin** seharusnya hanya situs yang tepercaya. Secara khusus, secara dinamis mencerminkan origin dari permintaan lintas asal tanpa validasi mudah dieksploitasi dan harus dihindari.

# Hindari whitelist null

Hindari menggunakan header **Access-Control-Allow-Origin: null**. Header CORS harus didefinisikan dengan benar sehubungan dengan asal tepercaya untuk server pribadi dan publik.

# Hindari wildcard di jaringan internal

Hindari menggunakan wildcard di jaringan internal. Mempercayai konfigurasi jaringan saja untuk melindungi sumber daya internal tidak cukup ketika browser internal dapat mengakses domain eksternal yang tidak tepercaya.