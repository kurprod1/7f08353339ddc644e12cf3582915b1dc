# theHarvester


TheHarvester merupakan salah satu alat bantu untuk melakukan pasif information gathering yang umum digunakan dan cukup baik dalam hal pengenalan target.

Untuk detail penggunaan command pada theHarvester kita dapat menjalankan perinitah :

```bash
# theHarvester -h
```

![https://lh3.googleusercontent.com/vZ0ttbIEUherFAM_2bGUTtXSndcnm41Qc0l6njlVOCJJ8nZiiCTwSTTV4LvyadbIAYEWhcLDxaaqPEigUZoWKJPepCIYgLdy6azOa26_nzScGi66_Eq99z5d9cgPgEj_9pZRpLEMpGofe0qMJZwxT517j8I](https://lh3.googleusercontent.com/vZ0ttbIEUherFAM_2bGUTtXSndcnm41Qc0l6njlVOCJJ8nZiiCTwSTTV4LvyadbIAYEWhcLDxaaqPEigUZoWKJPepCIYgLdy6azOa26_nzScGi66_Eq99z5d9cgPgEj_9pZRpLEMpGofe0qMJZwxT517j8I)

Sedangkan untuk menggunakan theHarvester sebagaimana umumnya , kita dapat menggunakan perintah :

```bash
# theHarvester -d <DOMAIN> -l <LIMIT> -b <SOURCE> -f <FILE_OUPUT>
```

Contoh:

![](https://lh3.googleusercontent.com/750lOVG3LuMudrvxJZKXYu6Q5Z6snDkCsNAE6pKF1aPpJmkM_-hMLy1VQSU1xx4ECUnM0e9wTpxObZXz6n-RMpqqI5iWHMmFEC-pUKQY2hGeZ34XTHfPkfH5OhcT_NrR4_EW-PGGsLFTsweAX6wXmUE6BW8)


Contoh diatas hanya menggunakan satu sumber yaitu Google , theHarvester akan melakukan kueri ke mesin pencari google lalu mencatat temuannya kemudian diproses untuk mengambil hanya informasi yang terkait target saja yang ditampilkan dengan maksimal kueri sebanyak 500 halaman pencarian lalu menyimpan hasil query pada file ***nokia.html*** dan ***nokia.xml***.

theHarvester mampu melakukan pencarian ke lebih dari satu sumber, kita dapat menentukan sumber tersebut dengan memisahkan sumber menggunakan koma **(,)** pada parameter theHarvester, sebagai contoh kita akan menambahkan sumber bing pada target yang sama dengan perintah :

```bash
# theHarvester -d <DOMAIN> -l <LIMIT> -b <SOURCE1, SOURCE2> -f <FILE_OUPUT>
```

![https://lh5.googleusercontent.com/D-aNycxKfdEozPftJuXzjPRs2aGLPn5WafJ5tuWbpelmw9mtgegvIq80r5MP-Hk56tQF060cxhYH4hb0pDrz-0EyN9856-rU4tpoo74Gtza7xPn82NM7l_xrfJru5rr6dYE9bW3xqV7Tr0ajm0Fi93bRatQ](https://lh5.googleusercontent.com/D-aNycxKfdEozPftJuXzjPRs2aGLPn5WafJ5tuWbpelmw9mtgegvIq80r5MP-Hk56tQF060cxhYH4hb0pDrz-0EyN9856-rU4tpoo74Gtza7xPn82NM7l_xrfJru5rr6dYE9bW3xqV7Tr0ajm0Fi93bRatQ)


Contohnya, kita akan mencoba mencoba melakukan scanning ke website sekolahhacker.com. Perintah yang kita gunakan adalah  theHarvester -d sekolahhacker.com -l 500 -b google,bing -f sekolahhacker

![https://lh6.googleusercontent.com/uDJiSMUmrjMyQt6mAxhZhlulU7nkrFNylkGVkyokMEIBY5hPQRjlQ-CFdy27g3uusXToPWwCCxBJNKrOahrx5XnqA3kKWWEhtSVH-UTg-z-xQ4IaAy-mGSIUFHGj_CBi_68wJ894h1wRYKyG-w](https://lh6.googleusercontent.com/uDJiSMUmrjMyQt6mAxhZhlulU7nkrFNylkGVkyokMEIBY5hPQRjlQ-CFdy27g3uusXToPWwCCxBJNKrOahrx5XnqA3kKWWEhtSVH-UTg-z-xQ4IaAy-mGSIUFHGj_CBi_68wJ894h1wRYKyG-w)

catatan :

theHarvester merupakan salah satu tools yang sudah terdapat secara default di Distro Kali Linux , untuk sistem operasi lain silahkan install theHarvester langsung dari sumbernya yaitu [https://github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)

Untuk penginstalan pada umumnya dapat menggunakan susunan perintah berikut  :

```bash
# git clone https://github.com/laramies/theHarvester
# cd theHarvester
# vi api-keys.yml
# python3.7 -m pip install -r requirements.txt
# python3.7 theHarvester.py -h
```

Pastikan kalian sudah memiliki API Keys dari masing-masing service tambahan yang ingin digunakan seperti shodan dan lain sebagainya.

## Documentation

- [https://github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)

## Other References

- [Python theHarvester - How to use it? - GeeksforGeeks](https://www.geeksforgeeks.org/python-theharvester-how-to-use-it/)

- [Passive Reconnaissance - Email Harvesting With theHarvester](https://www.youtube.com/watch?v=VytCL2ujjcA&ab_channel=HackerSploit)