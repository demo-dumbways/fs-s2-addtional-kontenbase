---
sidebar_position: 1
---

# Local Tunnel

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum kita melakukan proses payment gateway menggunakan midtrans, maka kita perlu membuat aplikasi/server local kita dapat diakses melalui internet. Menggunakan `localtunnel` memungkikan kita untuk melakukan hal tersebut. **Local tunnel** merupakan sebuah package yang disediakan oleh NPM dan berfungsi untuk membuat server local bisa diakses secara public tanpa memerlukan `Domain Name Server (DNS)`.

Maka langkah pertama yang harus kita lakukan adalah menginstall package local tunnel melalui NPM

```shell
npm i localtunnel
```

Setelah melakukan instalasi local tunnel, maka kita perlu menjalankan local tunnel di sisi client maupun sisi server. Maka kita perlu menjalankannya pada port yang berbeda agar tidak terjadi conflict.

Kita akan menjalankan localtunnel pada port `3000` untuk sisi client menggunakan command berikut
```shell
lt --port 3000
```

sedangkan pada sisi server akan kita jalankan pada port `5000` menggunakan command berikut
```shell
lt --port 5000
```


