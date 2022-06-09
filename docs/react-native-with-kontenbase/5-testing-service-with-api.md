---
sidebar_position: 5
---

# 5. Testing Service with API

import useBaseUrl from '@docusaurus/useBaseUrl';

### 5.1 Postman

Selain menguji Rest API menggunakan GUI yang telah disediakan `KontenBase`, Anda juga dapat menguji Rest API menggunakan Aplikasi REST CLIENT seperti [POSTMAN](https://www.postman.com/). Dibawah ini contoh pengujian REST API menggunakan `Postman`.

### 5.2 `GET` Find Records

- Copy Url API `Find Records`

<center>
    <img alt="kb-img-14" src={useBaseUrl('img/docs/kb-14.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman, lalu atur HTTP Method menjadi GET, dan klik tombol `Send`. Maka Anda akan mendapatkan semua data.

<center>
    <img alt="kb-img-15" src={useBaseUrl('img/docs/kb-15.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/find)

### 5.3 `GET` Get Record

- Copy Url API `Get Record`

<center>
    <img alt="kb-img-16" src={useBaseUrl('img/docs/kb-16.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman beserta isi `ID` pada bagian akhir `URL`, lalu atur HTTP Method menjadi GET, dan klik tombol `Send`. Maka Anda akan mendapatkan data berdasarkan ID.

<center>
    <img alt="kb-img-17" src={useBaseUrl('img/docs/kb-17.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/get-by-id)

### 5.4 `GET` Count Records

- Copy Url API `Count Records`

<center>
    <img alt="kb-img-18" src={useBaseUrl('img/docs/kb-18.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman, lalu atur HTTP Method menjadi GET, dan klik tombol `Send`. Maka Anda akan mendapatkan jumlah data.

<center>
    <img alt="kb-img-19" src={useBaseUrl('img/docs/kb-19.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/count)

### 5.5 `POST` Create Record

- Copy Url API `Create Record`

<center>
    <img alt="kb-img-20" src={useBaseUrl('img/docs/kb-20.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman, lalu atur HTTP Method menjadi `POST`, Input data yang ingin Anda tambahkan dengan klik `Body` &#8594; `raw` &#8594; `JSON`, dan klik tombol `Send`.

<center>
    <img alt="kb-img-21" src={useBaseUrl('img/docs/kb-21.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/create)

Anda dapat cek data yang telah ditambahkan menggunakan API `Find Records`

### 5.6 `PATCH` Update Record

- Copy Url API `Update Record`

<center>
    <img alt="kb-img-22" src={useBaseUrl('img/docs/kb-22.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman beserta isi `ID` pada bagian akhir `URL`, lalu atur HTTP Method menjadi `PATCH`, Input data yang ingin Anda ubah dengan klik `Body` &#8594; `raw` &#8594; `JSON`, dan klik tombol `Send`.

<center>
    <img alt="kb-img-23" src={useBaseUrl('img/docs/kb-23.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/update-by-id)

Anda dapat cek data yang telah diubah menggunakan API `Find Records`

### 5.7 `DELETE` Delete Record

- Copy Url API `Delete Record`

<center>
    <img alt="kb-img-24" src={useBaseUrl('img/docs/kb-24.png')} width="80%"/> 
</center>

- Paste URL pada Request Postman beserta isi `ID` pada bagian akhir `URL`, lalu atur HTTP Method menjadi `DELETE`, dan klik tombol `Send`.

<center>
    <img alt="kb-img-25" src={useBaseUrl('img/docs/kb-25.png')} width="80%"/> 
</center>

Referensi: [Link](https://docs.kontenbase.com/service/delete-by-id)

Anda dapat cek data yang telah dihapus menggunakan API `Find Records`
