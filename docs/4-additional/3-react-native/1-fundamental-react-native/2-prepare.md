---
sidebar_position: 2
---

# 2. Prepare

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum menggunakan `React Native`, kita perlu melakukan beberapa persiapan seperti `installasi package`dan `refactor code`.

## 2.1 Installasi React Native

Kita perlu menginstall Expo global terlebih dahulu Expo adalah adalah framework berbasis react native yang digunakan juga untuk mengembangkan aplikasi dengan tujuan yang sama yaitu dapat berjalan pada Android dan IOS.

Install Expo Global

```bash
npm install -g expo-cli
```

Selanjutnya kita buat project react native dengan nama `my-app` dengan perintah berikut:

```bash
expo init my-app
```

Kemudian masuk ke direktori project yang berhasil dibuat

```bash
cd my-app
```

Jalankan project dengan perintah berikut:

```bash
npm start
```

<br />
<center>
  <img alt="" src={useBaseUrl('img/docs/rn-2.png')} width="25%"/>
</center>
<br />

## 2.2 Struktur Folder

Struktur folder dalam React Native Expo seprti berikut:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io">
Contoh Folder
</a>
<br />
<br />

```text
 ┣ .expo
 ┣ .expo-shared
 ┣ .git
 ┣ assets
 ┣ node_modules
 ┣ src
 ┃ ┣ components
 ┣ .gitignore
 ┣ App.js
 ┣ app.json
 ┣ babel.config.js
 ┣ package-lock.json
 ┣ package.json
```
