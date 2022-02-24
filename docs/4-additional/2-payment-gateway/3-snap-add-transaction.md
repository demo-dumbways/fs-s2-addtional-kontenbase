---
sidebar_position: 3
---

# 3. Add Transaction

import useBaseUrl from '@docusaurus/useBaseUrl';

## 3.1 Snap 

**SNAP** adalah portal pembayaran yang memungkinkan merchant untuk menampilkan halaman pembayaran Midtrans langsung di website. Permintaan API harus dilakukan dari `backend merchant (aplikasi kita)` untuk memperoleh token transaksi Snap dengan memberikan informasi pembayaran dan `Server Key`. Setidaknya ada tiga komponen yang diperlukan untuk mendapatkan token Snap `(server_key, order_id, gross_amount)`

## 3.2 Instalasi midtrans-client

Hal pertama yang akan kita lakukan untuk menampilkan halaman pembayaran / snap yakni melakukan instalasi package `midtrans-client`. **Midtrans-client** merupakan sebuah client/library API Node JS resmi untuk pembayaran midtrans. Package ini akan kita install disisi `server` menggunakan command berikut

```shell
npm i midtrans-client
```

## 3.3 Data Transaksi

tentu proses selanjutnya adalah memanggil package midtrans-client yang telah terinstall kedalam file controller transaction

```js title=server/src/controllers/transaction.js {3}
const { user, transaction, product, profile } = require("../../models");

const midtransClient = require("midtrans-client");

exports.getTransactions = async (req, res) => { 
// continuation code is the same as in the template
```

