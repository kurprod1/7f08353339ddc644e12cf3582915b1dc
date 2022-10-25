# DOM-Based Vulnerabilities

Ada yang menyebut type-0 XSS. Adalah kerentanan yang berfokus pada hirarki aplikasi atau DOM (Document Object Model) dengan cara memodifikasi content pada DOM website pada server-side sehingga akan berakibat pada perilaku pada client-side.

Meskipun memiliki nama type-0 XSS, ini berbeda dengan XSS biasa yang menyimpan payload pada field input.

Coba lihat contoh dibawah. Ada script untuk membuat form untuk memilih bahasa.

```jsx
…
Select your language:

<select>
	<script>
		document.write("<OPTION value=1>"+decodeURIComponent(document.location.href.substring(document.location.href.indexOf("default=")+8))+"</OPTION>");

		document.write("<OPTION value=2>English</OPTION>");
	</script>
</select>
…
```

Dan url request yang dirender dari code diatas adalah

```bash
http://www.some.site/page.html?default=French
```

Kerentanan DOM-based XSS dapat kita lakukan dengan memodifikasi DOM melalui query string yang ada menjadi seperti ini.

```bash
http://www.some.site/page.html?default=<script>alert(document.cookie)</script>
```

Dengan begitu, malah menampilkan cookie bukan bahasa.