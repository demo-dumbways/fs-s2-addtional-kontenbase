---
sidebar_position: 3
---

# 3. Fetching Multiple Data

import useBaseUrl from '@docusaurus/useBaseUrl';

Melakukan proses fetching multiple data menggunakan ORM dapat menggunakan metode `Model.findAll()`. **Model.findAll** merupakan sebuah metode yang mengembalikan semua baris data dari sebuah tabel.

Sama halnya seperti proses entri data sebelumnya, proses kali ini juga akan kita simpan kedalam sebuah modul yang terdapat proses error handlingnya.

```js {20-26} title=user.js
const { user } = require("../../models");

exports.addUser = async (req, res) => {
  try {
    const data = req.body;
    const createdData = await user.create(data);

    res.send({
      status: "success",
      data: createdData,
    });
  } catch (error) {
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};

exports.getUsers = async (req, res) => {
  try {
  } catch (error) {}
};
```

Proses melakukan fetching, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan dapat berupa sebuah kondisi field - field yang tidak ingin kita fetching.

```js {4-8} title=user.js
// this code continues from the above code
exports.getUsers = async (req, res) => {
  try {
    const users = await user.findAll({
      attributes: {
        exclude: ["password", "createdAt", "updatedAt"],
      },
    });
  } catch (error) {}
};
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil difetching ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/2-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js {10-15,17-20} title=user.js
// this code continues from the above code
exports.getUsers = async (req, res) => {
  try {
    const users = await user.findAll({
      attributes: {
        exclude: ["password", "createdAt", "updatedAt"],
      },
    });

    res.send({
      status: "success",
      data: {
        users,
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

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses fetching multiple data, agar nantinya pengguna bisa melihat seluruh baris data didalam table user.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/2-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js {7,11} title=routes/index.js
const express = require("express");

const router = express.Router();

const { addUsers, getUsers } = require("../controllers/user");

router.post("/user", addUser);
router.get("/users", getUsers);

module.exports = router;
```

Berikut contoh endpoint yang dapat Anda gunakan untuk melakukan proses fetching multiple data:

```
https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/users
```
