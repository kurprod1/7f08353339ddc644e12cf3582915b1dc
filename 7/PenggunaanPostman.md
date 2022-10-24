# Penggunaan Postman

Created: June 22, 2022 1:17 PM

Aplikasi ini mendukung untuk pengujian API berbasis konsep REST maupun GraphQL. Selain itu Postman test scripts juga memungkinkan API berfungsi seperti yang diharapkan, untuk memastikan bahwa integrasi antar layanan berfungsi dengan andal, dan untuk memverifikasi bahwa perkembangan baru belum merusak fungsi apa pun yang ada. Istilah kerennya untuk pengujian ini biasa disebut functional tests.

Hanya saja kebutuhan kita berbeda seperti QA dalam memastikan jaminan kualitas produk yang dibuat software engineer. Kita memerlukan Postman untuk mengidentifikasi kerentanan yang sudah kita temukan sebelumnya. Istilah ini kurang tepat jika kita sebut dengan functional test. Akan lebih tepat jika aktivitas ini disebut dengan **Risk-Based and Functional Security Testing.**

# **Workspace**

Kita bisa mudah memisahkan jenis proyek misal bug bounty, freelance penetration testing, internal office, dan lain sebagainya berdasarkan workspace. Selain itu terdapat tipe workspace yang dibagi menjadi personal dan team. Penggunaan personal cocok apabila kita menggunakannya untuk kebutuhan pribadi tanpa perlu membagikan proyek kita dengan orang lain. Dan penggunaan workspace team bisa kita gunakan apabila kita ingin berkolaborasi lebih dari satu orang.

