---
sidebar_position: 5
---

# 5. Update Data

import useBaseUrl from '@docusaurus/useBaseUrl';

Melakukan proses update data menggunakan ORM dapat menggunakan metode `Model.update()`. **Model.update** hanya akan melakukan perubahan pada field - field yang datanya diisikan oleh pengguna pada formulir update.

Sama halnya seperti proses fetching data sebelumnya, proses kali ini juga akan kita simpan kedalam sebuah modul yang terdapat proses error handlingnya.

```js {27-33} title=user.js
// this code continues from the previous code
exports.getUser = async (req, res) => {
  try {
    const user = await user.findOne({
      where: {
        id: id,
      },
      attributes: {
        exclude: ["password", "createdAt", "updatedAt"],
      },
    });

    res.send({
      status: "success",
      data: {
        user,
      },
    });
  } catch (error) {
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};

exports.updateUser = async (req, res) => {
  try {
  } catch (error) {}
};
```

Sebelum melakukan proses update, maka kita membutuhkan `id` dari data yang akan diupdate. **Id** akan kita kirimkan melalui `query string`, sehingga untuk mendapatkannya bersumber dari `req.params`. Selain id, tentunya kita membutuhkan data yang akan menjadi data terbaru dari baris data yang akan diupate.

```js {4-5} title=user.js
// this code continues from the above code
exports.updateUser = async (req, res) => {
  try {
    const { id } = req.params;
    const newdata = req.body;
  } catch (error) {}
};
```

Pada proses update data, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan tentu berupa data update serta id baris data yang dilakukan update.

```js {7-11} title=user.js
// this code continues from the above code
exports.updateUser = async (req, res) => {
  try {
    const { id } = req.params;
    const newdata = req.body;

    await user.update(newdata, {
      where: {
        id,
      },
    });
  } catch (error) {}
};
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil diupdate ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/4-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js {13-17,19-22} title=user.js
// this code continues from the above code
exports.updateUser = async (req, res) => {
  try {
    const { id } = req.params;
    const newdata = req.body;

    await user.update(newdata, {
      where: {
        id,
      },
    });

    res.send({
      status: "success",
      message: `Update user id: ${id} finished`,
      data: newdata,
    });
  } catch (error) {
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};
```

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses update data, agar nantinya pengguna bisa melakukan update data pada tabel user sesuai id yang dikirimkan.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/4-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js {9,15} title=routes/index.js
const express = require("express");

const router = express.Router();

const {
  addUsers,
  getUsers,
  getUser,
  updateUser,
} = require("../controllers/user");

router.post("/user", addUser);
router.get("/users", getUsers);
router.get("/user/:id", getUser);
router.patch("/user/:id", updateUser);

module.exports = router;
```

Berikut contoh endpoint yang dapat Anda gunakan untuk melakukan proses update data:

```
https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user/1
```
