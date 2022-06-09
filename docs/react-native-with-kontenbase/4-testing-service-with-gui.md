---
sidebar_position: 4
---

# 4. Testing Service with GUI

import useBaseUrl from '@docusaurus/useBaseUrl';

### 4.1 REST API pada Service

Setiap `Service` memiliki beberapa GUI Rest API yang dapat Anda gunakan, seperti pada gambar dibawah ini:

<center>
    <img alt="kb-img-7" src={useBaseUrl('img/docs/kb-7.png')} width="80%"/> 
</center>

<br />

Keterangan:

- `GET` **Find Records**: Mengambil semua data
- `GET` **Get Record**: Mengambil sebuah data berdasarkan **ID**
- `GET` **Count Records**: Mengambil jumlah data
- `POST` **Create Record**: Menambahkan data
- `PATCH` **Update Record**: Mengubah data
- `DELETE` **Delete Record**: Menghapus data

### 4.2 `GET` Find Records

Klik tombol `Send` sebelah kanan atas untuk akses GUI API `Find Records` pada Service `Todo`, maka Anda akan mendapat semua data.

<center>
    <img alt="kb-img-8" src={useBaseUrl('img/docs/kb-8.png')} width="80%"/> 
</center>

### 4.3 `GET` Get Record

Untuk mengambil sebuah data, Anda harus Input kolom ID dari salah satu data pada Service `Todo`, kemudian klik tombol `Send`.

<center>
    <img alt="kb-img-9" src={useBaseUrl('img/docs/kb-9.png')} width="80%"/> 
</center>

### 4.4 `GET` Count Records

Klik tombol `Send` sebelah kanan atas untuk akses GUI API `Count Records` pada Service `Todo`, maka Anda akan mendapat jumlah data.

<center>
    <img alt="kb-img-10" src={useBaseUrl('img/docs/kb-10.png')} width="80%"/> 
</center>

### 4.5 `POST` Create Record

Untuk menambahkan data pada Service `Todo`, `Input` terlebih dahulu fields Service `Todo` (title dan isDone). Kemudian klik tombol `Send`.

<center>
    <img alt="kb-img-11" src={useBaseUrl('img/docs/kb-11.png')} width="80%"/> 
</center>

Anda dapat cek data yang telah ditambahkan menggunakan GUI API `Find Records`

### 4.6 `PATCH` Update Record

Untuk mengubah data pada Service `Todo`, `Input` terlebih pada fields yang ingin Anda ubah datanya. Kemudian klik tombol `Send`.

<center>
    <img alt="kb-img-12" src={useBaseUrl('img/docs/kb-12.png')} width="80%"/> 
</center>

Anda dapat cek data yang telah diubah menggunakan GUI API `Find Records`

### 4.7 `DELETE` Delete Record

Untuk menghapus data, Anda harus Input kolom ID dari salah satu data pada Service `Todo`, kemudian klik tombol `Send`.

<center>
    <img alt="kb-img-13" src={useBaseUrl('img/docs/kb-13.png')} width="80%"/> 
</center>

Anda dapat cek data yang telah dihapus menggunakan GUI API `Find Records`
