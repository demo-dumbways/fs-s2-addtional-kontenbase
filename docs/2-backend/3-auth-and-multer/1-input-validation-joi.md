---
sidebar_position: 1
---

# 1. Input Validation Joi

import useBaseUrl from '@docusaurus/useBaseUrl';

**Joi** merupakan sebuah package validation untuk membantu kita menghandle sebuah form input, untuk mencegah user memasukan input yang tidak sesuai dengan kriteria yang ditentukan.

Sebelumnya kita install terlebih dahulu dengan perintah.

```shell
npm install joi
```

Selanjutnya import joi pada component yang ingin menggunakan handle joi seperti berikut:
```js
const Joi = require("joi");
```

Dengan package joi kita bisa membuat aturan inputan yang harus di inputkan sesuai dengan yang kita buat, seperti type data, minimal inputan dan inputan yang harus wajib diisi.
```js
  const schema = Joi.object({
    name: Joi.string().min(5).required(),
    email: Joi.string().email().min(6).required(),
    password: Joi.string().min(6).required(),
  });
```

Jika inputan yang diinputkan tidak sesuai dengan yang kita buat, maka kita tampilkan error pada response agar yang diinputkan sesuai dengan aturan yang kita buat sebelumnya.
```js
  const { error } = schema.validate(req.body);

  if (error)
    return res.status(400).send({
      error: {
        message: error.details[0].message,
      },
    });
```

Selanjutnya kita akan mencoba implementasi Joi pada controller login dan register, berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-expressjs-fundamental/index.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/auth.js {3,6-19,45-57}
const { user } = require("../../models");

const Joi = require("joi");

exports.register = async (req, res) => {
  const schema = Joi.object({
    name: Joi.string().min(5).required(),
    email: Joi.string().email().min(6).required(),
    password: Joi.string().min(6).required(),
  });

  const { error } = schema.validate(req.body);

  if (error)
    return res.status(400).send({
      error: {
        message: error.details[0].message,
      },
    });

  try {
    const newUser = await user.create({
      name: req.body.name,
      email: req.body.email,
      password: req.body.password,
    });

    res.status(200).send({
      status: "success...",
      data: {
        name: newUser.name,
        email: newUser.email,
      },
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      status: "failed",
      message: "Server Error",
    });
  }
};

exports.login = async (req, res) => {
  const schema = Joi.object({
    email: Joi.string().email().min(6).required(),
    password: Joi.string().min(6).required(),
  });

  const { error } = schema.validate(req.body);

  if (error)
    return res.status(400).send({
      error: {
        message: error.details[0].message,
      },
    });

  try {
    const userExist = await user.findOne({
      where: {
        email: req.body.email,
      },
      attributes: {
        exclude: ["createdAt", "updatedAt"],
      },
    });

    if (userExist.password !== req.body.password) {
      return res.status(400).send({
        status: "failed",
        message: "credential is invalid",
      });
    }
    res.status(200).send({
      status: "success...",
      data: {
        name: userExist.name,
        email: userExist.email,
      },
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      status: "failed",
      message: "Server Error",
    });
  }
};
```

Selanjutnya import controller dan tambahkan route login dan register

```jsx title=routes/index.js {18,32-33}
const express = require("express");

const router = express.Router();

const {
  addUsers,
  getUsers,
  getUser,
  updateUser,
  deleteUser,
} = require("../controllers/user");
const { getProduct, addProduct } = require("../controllers/product");
const {
  getTransactions,
  addTransaction,
} = require("../controllers/transaction");

const { register, login } = require("../controllers/auth");

router.post("/user", addUsers);
router.get("/users", getUsers);
router.get("/user/:id", getUser);
router.patch("/user/:id", updateUser);
router.delete("/user/:id", deleteUser);

router.get("/products", getProduct);
router.post("/product", addProduct);

router.get("/transactions", getTransactions);
router.post("/transaction", addTransaction);

router.post("/register", register);
router.post("/login", login);

module.exports = router;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
