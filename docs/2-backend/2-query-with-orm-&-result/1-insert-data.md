---
sidebar_position: 1
---

# 1. Insert Data 

import useBaseUrl from '@docusaurus/useBaseUrl';

**Sequelize** menyediakan berbagai metode untuk melakukan proses query database. Melakukan proses insert data menggunakan ORM dapat menggunakan metode `Model.create()`. Model ini merupakan sebuah `shorthand` yang disediakan oleh sequelize sehingga memungkinkan kita untuk melakukan entri kedalam database berdasarkan data formulir.

Hal pertama yang kita lakukan adalah mengimport `model user` dengan cara melakukan `object destructuring` terhadap folder models

```js title=controllers/user.js
const { user } = require('../../models')
```

Selanjutnya kita akan membuat sebuah `modul` yang nantinya akan menangani terkait proses entri data kedalam database. Modul ini akan berjalan secara asynchronous agar bisa tetap berjalan tanpa mengganggu proses lainnya. Pada modul ini juga akan menangani `error handling` dengan menggunakan `try and catch`.

```js {3-9} title=controllers/user.js
const { user } = require('../../models')

exports.addUser = async (req, res) => {
    try {

    } catch (error) {

    }
}
```

Pada bagian `try`, kita akan melakukan proses entri data kedalam database. Diawali dengan menampung data inputan formulir kedalam variabel. Variabel yang telah berisikan data inputan, selanjutnya akan kita entri kedalam database menggunakan method `create()`

```js {5-7} title=controllers/user.js
const { user } = require('../../models')

exports.addUser = async (req, res) => {
    try {
      const data = req.body

      const createdData = await user.create(data)
    } catch (error) {

    }
}
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil dimasukkan kedalam database ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js {9-12,14-17} title=controllers/user.js
const { user } = require('../../models')

exports.addUser = async (req, res) => {
    try {
      const data = req.body

      const createdData = await user.create(data)

      res.send({
        status: 'success',
        data: createdData
      })
    } catch (error) {
      res.send({
        status: 'failed',
        message: 'Server Error'
      })
    }
}
```

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses entri data kedalam database, agar nantinya pengguna bisa melakukan penambahan data user ketika melakukan registrasi

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js title=routes/index.js
const express = require('express')

const router = express.Router()

const { addUser } = require('../controllers/user')

router.post('/user', addUser)

module.exports = router
```

Berikut contoh endpoint yang dapat Anda gunakan untuk melakukan proses insert data:

```
https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user
```
