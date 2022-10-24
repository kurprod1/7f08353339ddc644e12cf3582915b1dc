# Penggunaan Drozer

Created: June 22, 2022 1:17 PM

Pastikan kalian sudah memasang drozer di android dan di laptop dengan mengikuti petunjuk dari situs resminya. Aktifkan drozer server pada android dengan menekan tombol ON pada layar ini.

[https://lh5.googleusercontent.com/FnNToLFV3H_YYfhZelTaPubKQdpjKDzzVWLCYfeO_Bsc3AcOOHsLYoSh9kTHgVfCV7UPn-2kgBNX1FEfq6kn3imFEZgdeg_lCUnka7JNaOCSWLVaL8XG7k0hdK3CEV1TGXOU6vOeFJO_WsjeFX3UlbOj5y8](https://lh5.googleusercontent.com/FnNToLFV3H_YYfhZelTaPubKQdpjKDzzVWLCYfeO_Bsc3AcOOHsLYoSh9kTHgVfCV7UPn-2kgBNX1FEfq6kn3imFEZgdeg_lCUnka7JNaOCSWLVaL8XG7k0hdK3CEV1TGXOU6vOeFJO_WsjeFX3UlbOj5y8)

Mengaktifkan port forwarding sebelum bisa menjalankan drozer dengan perintah berikut :

```bash
$ adb forward tcp:31415 tcp:31415$ drozer console connect
```

Mendapatkan daftar aplikasi yang terpasang di android

```bash
dz> run app.package.list
```

Identifikasi kemungkinan darimana saja kita bisa menyerang

```bash
dz> run app.package.attacksurface <package id>
```

Identifikasi activity yang di export

```bash
dz> run app.activity.info -a <package id>
```

Menjalankan activity

```bash
dz> run app.activity.start --component <package id> <activity_name>
```

Mendapatkan informasi content provider

```bash
dz> run app.provider.info -a <package id>
```

Mendapatkan skema URI yang tersedia

```bash
dz> run app.provider.finduri
```

Mendapatkan data dari content provider

```bash
dz> run app.provider.query <URI scheme didapatkan di step sebelumnya>
```

Module lain yang tersedia untuk content provider:

1. app.provider.update
2. app.provider.delete
3. app.provider.info
4. app.provider.download
5. app.provider.read