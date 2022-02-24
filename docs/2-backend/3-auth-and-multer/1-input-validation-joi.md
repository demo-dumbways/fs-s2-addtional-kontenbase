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

### 1.1 Register

Selanjutnya kita implementasikan pada fungsi controller register, seperti berikut:

- import package joi yang sudah diinstal sebelumnya

```js title=src/controllers/auth.js
const Joi = require("joi");
```

- Buatlah handle form input register dan buat kondisi ketika yang diinputkan tidak sesuai dengan yang dibuat maka akan menampilkan error.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-auth-and-multer/src/controllers/auth.js">
Contoh code
</a>

<br />
<br />

```js title=src/controllers/auth.js
exports.register = async (req, res) => {
  const schema = Joi.object({
    name: Joi.string().min(5).required(),
    email: Joi.string().email().min(6).required(),
    password: Joi.string().min(6).required(),
  });

  if (error)
    return res.status(400).send({
      error: {
        message: error.details[0].message,
      },
    });

  try {
  } catch (error) {}
};
```

Selanjutnya Pada bagian `try`, kita akan melakukan proses entri data kedalam database. dan ketika proses memasukan data kedalam database gagal kita akan masukan ke `catch`

```js js title=src/controllers/auth.js {21-40}
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
```

### 1.2 Login

- Buatlah handle form input login dan buat kondisi ketika yang diinputkan tidak sesuai dengan yang dibuat maka akan menampilkan error. Lakukan langkah pengerjaan yang sama seperti pada saat membuat fungsi pada controller register.

```js title=src/controllers/auth.js
// this code continues from the previous code
exports.register = async (req, res) => {
  const schema = Joi.object({
    email: Joi.string().email().min(6).required(),
    password: Joi.string().min(6).required(),
  });

  if (error)
    return res.status(400).send({
      error: {
        message: error.details[0].message,
      },
    });

  try {
  } catch (error) {}
};
```

```js title=src/controllers/auth.js {17-46}
// this code continues from the previous code
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

Selanjutnya import controller dan tambahkan route login dan register pada file `src/routes/index.js`

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-auth-and-multer/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js title=src/routes/index.js {18,32-33}
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

<!-- <img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br /> -->

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
