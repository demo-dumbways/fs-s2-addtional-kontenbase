---
sidebar_position: 3
---

# 3. Authentication JWT

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum memahami apa itu JWT (JSON Web Token) baik nya memahami terlebih dahulu apa itu **Token**. **Token** adalah standar Internet yang diusulkan untuk membuat data dengan tanda tangan opsional dan/atau enkripsi opsional yang muatannya menampung JSON yang menegaskan sejumlah klaim. Token ditandatangani baik menggunakan rahasia pribadi atau kunci publik/pribadi.

**JWT** JSON Web Token atau lebih dikenal dengan JWT yang mana JWT ini adalah sebuah library yang bekerja untuk membuat sebuah token berbentuk string panjang yang berbentuk random yang berguna untuk melakukan sistem Autentikasi dan Pertukaran Informasi.

contoh token seperti berikut:

```js
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ
.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

Contoh token diatas dipisahkan dengan `titik` yang terdiri 3 bagian yaitu:

bagian pertama adalah Header: Algorithm & Token Type

```js
{
  "alg": "HS256",
  "typ": "JWT"
}
```

bagian kedua adalah Payload: DATA

```js
{
  "sub": "1234567890",
  "name": "John Doe",
  "iat": 1516239022
}
```

bagian ketiga adalah Verify Signature

```js
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),

your-256-bit-secret

) secret base64 encoded

```

Untuk menggunakan jwt kita harus install dengan perintah:

```shell
npm install jsonwebtoken
```

kemudian import jwt pada controller
```js title=controllers/auth.js 
const jwt = require("jsonwebtoken")
```

untuk mengenerate token, kita buat 2 variabel, yang pertama kita buat untuk menampung secret key dan yang kedua untuk menampung data user dan secret key yang hasil datanya akan berbentuk token.
```js title=controllers/auth.js 
const SECRET_KEY = 'rahasia'
const token = jwt.sign({id: newUser.id}, SECRET_KEY)
```

Selanjutnya kita implementasikan, berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/3-auth-and-multer/src/controllers/auth.js">
Contoh code
</a>

<br />
<br />

```js title=src/controllers/auth.js {6,36-37,90-91}
const { user } = require("../../models");

const Joi = require("joi");
const bcrypt = require("bcrypt");
//import jsonwebtoken
const jwt = require("jsonwebtoken");

exports.register = async (req, res) => {
  const schema = Joi.object({
    name: Joi.string().min(3).required(),
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
    const salt = await bcrypt.genSalt(10);
    const hashedPassword = await bcrypt.hash(req.body.password, salt);

    const newUser = await user.create({
      name: req.body.name,
      email: req.body.email,
      password: hashedPassword,
      status: "customer",
    });

    // generate token
    const SECRET_KEY = 'rahasia'
    const token = jwt.sign({id: newUser.id}, SECRET_KEY)

    res.status(200).send({
      status: "success...",
      data: {
        name: newUser.name,
        email: newUser.email,
        token,
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
    const isValid = await bcrypt.compare(req.body.password, userExist.password);

    if (!isValid) {
      return res.status(400).send({
        status: "failed",
        message: "credential is invalid",
      });
    }

    // generate token
    const SECRET_KEY = 'rahasia'
    const token = jwt.sign({id: userExist.id}, SECRET_KEY)

    res.status(200).send({
      status: "success...",
      data: {
        id: userExist.id,
        name: userExist.name,
        email: userExist.email,
        status: userExist.status,
        token,
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
Selanjutnya buat folder middlewares kemudian buat file auth.js, kemudian ketikan configurasi agar kita data memverifikasi data user ketika mengakses route kita nanti, jika user tidak memiliki token atau token yang dimasukan salah maka user tidak akan bisa mengakses route yang sudah kita buat. 

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/3-auth-and-multer/src/middlewares/auth.js">
Contoh code
</a>

<br />
<br />

```js title=src/middlewares/auth.js
const jwt = require("jsonwebtoken");

exports.auth = (req, res, next) => {
  const authHeader = req.header("Authorization");
  const token = authHeader && authHeader.split(" ")[1];
  // check if user send token via Authorization header or not
  if (!token) {
    // rejected request and send response access denied
    return res.status(401).send({ message: "Access denied!" });
  }

  try {
    // generate token
    const SECRET_KEY = 'rahasia'
    const verified = jwt.verify(token, TOKEN_KEY); //verified token
    req.user = verified;
    next(); // if token valid go to the next request
  } catch (error) {
    // if token not valid send response invalid token
    res.status(400).send({ message: "Invalid token" });
  }
};

```
Selanjutnya kita buat route atau endpoint apa saja yang membutuhkan token, disini kita akan mencontohkan pada route atau endpoint /users, jadi ketika kita ingin mengakses route users kita memerlukan token, jika tidak  memiliki token atau token yang dimasukan salah maka controller getUsers tidak di jalankan dan akan menampilkan error dari configurasi auth.js yang kita buat sebelumnya.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/3-auth-and-multer/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js title=src/routes/index.js {13,17}
const express = require('express')

const router = express.Router()

// Controller
const { addUsers, getUsers, getUser, updateUser, deleteUser } = require('../controllers/user')
const { getProduct, addProduct } = require('../controllers/product')
const { getTransactions, addTransaction } = require('../controllers/transaction')
const { register, login } = require('../controllers/auth')

// Middleware
// import middleware here
const {auth} = require('../middlewares/auth')

// Route
router.post('/user', addUsers)
router.get('/users', auth, getUsers)
router.get('/user/:id', getUser)
router.patch('/user/:id', updateUser)
router.delete('/user/:id', deleteUser)

router.get('/products', auth, getProduct)
router.post('/product', addProduct) 

router.get('/transactions', getTransactions)
router.post('/transaction', addTransaction)

router.post('/register', register)
router.post('/login', login)

module.exports = router
```

<!-- <img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br /> -->

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
