# Clickjacking Mitigations

Created: June 22, 2022 1:17 PM

Clickjacking adalah kerentanan dari sisi client dan keberhasilannya atau sebaliknya tergantung pada fungsionalitas browser dan kesesuaian dengan standar web yang berlaku dan best practice terbaik. 

Perlindungan sisi server terhadap clickjacking disediakan dengan mendefinisikan dan mengkomunikasikan batasan atas penggunaan komponen seperti **iframe**. Namun, penerapan perlindungan bergantung pada kepatuhan browser dan penegakan batasan ini. Dua mekanisme untuk perlindungan clickjacking sisi server adalah **X-Frame-Options** dan **Content Security Policy**.

# ****X-Frame-Options****

X-Frame-Options awalnya diperkenalkan sebagai header respons tidak resmi di Internet Explorer 8 dan dengan cepat diadopsi di browser lain. Header memberi pemilik situs web kontrol atas penggunaan **iframe** atau objek sehingga injection pada halaman web dalam frame dapat dilarang dengan direktif penolakan:

```
X-Frame-Options: deny
```

Atau dapat juga mendefinisikan bahwa yang dapat di masukan kedalam web berasal dari domain asal.

```
X-Frame-Options: sameorigin
```

Atau mengizinkan dari website terpercaya

```
X-Frame-Options: allow-from https://normal-website.com
```

# Content Security Policy

Content Security Policy (CSP) adalah mekanisme deteksi dan pencegahan pada kerentanan XSS dan clickjacking. CSP biasanya diimplementasikan di web server sebagai reutn header:

```
Content-Security-Policy: policy
```

Policy yang direkomendasi untuk pencegahan clickjacking adalah `frame-ancestors` . 

`frame-ancestors 'none'` juga memiliki sifat yang sama dengan X-Frame-Options `deny` . `frame-ancestors 'self'` ekivalen dengan X-Frame-Options `sameorigin` directive. Contohnya seperti ini:

```
Content-Security-Policy: frame-ancestors 'self';
```

dan ini:

```
Content-Security-Policy: frame-ancestors normal-website.com;
```