---
sidebar_position: 2
---

# ReactJs

import useBaseUrl from '@docusaurus/useBaseUrl';

## Installation

Anda perlu melakukan Instalasi ReactJs pada perangkat komputer, sebelum melakukan instalasi pastikan Anda telah menginstall `NodeJs` dengan versi minimal 14.0.0 ([Referensi](https://reactjs.org/docs/create-a-new-react-app.html)).

Lakukan instalasi `create-react-app` dengan perintah berikut pada terminal/command prompt:

```bash
npm install create-react-app
```

**create-react-app** adalah seperangkat alat yang memungkinkan Anda membuat aplikasi `React`. `create-react-app` menyimpan dependensi seperti webpack dan babel di dalam skrip react. `create-react-app` memudahkan untuk bekerja dengan transpiler dan bundler.

## Membuat Aplikasi ReactJs

Sebelum membuat Aplikasi ReactJs, pastikan Anda telah menyiapkan directory/folder untuk menyimpan Aplikasi ReactJs.

Anda dapat membuat Aplikasi `ReactJs` menggunakan alat `create-react-app` yang telah diinstall sebelumnya. Jalankan perintah berikut pada terminal/command prompt Anda:

```bash
npx create-react-app my-app
```

Keterangan:

- `npx`: **node package execute** untuk mengeksekusi package nodejs
- `create-react-app`: package untuk membuat aplikasi ReactJs
- `my-app`: nama aplikasi reactjs yang dibuat

Hasil setelah menjalankan perintah untuk membuat Aplikasi ReactJs:

<center>
<img alt="image" src={useBaseUrl('img/docs/image-started-reactjs-1.png')} width="70%"/>
</center>

## Menjalankan Aplikasi ReactJs

Untuk menjalankan Aplikasi ReactJs Anda harus masuk terlebih dahulu kedalam directory Aplikasi ReactJs. Gunakan perintah berikut untuk masuk kedalam directory Aplikasi ReactJs `my-app`.

```bash
cd my-app
```

Setelah masuk kedalam directory `my-app`, gunakan perintah berikut untuk menjalankan Aplikasi ReactJs `my-app`:

```
npm start
```

Secara default Aplikasi ReactJs, akan berjalan pada port `3000`. Sehingga Anda dapat mengakses Aplikasi ReactJs menggunakan url berikut `localhost:3000`

<center>
<img alt="image" src={useBaseUrl('img/docs/image-started-reactjs-2.png')} width="70%"/>
</center>
