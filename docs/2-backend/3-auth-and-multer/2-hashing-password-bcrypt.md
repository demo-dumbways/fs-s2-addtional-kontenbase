---
sidebar_position: 2
---

# 2. Hashing Password Bcrypt

import useBaseUrl from '@docusaurus/useBaseUrl';

**Bcrypt** merupakan sebuah package untuk mengamankan sebuah password dari serangan rainbow table dimana nantinya password tersebut akan di enkripsi dengan menggunakan salt, enkripsi akan menjamin data tetap aman meskipun berada di tangan orang lain.

contoh password belum di enkrip
`123456`

contoh password sudah di enkrip
`$2a$10$BLMmNP5ERgFYq3HZEH2b9.2uZG6qYrUbDbPx8GGluNGWbPz7/Oh72`

Sebelumnya kita install terlebih dahulu dengan perintah.

```shell
npm install bcrypt
```

Selanjutnya import bcrypt yang diinstal pada controller register
```js title=controllers/auth.js 
const bcrypt = require("bcrypt");
```

Sebelumnya kita perlu tahu, bahwa kita harus memasukan round ketika kita ingin membuat enkrip pada password, rounds ini adalah jumlah enkrip atau hash yang akan dilakukan enkrip perdetiknya. 

```js
rounds=8 : ~40 hashes/sec
rounds=9 : ~20 hashes/sec
rounds=10: ~10 hashes/sec
rounds=11: ~5  hashes/sec
rounds=12: 2-3 hashes/sec
rounds=13: ~1 sec/hash
rounds=14: ~1.5 sec/hash
rounds=15: ~3 sec/hash
rounds=25: ~1 hour/hash
rounds=31: 2-3 days/hash
```

Selanjutnya kita akan membuat salt untuk password kita adalah rounds 10, yang nantinya password akan di enkrip 10 hashes perdetiknya, dan selanjutnya kita buat variabel hashedPassword untuk menampung data req.body.password atau yang diinpukan oleh user dan diganti dengan password yang sudah di enkrip. 
```js title=controllers/auth.js 
const salt = await bcrypt.genSalt(10);
const hashedPassword = await bcrypt.hash(req.body.password, salt);
```

Selanjutnyya kita kirimkan password yang sudah di enkrip pada method create, agar yang masuk kedalam database password yang sudah terenkripsi.
```js title=controllers/auth.js {4}
const newUser = await user.create({
  name: req.body.name,
  email: req.body.email,
  password: hashedPassword,
});
```

Selanjutnya kita implementasikan, berikut contoh codenya:
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/2-auth-and-multer/src/controllers/auth.js">
Contoh code
</a>

<br />
<br />

```js title=src/controllers/auth.js {4,23-24,29,73-79} 
const { user } = require("../../models");

const Joi = require("joi");
const bcrypt = require("bcrypt");

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
    const salt = await bcrypt.genSalt(10);
    const hashedPassword = await bcrypt.hash(req.body.password, salt);

    const newUser = await user.create({
      name: req.body.name,
      email: req.body.email,
      password: hashedPassword,
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

    const isValid = await bcrypt.compare(req.body.password, userExist.password);

    if (!isValid) {
      return res.status(400).send({
        status: "failed",
        message: "password not match",
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

## 2.1 Penggunaan

Cara menambah data menggunakan `Postman` sebagai berikut:

- Buat sebuah request baru, yang bernama `register`
- Gunakan HTTP Method: `POST`
- Gunakan endpoint: `/register`
  ```
  http://localhost:5000/api/v1/register
  ```
- Pilih `Body` &rarr; `raw` &rarr; ubah `Text` menjadi `JSON`
- Ketik pada bagian `Request Body` seperti berikut:

  ```json title=Request
  {
    "name": "user 2",
    "email": "user2@mail.com",
    "password": "123456",
  }
  ```

- Silakan tekan tombol `Send`, kemudian Anda akan mendapatkan `Response` seperti berikut:

  ```json title=Response
  {
    "status": "success",
    "data": {
      "name": "user 1",
      "email": "user1@mail.com",
    }
  }
  ```
## 2.2 Practice

Sesuaikan code Anda dengan contoh code berikut:
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/tree/2-auth-and-multer/src">
Contoh code
</a>

<br />
<br />

Berikut contoh endpoint yang dapat Anda gunakan:

```
https://ebook-code-results-stage-2-be.herokuapp.com/auth-and-multer/api/v1/register
```