Setelah memanggil package midtrans-client, maka kita akan melakukan `step pertama` dalam proses kerja payment gateway seperti yang telah dijelaskan pada section [introduction](https://ebook-stage-2-dumbways.netlify.app/additional/payment-gateway/Introduction) yakni `menambahkan transaksi`

Kita akan membuat sebuah modul yang nantinya akan menangani terkait proses `add transaction`. Modul ini akan berjalan secara asynchronous agar bisa tetap berjalan tanpa mengganggu proses lainnya. Pada modul ini juga akan menangani error handling dengan menggunakan `try` and `catch`.

```js title=server/src/controllers/transaction.js 
//  this code continues from the above code
exports.addTransaction = async (req, res) => {
  try {

  } catch (error) {

  }
};
```

Pada bagian try, kita akan melakukan proses entri data kedalam database. Diawali dengan menampung data inputan kedalam variabel. Variabel yang telah berisikan data inputan, selanjutnya akan kita entri kedalam database menggunakan method create()

```js title=server/src/controllers/transaction.js {3-11}
exports.addTransaction = async (req, res) => {
  try {
    let data = req.body;
    data = {
        id: parseInt(data.idProduct + Math.random().toString().slice(3, 8)),
        ...data,
        idBuyer: req.user.id,
        status: "pending",
    }

    const newData = await transaction.create(data);
  } catch (error) {

  }
};
```

setelah data transaksi dimasukkan kedalam database, selanjutnya kita akan mencari data pengguna yang melakukan transaksi. Hal ini bertujuan untuk meneruskan informasi transaction menuju Midtrans speerti yang telah dijelaskan diproses `step kedua`

```js title=server/src/controllers/transaction.js {13-27}
exports.addTransaction = async (req, res) => {
  try {
    let data = req.body;
    data = {
        id: parseInt(data.idProduct + Math.random().toString().slice(3, 8)),
        ...data,
        idBuyer: req.user.id,
        status: "pending",
    }

    const newData = await transaction.create(data);

    const buyerData = await user.findOne({
        include: {
            model: profile,
            as: "profile",
            attributes: {
            exclude: ["createdAt", "updatedAt", "idUser"],
            },
        },
        where: {
            id: newData.idBuyer,
        },
        attributes: {
            exclude: ["createdAt", "updatedAt", "password"],
        },
    });
  } catch (error) {

  }
};
```

## 3.4 Konfigurasi API

Saatnya kita menyiapkan konfigurasi data yang akan dikirimkan ke midtrans melalui API yang disediakan oleh package midtrans-client. Kita akan melakukan konfigurasi snap, pada konfigurasi akan membutuhkan `MIDTRANS_SERVER_KEY` yang kita dapatkan dari midtrans.

Referensi : [link](https://docs.midtrans.com/en/midtrans-account/overview?id=retrieving-api-access-keys)

<center>
  <img alt="image1-2" src={useBaseUrl('img/docs/image-payment-5.png')} width="100%"/>
</center>
<br/>

data MIDTRANS_SERVER_KEY akan kita simpan kedalam environment variabel agar lebih aman, isikan pada variabel MIDTRANS_SERVER_KEY

```shell title=.env
PATH_FILE=http://localhost:5000/uploads/
TOKEN_KEY=dsafc97632kdsf0234kjvdsaofy92342bdfre245feg
MIDTRANS_SERVER_KEY=your_server_key_here ...
```

selanjutnya adalah melakukan konfigurasi terkait data - data yang akan dikirimkan dari server ke midtrans. Data ini selanjutnya akan kita kirimkan melalui API midtrans-client

```js title=server/src/controllers/transaction.js {7-22}
exports.addTransaction = async (req, res) => {
  try {
    let data = req.body;
    
    // this code same as code above, just hidden

    let parameter = {
      transaction_details: {
        order_id: newData.id,
        gross_amount: newData.price,
      },
      credit_card: {
        secure: true,
      },
      customer_details: {
        full_name: buyerData?.name,
        email: buyerData?.email,
        phone: buyerData?.profile?.phone,
      },
    };

    const payment = await snap.createTransaction(parameter);
  } catch (error) {

  }
};
```

Step teakhir yang akan kita lakukan adalah mengirimkan response ketika data berhasilataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian try, sedangkan ketika gagal akan kita masukkan kedalam bagian catch.

```js title=server/src/controllers/transaction.js {52-59,61-64}
exports.addTransaction = async (req, res) => {
  try {
    let data = req.body;

    data = {
      id: parseInt(data.idProduct + Math.random().toString().slice(3, 8)),
      ...data,
      idBuyer: req.user.id,
      status: "pending",
    };

    const newData = await transaction.create(data);

    const buyerData = await user.findOne({
      include: {
        model: profile,
        as: "profile",
        attributes: {
          exclude: ["createdAt", "updatedAt", "idUser"],
        },
      },
      where: {
        id: newData.idBuyer,
      },
      attributes: {
        exclude: ["createdAt", "updatedAt", "password"],
      },
    });

    let snap = new midtransClient.Snap({
      isProduction: false,
      serverKey: process.env.MIDTRANS_SERVER_KEY,
    });

    let parameter = {
      transaction_details: {
        order_id: newData.id,
        gross_amount: newData.price,
      },
      credit_card: {
        secure: true,
      },
      customer_details: {
        full_name: buyerData?.name,
        email: buyerData?.email,
        phone: buyerData?.profile?.phone,
      },
    };

    const payment = await snap.createTransaction(parameter);

    res.send({
      status: "pending",
      message: "Pending transaction payment gateway",
      payment,
      product: {
        id: data.idProduct,
      },
    });
  } catch (error) {
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};
```

response yang akan didapatkan ketika berhasil mengirimkan data berupa `token dan redirect_url`. **Token** berfungsi untuk menampilkan popup snap pada sisi client. Sedangkan **redirect_url** berfungsi untuk menampilkan langsung tanpa snap (kehalaman midtrans). Oleh karena itu, nantinya yang kita butuhkan hanyalah property token dari response yang didapatkan.

```shell
{
  "token": "66e4fa55-fdac-4ef9-91b5-733b97d1b862",
  "redirect_url": "https://app.sandbox.midtrans.com/snap/v2/vtweb/66e4fa55-fdac-4ef9-91b5-733b97d1b862"
}
```