[https://lh3.googleusercontent.com/rLCRas62lXRGdLp9-su5slCFbq7Z85e-A8vQjl_9VdOinyfhoBMQdRU-VfLLU4O5CAVflyd_dOZN8yu7Rco5HQ6GY24004ItHr4d6ua04q9sm7h4d8Blu72WhNjXTExsXmp_vhygy47vpIyfPOczb5_gXpg](https://lh3.googleusercontent.com/rLCRas62lXRGdLp9-su5slCFbq7Z85e-A8vQjl_9VdOinyfhoBMQdRU-VfLLU4O5CAVflyd_dOZN8yu7Rco5HQ6GY24004ItHr4d6ua04q9sm7h4d8Blu72WhNjXTExsXmp_vhygy47vpIyfPOczb5_gXpg)

Selanjutnya kita perlu membuat workspace team untuk berkolaborasi antar siswa SekolahHacker. Instruktur perlu membuat workspace team dengan nama misalnya **SekolahHacker2**.

[https://lh6.googleusercontent.com/Gbs29TdHsES3csW3hsgRsLnxu6khRZAVAvE63M64KTy28J3_uq-XKoB_Am_Z4jGMp0k5noK12Dgr7dRpeKDCYhi94R6_605tA7lHTAe4CSthtI9iZtejwdsdSXgmmd_4dPvlFy9x8ZsjRshGb6GIcsDMeXA](https://lh6.googleusercontent.com/Gbs29TdHsES3csW3hsgRsLnxu6khRZAVAvE63M64KTy28J3_uq-XKoB_Am_Z4jGMp0k5noK12Dgr7dRpeKDCYhi94R6_605tA7lHTAe4CSthtI9iZtejwdsdSXgmmd_4dPvlFy9x8ZsjRshGb6GIcsDMeXA)

Di Bagian area invite people kita bisa menambahkan member dengan menginputkan email.

[https://lh5.googleusercontent.com/R4VlmmSr8BA4XNPSq00QIvER4nCHj_LHEXl6YE1LqIzVF8FveGosAHkELFPQa1WIZBz92Q3zt7oCVi7fwVFV49_XUozfgTV9Mr2wujZBHsrXZUnPF_isadr_9OoFN1AJYjmpWDon_b5Twj5mHbewucyc8Vw](https://lh5.googleusercontent.com/R4VlmmSr8BA4XNPSq00QIvER4nCHj_LHEXl6YE1LqIzVF8FveGosAHkELFPQa1WIZBz92Q3zt7oCVi7fwVFV49_XUozfgTV9Mr2wujZBHsrXZUnPF_isadr_9OoFN1AJYjmpWDon_b5Twj5mHbewucyc8Vw)

Jika dirasa sudah menambahkan semua anggota team, langkah terakhir cukup menekan tombol **Create Workspace** dan otomatis beralih ke workspace team. Member yang tadi sudah kita invite diharuskan meng klik link konfirmasi agar bisa mengakses juga.

# **Collection**

Kita bisa menggunakan fitur ini untuk mengelompokkan permintaan HTTP dan tentunya menjadi lebih rapi untuk mengelompokkan proyek kita. Membuat collection tidaklah sulit kita cukup menekan tombol **New Collection** pada panel kiri Postman.

[https://lh6.googleusercontent.com/ZrvgkicPOFsHAc4uDl21eHE9xgNtfM422wNwoZOKUYSTSHFJHmgeb-rTrEv5bnjdhfe-N3xHFY8hmGKm3eDBkfDx-fQc4LyxX7jHw7apXCRAuZo6zTes0qf5g1Cbos6Rx6X_pjaLQxRDkGAtMGclpTwAQjg](https://lh6.googleusercontent.com/ZrvgkicPOFsHAc4uDl21eHE9xgNtfM422wNwoZOKUYSTSHFJHmgeb-rTrEv5bnjdhfe-N3xHFY8hmGKm3eDBkfDx-fQc4LyxX7jHw7apXCRAuZo6zTes0qf5g1Cbos6Rx6X_pjaLQxRDkGAtMGclpTwAQjg)

Gambar: Klik tombol **New Collection**

[https://lh3.googleusercontent.com/LGIrHz-MhL6nDO4__CM2xaRJEC04f8_NsDoENh_w_DXrhKKIjgsC0nYOZauI_dfadl5W0IIrFpSisTe-2gj-Jg4v08WkwNxGghGYj_0bWQo3aXLfn-lLtQ6rfgdMalBIBIcD4ISe3qDQnMtWNIRjWHw8F74](https://lh3.googleusercontent.com/LGIrHz-MhL6nDO4__CM2xaRJEC04f8_NsDoENh_w_DXrhKKIjgsC0nYOZauI_dfadl5W0IIrFpSisTe-2gj-Jg4v08WkwNxGghGYj_0bWQo3aXLfn-lLtQ6rfgdMalBIBIcD4ISe3qDQnMtWNIRjWHw8F74)

Kita bisa memberikan nama collection sesuai dengan nama produk yang akan kita test. Contoh saja nama produknya adalah **authentication-service** dan teman-teman bisa menuliskan juga deskripsinya sehingga kalian tidak akan lupa tentang proyek collection ini.

[https://lh4.googleusercontent.com/Lkk9lT-aT5PjiuL3_OtCuSlDwnj4LQFPdm6bFpSUmAmVbO8-TGlSHtX_nJu-Ppqmu9mJiscSFYYH9HpyBOYxty8rkzrJImV-JQt7NVUZvnoG6buZ-zInOQUYbdTzaPqV9jfZuA7U_gLqLSXvHF-YCiq34iw](https://lh4.googleusercontent.com/Lkk9lT-aT5PjiuL3_OtCuSlDwnj4LQFPdm6bFpSUmAmVbO8-TGlSHtX_nJu-Ppqmu9mJiscSFYYH9HpyBOYxty8rkzrJImV-JQt7NVUZvnoG6buZ-zInOQUYbdTzaPqV9jfZuA7U_gLqLSXvHF-YCiq34iw)

Pada collection terdapat fitur untuk menambahkan tests script baik sebelum request dilakukan (pre-request scripts), tests script setelah request dilakukan (tests), dan variables dimana kita bisa mendefinisikan key value.

[https://lh4.googleusercontent.com/kLfgIpPJB8ndw1jtzNaQ6XVNan8NxeuMEYxgruWyOPKDUjBGJcyiDlYeOyFdVbQ7yu9ID-1y5X1Bsl-Qo3oIdI0SV6Ey-J91Ob_004U-FPyK6V_-rJpFBlBBVtw0n1A7395yu7PWzcruY7jUAmMwJLDqGUo](https://lh4.googleusercontent.com/kLfgIpPJB8ndw1jtzNaQ6XVNan8NxeuMEYxgruWyOPKDUjBGJcyiDlYeOyFdVbQ7yu9ID-1y5X1Bsl-Qo3oIdI0SV6Ey-J91Ob_004U-FPyK6V_-rJpFBlBBVtw0n1A7395yu7PWzcruY7jUAmMwJLDqGUo)

Apabila sudah dirasa cukup kalian hanya perlu menekan tombol **Create** untuk membuat collection.

[https://lh3.googleusercontent.com/Pbs-Rv-b1t2cO5QdQIUZ9HqUFIV7ICFS_g4xwT7gKjpo3MHqnMHMXE0RVMdLJf9GVCbH19cmut9Wt_ysMjnFe0W4fNytRnrryduQhIudpfJeVW9uY9bkZHZtLZSx0j8EokuZq-q0bIpDWRHcgfhEuQ7NXL4](https://lh3.googleusercontent.com/Pbs-Rv-b1t2cO5QdQIUZ9HqUFIV7ICFS_g4xwT7gKjpo3MHqnMHMXE0RVMdLJf9GVCbH19cmut9Wt_ysMjnFe0W4fNytRnrryduQhIudpfJeVW9uY9bkZHZtLZSx0j8EokuZq-q0bIpDWRHcgfhEuQ7NXL4)

# **Folder**

Folder membantu kita untuk mengelompokkan APIs berdasarkan resource sebagai contoh pada API ini memiliki resource users. Untuk membuat folder cukup klik icon **...** pada collection **authentication-service**.

[https://lh3.googleusercontent.com/G1VANA7OZNdAL5xV4g_t_Fmf-ptKvRPHgHOB7TNwUL7d9HDUdpg_k8NuAwL7NORUrCu6tPvbbSX6kRQGCGY_lgvd4gNQAhJNoQACX_-i9cd7yUvjzbPWQlS8BG1hm_EyFZ1Dq4g-q9kSz9y7TtSHdAj_veU](https://lh3.googleusercontent.com/G1VANA7OZNdAL5xV4g_t_Fmf-ptKvRPHgHOB7TNwUL7d9HDUdpg_k8NuAwL7NORUrCu6tPvbbSX6kRQGCGY_lgvd4gNQAhJNoQACX_-i9cd7yUvjzbPWQlS8BG1hm_EyFZ1Dq4g-q9kSz9y7TtSHdAj_veU)

Gambar: Membuat folder

[https://lh5.googleusercontent.com/WWqLY9dqWTdE3sbw8YjCMU5Asf6RwRC0Yf8MbtpXHimnC5ItWk8KRDqZG8chZszdl-vc2ybo59eoSohFw6wtY9DaRjZUnj6AoyyqXpH7cXAoo4Dl-wQgavN20WSCVEzj1ABxCBiZvyDXjnyPx4bp3Lz1X24](https://lh5.googleusercontent.com/WWqLY9dqWTdE3sbw8YjCMU5Asf6RwRC0Yf8MbtpXHimnC5ItWk8KRDqZG8chZszdl-vc2ybo59eoSohFw6wtY9DaRjZUnj6AoyyqXpH7cXAoo4Dl-wQgavN20WSCVEzj1ABxCBiZvyDXjnyPx4bp3Lz1X24)

Langkah terakhir pada tahap ini tinggal menekan tombol **Create**.

# **Request**

Sebutan ini digunakan untuk nama API yang kita gunakan. Artinya **Request** merupakan spesifikasi permintaan yang kita lakukan kepada API server.

Untuk membuat Request kalian harus mengetahui dokumentasi dari penggunaan API atau bisa dengan mengamati hasil intercept dari Burp Suite. Penggunaan Burp Suite untuk mempelajari penggunaan API akan dibutuhkan jika kalian melakukan penetration test atau security test dengan metode Black Box atau Gray Box. Namun pada whitebox semua dokumentasi akan diberikan oleh Software Engineer. 

Berikut contoh dokumentasi APIs yang diberikan olehnya :

```
What is vAPI ?

vAPI is an API written specifically to illustrate common API vulnerabilities. vAPI is implemented using the Bottle Python Framework and consists of a user database and a token database.

How is vAPI Used ?

vAPI Process flow
1. Request token from /tokens
2. Returns an auth token
3. Returns expiration date of auth token
4. Returns a user id

Request user record from /user/<user_id>
1. Requires the auth token
2. Returns the user record for the user specified, provided the auth token is not expired and is valid for the user id specified
3. Each user can only access their own record
```

```
Test Users

Username : admin1
Password : pass1

Username : user{1-9}
Password : user{1-9}
```

```
API Reference

URL
- http://vuln.cilsy.id:31347
-----------------------------------------------------------------------------------
POST /tokens
Request an Auth Token for a user

Request Headers
Accept: application/json
Content-Type: application/json or application/xml

Request JSON Object
1. username (string) - Name of user requesting token
2. password (string) - Password of user requesting a token

Response JSON Object
1. token
- expires (string) - The Auth Token expiration date/time
token - id (string) - Auth Token
- user - id (string) - Unique user ID
- name (string) - Username

Status Code
1. 200 OK - Request completed successfully

Request
POST /tokens HTTP/1.1
Accept: application/json
Content-Length: 36
Content-Type: application/json
Host: 192.168.13.37:8081

{"auth":
	{"passwordCredentials":
    	{"username": "USER_NAME",
      	"password":"PASSWORD"}
	}
}

 
or
POST /tokens HTTP/1.1
Accept: */*
Content-Length: 170
Content-Type: application/xml
Host: 192.168.13.37:8081

<?xml version="1.0" encoding="UTF-8"?>
<auth>
	<passwordCredentials>
    	<username>user1</username>
    	<password>pass1</password>
	</passwordCredentials>
</auth>

 

Response
HTTP/1.0 200 OK
Date: Tue, 07 Jul 2015 15:34:01 GMT
Server: WSGIServer/0.1 Python/2.7.6
Content-Type: text/html; charset=UTF-8
 
{
	"access":
    	{
        	"token":
            	{
                	"expires": "Tue Jul  7 15:39:01 2015",
                	"id": "AUTH_TOKEN"
            	},
        	"user":
            	{
                	"id": 10,
                	"name": "USER_NAME"
            	}
    	}
}

-----------------------------------------------------------------------------------

GET /user/USER_ID
Retrieve the user's entry in the user database

Request Headers
Accept: application/json
Content-Type: application/json
X-Auth-Token: <TOKEN_ID> (from /tokens POST)

Request JSON Object
1. None

Response JSON Object
1. User
- id (string) - Unique user ID
- name (string) - Username
- password (string) - Password

Status Codes
1. 200 OK - Request completed successfully

Request
GET /user/1 HTTP/1.1
Host: 192.168.13.37:8081
X-Auth-Token: AUTH_TOKEN
Content-type: application/json
Accept: text/plain
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 0

Response
HTTP/1.0 200 OK
Date: Mon, 06 Jul 2015 22:08:56 GMT
Server: WSGIServer/0.1 Python/2.7.9
Content-Length: 73
Content-Type: application/json
 
{
	"response":
    	{
        	"user":
            	{
                	"password": "PASSWORD",
                	"id": USER_ID,
                	"name": "USER_NAME"
            	}
    	}
}

-----------------------------------------------------------------------------------

POST /user
Creates a user with the given username and password. 2 Conditions:
User cannot already exist
Username has to meet strict naming guidelines. The username must be matched by this regular expression: ([a-z]+)*[0-9]. This means that a username has to start with a lowercase letter and end with numbers. So, usernames that look like "user1" or "abc123" will be accepted, but usernames that look like "USER1" or "1user" will not be accepted.

Request Headers
X-Auth-Token - Valid token for the admin user

Request JSON Object
1. User
name (string) - Username that matches above conditions
password (string) - Password

Response JSON Object
1. response
- user
   -> username - the name of the successfully created user
   -> password - the password of the successfully created user

Status Code
1. 200 OK - Request completed successfully

Request
POST /user HTTP/1.1
User-Agent: curl/7.35.0
Host: 127.0.0.1:8081
Accept: */*
x-auth-token: ADMIN TOKEN
Content-type: application/json
Content-Length: 54

{"user":
	{"username": "USERNAME",
	"password": "PASSWORD"}
}

Response
HTTP/1.0 200 OK
Date: Mon, 06 Jul 2015 22:08:56 GMT
Server: WSGIServer/0.1 Python/2.7.9
Content-Length: 68
Content-Type: application/json
 
{
	"response":
    	{
        	"user":
            	{
                	"password": "PASSWORD",
                	"name": "USER_NAME"
            	}
    	}
}

-----------------------------------------------------------------------------------

GET /uptime

GET /uptime/FLAG
Returns the server uptime, and now supports pretty formatting just by passing in command line flags. Super useful for system administrators!

Request JSON Object
1. None

Response JSON Object
1. Response
- Command (string) - The system call you made
- Output (string) - uptime

Status Codes
1. 200 OK - Request completed successfully

Request
GET /uptime/s HTTP/1.1
Host: 192.168.13.37:8081
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 0

Response
HTTP/1.0 200 OK
 Date: Wed, 17 Feb 2016 22:44:27 GMT
 Server: WSGIServer/0.1 Python/2.7.6
 Content-Length: 90
 Content-Type: text/html; charset=UTF-8
 
{
  "response": {
	"Command": "uptime -s",
	"Output": "2016-02-17 09:42:44\n"
  }
}
```

Sebelumnya teman-teman sudah sering menguji aplikasi web secara blackbox ataupun graybox. Kali ini berbeda, teman-teman akan mencoba melakukan penetration test atau security test secara white box berdasarkan dokumentasi diatas.

# ***Authentication***

Menurut dokumentasi diatas langkah pertama harus melakukan autentikasi dengan mengirimkan username dan password.

[https://lh4.googleusercontent.com/xgXjqY8SHgpy_wkKdW7QEIk6DSMN_B0zqqIiCQoBtlM-ttZfV7Zmrn27BopZMTzwcy_iBRZweNC8FBr72R_h6SDwb89HpExauTkMEqSqf1d6LCb6RDwtivn9pJA40Qk4dKnm-bmA0K8KTiIU8m9b08yKeEk](https://lh4.googleusercontent.com/xgXjqY8SHgpy_wkKdW7QEIk6DSMN_B0zqqIiCQoBtlM-ttZfV7Zmrn27BopZMTzwcy_iBRZweNC8FBr72R_h6SDwb89HpExauTkMEqSqf1d6LCb6RDwtivn9pJA40Qk4dKnm-bmA0K8KTiIU8m9b08yKeEk)

Simpan Request diatas lalu selanjutnya kita akan menyesuaikan HTTP method menjadi POST dan endpoint URL pada Request yang baru saja dibuat.

[https://lh3.googleusercontent.com/OeYMYEWv3xDNKQfOsoa-mYI6XiAZUxMFm9HTpeQSyS0y1STTZ6eXOwYX-ahMsnV3VifxOEa5tEX3KzNYUi_AIqRlKWepOyB4bqx6xy2KEJaoUP_ViFVobKvKqslMnM7NZdwYNSpkbe7-0DK7BLiXV-rUmHQ](https://lh3.googleusercontent.com/OeYMYEWv3xDNKQfOsoa-mYI6XiAZUxMFm9HTpeQSyS0y1STTZ6eXOwYX-ahMsnV3VifxOEa5tEX3KzNYUi_AIqRlKWepOyB4bqx6xy2KEJaoUP_ViFVobKvKqslMnM7NZdwYNSpkbe7-0DK7BLiXV-rUmHQ)

Nah masih ingat bukan kalau sebelumnya kita sudah membuat variabel di dalam collection ? Syntax {{endpoint}} digunakan untuk mengambil nilai variabel endpoint.

Langkah selanjutnya kita perlu mengisi HTTP Post parameter pada tab **Body**. Isi sesuai dengan kebutuhan yang ada di dokumentasi API sebelumnya.

[https://lh4.googleusercontent.com/Z0dlsCVoQu3I4B-AeI9GjzptrsUat58Ix3Q_oF6wCgPmPrsmuWpAUXdL_qU5zA_hygWNKUsiRpim9ZRqFUjJSIxsja3R4Md9hdeyAZMgTKMu9hsMnTULDPrLg5YJi8ygnPd8r9ZF_L12eAeW2lyHiFQSGQA](https://lh4.googleusercontent.com/Z0dlsCVoQu3I4B-AeI9GjzptrsUat58Ix3Q_oF6wCgPmPrsmuWpAUXdL_qU5zA_hygWNKUsiRpim9ZRqFUjJSIxsja3R4Md9hdeyAZMgTKMu9hsMnTULDPrLg5YJi8ygnPd8r9ZF_L12eAeW2lyHiFQSGQA)

Perlu teman-teman perhatikan pada **Body** type yang kita gunakan adalah **raw** dan untuk tipe konten kita atur menjadi **JSON**. Dan untuk data JSON kita hanya perlu memasukkan payload sesuai dokumentasi sebelumnya. Selain itu pada JSON payload diatas kita masukkan variabel yang sudah kita definisikan sebelumnya pada collection.

Jika sudah merasa yakin, bisa kalian coba dengan menekan tombol **Send**. Seandainya konfigurasi benar seharusnya kalian akan mendapatkan respon sebagai berikut :

[https://lh6.googleusercontent.com/wEqpsCq7PJdwzq3j3iVzPR714lj72GW3Mq7kILl1bhGBsVI0M26qDtyW0Ir3ZSCLpsQ_V5Y64l7o8bdQq604m50lQwYNvOl4vsMxL54-WHo4hMRsRlgRT1BUhzS3A_rMaosf-x30fyt2MDjwKXF24YXhr7c](https://lh6.googleusercontent.com/wEqpsCq7PJdwzq3j3iVzPR714lj72GW3Mq7kILl1bhGBsVI0M26qDtyW0Ir3ZSCLpsQ_V5Y64l7o8bdQq604m50lQwYNvOl4vsMxL54-WHo4hMRsRlgRT1BUhzS3A_rMaosf-x30fyt2MDjwKXF24YXhr7c)

Selain itu kita bisa mendefinisikan tests script pada Postman untuk melakukan validasi apakah kita berhasil login atau tidak.

[https://lh4.googleusercontent.com/nNOP0RscsFnOG37qgiJKcAgIT2btBpoly3AncSwEX2UzU1fcOb55DEZ3xIX-zS4kc2M5WFOu-sPsUz9OUfInBk_MdXkiZ3Yo6fIA7iPTG3A4_WAMqJbNqp_5JkVOkz6KXaCaWNSKQXucb6mQ-HJV6AELoZs](https://lh4.googleusercontent.com/nNOP0RscsFnOG37qgiJKcAgIT2btBpoly3AncSwEX2UzU1fcOb55DEZ3xIX-zS4kc2M5WFOu-sPsUz9OUfInBk_MdXkiZ3Yo6fIA7iPTG3A4_WAMqJbNqp_5JkVOkz6KXaCaWNSKQXucb6mQ-HJV6AELoZs)

Gambar: Tests script kita atur di tab Tests

Untuk script lengkapnya kurang lebih seperti ini :

```bash
pm.test("01. Permintaan token", function(){
   var response = pm.response.json(); // Mengambil respon berupa JSON
   pm.expect(response.access.token.id).not.equal(undefined); // Validasi token harus ada di respon. Jika ada maka berhasil login
   pm.collectionVariables.set("auth-token", response.access.token.id) // Simpan token ke variabel di collection
});
```

Seandainya kalian sudah memasukan test script tersebut dan sudah disimpan juga, maka ketika kalian klik ulang tombol **Send** kita bisa melihat hasil test scriptnya pada area berikut :

[https://lh6.googleusercontent.com/zTBtd0yx233d31ma2OaGhtdAy2zFqlFc9asf89ZFQSn5iIP_CJY8piXmW6tSP-mt8mw7zBC7yrOo0dtBkP7zJMZuR-TIS2VGfjQQAf3mgHdjDHD_M8oCver5PU88hyYUNW30NKzH3yMSdOP8tSx3Gi0MfR8](https://lh6.googleusercontent.com/zTBtd0yx233d31ma2OaGhtdAy2zFqlFc9asf89ZFQSn5iIP_CJY8piXmW6tSP-mt8mw7zBC7yrOo0dtBkP7zJMZuR-TIS2VGfjQQAf3mgHdjDHD_M8oCver5PU88hyYUNW30NKzH3yMSdOP8tSx3Gi0MfR8)