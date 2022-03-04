---
sidebar_position: 2
---

# 2. Prepare

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum kita melakukan pengiriman email, maka kita perlu melakukan instalasi package `nodemailer` menggunakan NPM pada sisi server.

```shell
npm install nodemailer
```

selanjutnya kita akan menyimpan data `email` dan `password` akun email yang akan menjadi pengirim email notifikasi pembayaran. Data email dan password akan kita simpan kedalam environment variabel agar lebih aman.

```js title=.env {5-6}
PATH_FILE=http://localhost:5000/uploads/
TOKEN_KEY=dsafc97632kdsf0234kjvdsaofy92342bdfre245feg
MIDTRANS_SERVER_KEY=your_server_key_here ...
MIDTRANS_CLIENT_KEY=your_server_key_here ...
SYSTEM_EMAIL=xxxxxxxxx@gmail.com
SYSTEM_PASSWORD=xxxxxxxxx
```

Jika terjadi error ketika mengirimkan pesan email
```
Error: Invalid login: 535-5.7.8 Username and Password not accepted.
```

maka lakukan konfigurasi lanjutan pada akun email seperti langkah berikut 
- Masuk kedalam halaman akun google
    <center>
    <img alt="image1-2" src={useBaseUrl('img/docs/image-nodemailer-2.png')} width="100%"/>
    </center>

- Click Keamanan and Nonaktifkan akses
    <center>
    <img alt="image1-2" src={useBaseUrl('img/docs/image-nodemailer-3.png')} width="100%"/>
    </center>

- Turn on `izinkan aplikasi yang kurang aman`
    <center>
    <img alt="image1-2" src={useBaseUrl('img/docs/image-nodemailer-4.png')} width="100%"/>
    </center>
