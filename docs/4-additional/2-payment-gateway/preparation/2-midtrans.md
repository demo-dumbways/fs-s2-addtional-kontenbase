---
sidebar_position: 2
---

# Midtrans

import useBaseUrl from '@docusaurus/useBaseUrl';

Hal pertama yang harus kita lakukan adalah melakukan registrasi akun Midtrans. Registrasi akun dapat diakses melalui laman resmi midtrans yakni [midtrans.com](https://midtrans.com/)

<center>
  <img alt="image1-2" src={useBaseUrl('img/docs/image-payment-2.png')} width="100%"/>
</center>
<br/>

Setelah melakukan registrasi akun, maka kita perlu melakukan konfigurasi notifikasi pada midtrans. Notifikasi yang akan dikonfigurasi yakni pada bagian `Payment Notification URL` dan `Finish Redirect URL`. 

1. Payment Notification URL <br/>
   **Payment Notification** adalah konfigurasi yang digunakan untuk menentukan URL tujuan pengiriman notifikasi saat pembayaran dilakukan oleh pelanggan. `Value` yang kita isikan didapatkan dari url yang disediakan oleh `local tunnel pada sisi server` ketika dijalankan.

    <center>
    <img alt="image1-2" src={useBaseUrl('img/docs/image-payment-3.png')} width="100%"/>
    </center>
    <br/>

2. Finish Redirect URL <br/>
   **Finish Redirect URL** adalah konfigurasi yang digunakan untuk menentukan URL yang akan dituju pelanggan saat transaksi selesai. `Value` yang kita isikan didapatkan dari url yang disediakan oleh `local tunnel pada sisi client` ketika dijalankan.

    <center>
    <img alt="image1-2" src={useBaseUrl('img/docs/image-payment-4.png')} width="100%"/>
    </center>
    <br/>

