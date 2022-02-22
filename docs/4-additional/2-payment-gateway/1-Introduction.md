---
sidebar_position: 1
---

# 1. Introduction

import useBaseUrl from '@docusaurus/useBaseUrl';

## 1.1 Payment Gateway

<center>
  <img alt="image1-2" src={useBaseUrl('img/docs/image-payment-1.png')} width="70%"/>
</center>

**Payment gateway** adalah alat pembayaran suatu transaksi dalam layanan aplikasi `e-commerce` dengan fungsi mengautorisasi berbagai proses pembayaran baik perbankan, kartu kredit, transfer bank maupun secara langsung dari konsumen.

Cara kerja payment gateway:
- Konsumen Melakukan Transaksi <br/>
  Cara kerja payment gateway pertama adalah konsumen e-commerce melakukan pembayaran menggunakan opsi pembayaran `payment gateway`. Pembayaran dengan payment gateway dapat menjadi salah satu opsi atau terpasang otomatis saat konsumen akan membayar.

- Penerusan Informasi Payment Gateway ke Prosessor Pembayaran <br/>
  Payment gateway akan meneruskan informasi pada langkah pertama yang diketahui oleh koneksi sumber payment gateway kepada pelaku proses pembayaran yang dipilih konsumen. Misalnya konsumen memilih transaksi pembayaran melalui bank, maka payment gateway akan menyampaikan informasi ke bank tersebut.

- Informasi Diterima Oleh Asosiasi Penerbit <br/>
  pelaku prosessor pembayaran menyampaikan informasi terjadinya payment gateway kepada asosiasi penerbit kartu, seperti Visa atau Mastercard. Selain berdasarkan Visa atau Mastercard, payment gateway juga dapat menghubungkan ke bank-bank yang bekerjasama dengan payment gateway bersangkutan.

- Pemberian Kode Khusus <br/>
  Setelah itu, asosiasi penerbit akan memberikan balasan berupa kode khusus ke prosessor pembayaran. Kode khusus ini sifatnya mirip dengan OTP, akan tetapi hanya diketahui oleh penerbit kartu dan prosesor payment gateway

- Keberhasilan Transaksi <br/>
  Setelah kode pembayaran diterima dan dikonfirmasi, payment gateway akan mengubah status pembayaran konsumen menjadi lunas. Setelah itu, payment gateway akan meneruskan informasi ke merchant pemasang, dan transaksi jual beli pun sukses dilakukan

## 1.2 Explanation

Pada materi ini kita akan membuat fitur `payment gateway` menggunakan salah satu penyedia layanan payment gateway yakni `Midtrans`. 

**Midtrans** adalah gateway pembayaran yang memfasilitasi kebutuhan bisnis online dengan memberikan layanan dalam berbagai metode pembayaran. Layanan ini memungkinkan para pelaku industri untuk beroperasi lebih mudah dan meningkatkan penjualan. Metode pembayaran yang disediakan adalah card payment, bank transfer, direct debit, e-wallet, over the counter, dan lain-lain




