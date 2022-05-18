---
sidebar_position: 6
---

# 6. Stand Alone APK

import useBaseUrl from '@docusaurus/useBaseUrl';

`Stand Alone Application` adalah aplikasi mandiri digunakan saat tidak diperlukan koneksi internet untuk fungsionalitas aplikasi utama. Semua data dapat disimpan secara lokal di perangkat. Konektivitas jaringan tidak diperlukan agar aplikasi berfungsi.

Disini kita akan membuat sebuah stand alone APK menggunakan Expo, Expo memungkinkan kita untuk membangun sebuah aplikasi mandiri untuk device `Android` ataupun `IOS`.  Membuat stand alone apk menggunakan expo membutuhkan expo-cli. Maka pastikan sudah terinstall, jika belum maka lakukan perintah instal seperti berikut:

```bash
npm install -g expo-cli
```

Selanjutnya buka file app.json, lalu ubah bagian kode berikut dengan nama perusahaan beserta nama aplikasi yang akan di-deploy. Pada case kali ini kita akan melakukan build stand alone APK untuk device berbasis `android`.

```json title=app.json {11-14}
{
   "expo": {
    "name": "Your App Name",
    "icon": "./path/to/your/app-icon.png",
    "version": "1.0.0",
    "slug": "your-app-slug",
    "ios": {
      "bundleIdentifier": "com.yourcompany.yourappname",
      "buildNumber": "1.0.0"
    },
    "android": {
      "package": "com.yourcompany.yourappname",
      "versionCode": 1
    }
   }
 }
```

Selanjutnya jalankan command berikut untuk memulai proses build,

```bash
expo build:android
```

Pertama kali melakukan proses build APK, maka akan diminta untuk login terlebih dahulu menggunakan akun expo yang telah terdaftar.Selanjutnya akan diberikan pilihan untuk memanajemen keystore, kita akan menggunakan keystore yang akan dihandle oleh expo. Maka kita pilih nomor satu, dengan cara `ketikkan angka 1` pada terminal.

<center>
  <img alt="image-4-rn" src={useBaseUrl('img/docs/image-4-rn.png')} width="100%"/>
</center>

selanjutnya pilih option APK sebagai tipe yang akan kita build

<center>
  <img alt="image-4-rn" src={useBaseUrl('img/docs/image-4-2-rn.png')} width="100%"/>
</center>

Durasi proses build apk akan bergantung dengan antrian yang ada di Expo. Sehingga bisa dipantau proses build APK melalui dashboard akun Expo. 




