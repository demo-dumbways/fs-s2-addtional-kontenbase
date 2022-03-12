---
sidebar_position: 3
---

# Postman

import useBaseUrl from '@docusaurus/useBaseUrl';

Postman adalah sebuah aplikasi yang berfungsi sebagai REST CLIENT untuk uji coba REST API. Postman biasa digunakan oleh developer pembuat API sebagai tools untuk menguji API yang telah mereka buat.

<img alt="image1-2" src={useBaseUrl('img/docs/intro-postman-1.png')} width="100%"/>

## Installation
- Download file installer nya di website resmi postman [postman.com](https://www.getpostman.com/downloads/)
- Jalankan file installer nya yang berformat .exe
- Buat akun postman baru atau masuk dengan akun postman (anda dapat melewati nya tanpa masuk akun)
<br/>
<br/>

## Akses API dengan Postman

Untuk Mencoba API yang sudah kita buat kita memerlukan sebuah aplikasi yang dapat mengakses dan menyajian data dari sebuah API. untuk itu pastikan kalian sudah memiliki aplikasi yang bernama Postman, jika belum bisa mendownload melalui link dibawah ini

**Postman :[Download](https://www.postman.com/downloads/?utm_source=postman-home)**

**Dokumentasi Penggunaan Lebih lengkap : [Here](https://learning.postman.com/docs/sending-requests/requests/)**

```link title=baseUrl
https://ebook-code-results-stage-2-backend-git-3-e-d5f17e-demo-dumbways.vercel.app
```

Berikut list route yang telah dibuat ...

| Method | Route       |
| ------ | ----------- |
| GET    | `/todos`    |
| GET    | `/todo/:id` |
| POST   | `/todo`     |
| PATCH  | `/todo/:id` |
| DELETE | `/todo/:id` |

- Buka Aplikasi Postman
- Klik +, maka akan muncul tampilan seperti berikut :
  <img alt="image1-2" src={useBaseUrl('img/docs/Postman-1.png')} width="100%"/>
- Pastekan link yang sudah anda copy kesini

  <img alt="image1-2" src={useBaseUrl('img/docs/Postman-2.png')} width="100%"/>

- Tentukan Method dan Route yang tertera pada ebook

  <img alt="image1-2" src={useBaseUrl('img/docs/Postman-3.png')} width="100%"/>
