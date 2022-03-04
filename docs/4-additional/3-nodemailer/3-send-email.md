---
sidebar_position: 3
---

# 3. Send Email

import useBaseUrl from '@docusaurus/useBaseUrl';

Melakukan proses pengiriman email menggunakan nodemailer, maka kita akan mengimport package `nodemailer` kedalam file `transaction.js`

```js title=server/src/controller/transaction.js {6}
const { user, transaction, product, profile } = require("../../models");
const midtransClient = require("midtrans-client");

const convertRupiah = require("rupiah-format");

const nodemailer = require("nodemailer");

// continuation code is the same as in the template
```

Setelah itu, kita akan membuat sebuah method yang akan menghandle data - data /  pesan yang akan dikirimkan melalui email serta melakuakn konfigurasi `service` dan `email account`

```js title=server/src/controller/transaction.js {18-26}
// continuation code is the same as in the template

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

const sendEmail = async (status, transactionId) => {
  const transporter = nodemailer.createTransport({
    service: "gmail",
    auth: {
      user: process.env.SYSTEM_EMAIL,
      pass: process.env.SYSTEM_PASSWORD,
    },
  });
};
```

Nantinya pada bagian pesan yang dikirimkan kita akan membutuhkan data terkait `transaksi`. Oleh karena itu kita akan mencari data transaksi yang akan dikirimkan notifikasi pembayarannya menggunakan method `ORM findOne`.

```js title=server/src/controller/transaction.js {12-44}
// this code continuation from code above

const sendEmail = async (status, transactionId) => {
  const transporter = nodemailer.createTransport({
    service: "gmail",
    auth: {
      user: process.env.SYSTEM_EMAIL,
      pass: process.env.SYSTEM_PASSWORD,
    },
  });

  let data = await transaction.findOne({
    where: {
      id: transactionId,
    },
    attributes: {
      exclude: ["createdAt", "updatedAt", "password"],
    },
    include: [
      {
        model: user,
        as: "buyer",
        attributes: {
          exclude: ["createdAt", "updatedAt", "password", "status"],
        },
      },
      {
        model: product,
        as: "product",
        attributes: {
          exclude: [
            "createdAt",
            "updatedAt",
            "idUser",
            "qty",
            "price",
            "desc",
          ],
        },
      },
    ],
  });

  data = JSON.parse(JSON.stringify(data));
};
```

Setelah mendapatkan data transaksi, maka selanjutnya kita akan membuat `email body / pesan` yang akan dikirimkan melalui email


```js title=server/src/controller/transaction.js {6-33}
const sendEmail = async (status, transactionId) => {
  // this code continuation from code above

  data = JSON.parse(JSON.stringify(data));

  const mailOptions = {
    from: process.env.SYSTEM_EMAIL,
    to: data.buyer.email,
    subject: "Payment status",
    text: "Your payment is <br />" + status,
    html: `<!DOCTYPE html>
            <html lang="en">
              <head>
                <meta charset="UTF-8" />
                <meta http-equiv="X-UA-Compatible" content="IE=edge" />
                <meta name="viewport" content="width=device-width, initial-scale=1.0" />
                <title>Document</title>
                <style>
                  h1 {
                    color: brown;
                  }
                </style>
              </head>
              <body>
                <h2>Product payment :</h2>
                <ul style="list-style-type:none;">
                  <li>Name : ${data.product.name}</li>
                  <li>Total payment: ${convertRupiah.convert(data.price)}</li>
                  <li>Status : <b>${status}</b></li>
                </ul>  
              </body>
            </html>`,
  };

};
```

Terakhir adalam mengirimkan email jikan terjadi perubahan status pembayaran pada transaksi

```js title=server/src/controller/transaction.js {35-45}
const sendEmail = async (status, transactionId) => {
  // this code continuation from code above

  data = JSON.parse(JSON.stringify(data));

  const mailOptions = {
    from: process.env.SYSTEM_EMAIL,
    to: data.buyer.email,
    subject: "Payment status",
    text: "Your payment is <br />" + status,
    html: `<!DOCTYPE html>
            <html lang="en">
              <head>
                <meta charset="UTF-8" />
                <meta http-equiv="X-UA-Compatible" content="IE=edge" />
                <meta name="viewport" content="width=device-width, initial-scale=1.0" />
                <title>Document</title>
                <style>
                  h1 {
                    color: brown;
                  }
                </style>
              </head>
              <body>
                <h2>Product payment :</h2>
                <ul style="list-style-type:none;">
                  <li>Name : ${data.product.name}</li>
                  <li>Total payment: ${convertRupiah.convert(data.price)}</li>
                  <li>Status : <b>${status}</b></li>
                </ul>  
              </body>
            </html>`,
  };

  if (data.status != status) {
    transporter.sendMail(mailOptions, (err, info) => {
      if (err) throw err;
      console.log("Email sent: " + info.response);

      return res.send({
        status: "Success",
        message: info.response,
      });
    });
  }
};
```



