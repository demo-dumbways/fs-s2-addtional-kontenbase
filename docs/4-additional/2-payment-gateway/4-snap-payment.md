---
sidebar_position: 4
---

# 4. Handle Payment

import useBaseUrl from '@docusaurus/useBaseUrl';

## 4.1 Konfigurasi CoreApi

Pembayaran yang dilakukan oleh pembeli akan ditangani oleh midtrans-client. Oleh karena itu kita perlu melakukan konfigurasi terhadap API yang akan digunakan. Pada proses ini membutuhkan `MIDTRANS_CLIENT_KEY` yang didapat dari akun midtrans (sama seperti sebelumnya MIDTRANS_SERVER_KEY). Data `MIDTRANS_CLIENT_KEY` akan kita simpan pula kedalam variabel environment.

```shell {4} title=.env
PATH_FILE=http://localhost:5000/uploads/
TOKEN_KEY=dsafc97632kdsf0234kjvdsaofy92342bdfre245feg
MIDTRANS_SERVER_KEY=your_server_key_here ...
MIDTRANS_CLIENT_KEY=your_server_key_here ...
```

```js title=server/src/controllers/transaction.js {3-12}
// this code continues from the previous section

const MIDTRANS_CLIENT_KEY = process.env.MIDTRANS_CLIENT_KEY;
const MIDTRANS_SERVER_KEY = process.env.MIDTRANS_SERVER_KEY;

const core = new midtransClient.CoreApi();

core.apiConfig.set({
  isProduction: false,
  serverKey: MIDTRANS_SERVER_KEY,
  clientKey: MIDTRANS_CLIENT_KEY,
});
```

## 4.2 Konfigurasi Notifikasi

Selanjutnya kita perlu memberikan `notifikasi` kepada pembeli terkait payment yang dilakukan. Kita akan membuat sebuah modul yang nantinya akan menangani terkait proses `notifikasi`. Modul ini akan berjalan secara asynchronous agar bisa tetap berjalan tanpa mengganggu proses lainnya. Pada modul ini juga akan menangani error handling dengan menggunakan `try` and `catch`.

```js title=server/src/controllers/transaction.js {3-8}
// this code continues from the code above

exports.notification = async (req, res) => {
  try {
      
  } catch (error) {
      
  }
};
```

Pada bagian try, kita akan melakukan proses update `status payment` dan `stock produck`. Diawali dengan menampung data response dari `CoreApi` kedalam variabel. Data yang disimpan ada tiga, yakni `orderId, transactionStatus, fraudStatus`.

```js title=server/src/controllers/transaction.js {3-7}
exports.notification = async (req, res) => {
  try {
    const statusResponse = await core.transaction.notification(req.body);
    
    const orderId = statusResponse.order_id;
    const transactionStatus = statusResponse.transaction_status;
    const fraudStatus = statusResponse.fraud_status;
  } catch (error) {
      
  }
};
```

Selanjutnya kita akan melakukan pengkondisian terhadap kondisi - kondisi tertentu berdasarkan `transactionStatus`. Terdapat 6 status yang akan dicek kondisinya yakni `capture, settlement, cancel, den, expire, dan pending` untuk menghasilkan response yang berbeda. Pada step kali ini kita juga akan menambahkan response dibagian `catch` jika terjadi error.

Referensi : [Link](https://docs.midtrans.com/en/after-payment/status-cycle)

```js title=server/src/controllers/transaction.js {9-31,33}
exports.notification = async (req, res) => {
  try {
    const statusResponse = await core.transaction.notification(req.body);
    
    const orderId = statusResponse.order_id;
    const transactionStatus = statusResponse.transaction_status;
    const fraudStatus = statusResponse.fraud_status;

    if (transactionStatus == "capture") {
      if (fraudStatus == "challenge") {
        updateTransaction("pending", orderId);
        res.status(200);
      } else if (fraudStatus == "accept") {
        updateProduct(orderId);
        updateTransaction("success", orderId);
        res.status(200);
      }
    } else if (transactionStatus == "settlement") {
      updateTransaction("success", orderId);
      res.status(200);
    } else if (
      transactionStatus == "cancel" ||
      transactionStatus == "deny" ||
      transactionStatus == "expire"
    ) {
      updateTransaction("failed", orderId);
      res.status(200);
    } else if (transactionStatus == "pending") {
      updateTransaction("pending", orderId);
      res.status(200);
    }
  } catch (error) {
    res.status(500);
  }
};
```

## 4.3 Update Status Pembayaran

Pada potongan code diatas, maka kita perlu membuat `function updateTransaction`. Function **updateTransaction** bertujuan untuk menangani proses perubahan data status pada database berdasarkan status yang didapatkan dari response `CoreApi`. 

```js title=server/src/controllers/transaction.js {3-14}
// this code continues from the code above

const updateTransaction = async (status, transactionId) => {
  await transaction.update(
    {
      status,
    },
    {
      where: {
        id: transactionId,
      },
    }
  );
};
```

## 4.3 Update Stock Produk

Pada potongan code diatas, maka kita perlu membuat `function updateProduct`. Function **updateProduct** bertujuan untuk menangani proses perubahan data stock product yang ada didatabase.

```js title=server/src/controllers/transaction.js {3-1}
// this code continues from the code above

const updateProduct = async (orderId) => {
  const transactionData = await transaction.findOne({
    where: {
      id: orderId,
    },
  });
  const productData = await product.findOne({
    where: {
      id: transactionData.idProduct,
    },
  });
  const qty = productData.qty - 1;
  await product.update({ qty }, { where: { id: productData.id } });
};
```

## 4.4 Menambahkan Route Notification

Pastikan modul - modul yang akan diakses nantinya telah dipanggil kedalam file `routes/index.js`. Terdapat 3 modul yang berkaitan dengan transaction yakni `getTrasactions`, `addTransaction`, `notification`.

```js title=routes/index.js {3-7}
// this code continues from template 

const {
  getTransactions,
  addTransaction,
  notification,
} = require("../controllers/transaction");
```
Method yang digunakan pada routes notification yakni `POST`. Hal ini bertujuan untuk menghandle `HTTP POST` dan `JSON Object` yang dikirimkan oleh midtrans

```js title=routes/index.js {3}
// this code continues from template 

const {
  getTransactions,
  addTransaction,
  notification,
} = require("../controllers/transaction");

// this code continues from template 

router.post("/notification", notification);
```