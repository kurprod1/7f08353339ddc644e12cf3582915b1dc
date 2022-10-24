# FTP Fuzzing

Created: June 22, 2022 1:17 PM

Untuk materi FTP server kita akan menggunakan tool BED. BED adalah singkatan dari Brute-force Exploit Detector. Ini dirancang untuk memeriksa potensi adanya buffer overflows, format string et. Al.

```bash
$ bed
BED 0.5 by mjm ( www.codito.de ) & eric ( www.snake-basket.de )

 Usage:

 bed -s <plugin> -t <target> -p <port> -o <timeout> [ depends on the plugin ]

 <plugin>   = FTP/SMTP/POP/HTTP/IRC/IMAP/PJL/LPD/FINGER/SOCKS4/SOCKS5
 <target>   = Host to check (default: localhost)
 <port> 	= Port to connect to (default: standard port)
 <timeout>  = seconds to wait after each test (default: 2 seconds)
 use "bed -s <plugin>" to obtain the parameters you need for the plugin.

 Only -s is a mandatory switch.
```

Untuk menggunakannya cukup mudah kita hanya perlu menjalankan sesuai perintah berikut:

```bash
$ bed -s FTP -t 127.0.0.1 -p 31336 -u anonymous -v anonymous
+ Buffer overflow testing:
            	testing: 1  	USER XAXAX  	...........
            	testing: 2  	USER anonymousPASS XAXAX    	...........
 + Formatstring testing:
            	testing: 1  	USER XAXAX  	.......
            	testing: 2  	USER anonymousPASS XAXAX    	.......
* Normal tests
 + Buffer overflow testing:
            	testing: 1  	ACCT XAXAX  	...........
            	testing: 2  	APPE XAXAX  	...........
            	testing: 3  	ALLO XAXAX  	...........
            	testing: 4  	CWD XAXAX   	...........
            	testing: 5  	CEL XAXAX   	...........
            	testing: 6  	DELE XAXAX  	...........
            	testing: 7  	HELP XAXAX  	...........
            	testing: 8  	MDTM XAXAX  	...........
            	testing: 9  	MLST XAXAX  	...........
```