---
sidebar_position: 3
---

# 3. Fetching Single Data 

import useBaseUrl from '@docusaurus/useBaseUrl';

Melakukan proses fetching single data menggunakan ORM dapat menggunakan metode `Model.findOne()`. **Model.findOne** mengembalikan satu baris data yang sesuai dengan kondisi yang diberikan.

Sama halnya seperti proses entri data sebelumnya, proses kali ini juga akan kita simpan kedalam sebuah modul yang terdapat proses error handlingnya.

```js {24-30} title=user.js
// this code continues from the previous code
exports.getUsers = async (req, res) => {
    try {
      const users = await user.findAll({
        attributes: {
          exclude: ['password', 'createdAt', 'updatedAt']
        }
      })

      res.send({
        status: 'success',
        data: {
          users
        }
      })
    } catch (error) {
      res.send({
        status: 'failed',
        message: 'Server Error'
      })
    }
}

exports.getUser = async (req, res) => {
    try {
        
    } catch (error) {

    }
}
```

Proses melakukan fetching, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan tentu berupa kondisi data yang akan ditampilkan. Ataupun field - field yang tidak ingin kita fetching . 

```js {4-11} title=user.js
// this code continues from the above code
exports.getUser = async (req, res) => {
    try {
      const user = await user.findOne({
        where: {
          id: id
        },
        attributes: {
          exclude: ['password', 'createdAt', 'updatedAt']
        }
      })
    } catch (error) {

    }
}
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil difetching ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/3-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js {13-18,20-23} title=user.js
// this code continues from the above code
exports.getUser = async (req, res) => {
    try {
      const user = await user.findOne({
        where: {
          id: id
        },
        attributes: {
          exclude: ['password', 'createdAt', 'updatedAt']
        }
      })

      res.send({
        status: 'success',
        data: {
          user
        }
      })
    } catch (error) {
      res.send({
        status: 'failed',
        message: 'Server Error'
      })
    }
}
```

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses fetching single data, agar nantinya pengguna bisa melihat baris data dari table user sesuai id yang dikirimkan.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/3-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js {8,13} title=routes/index.js
const express = require('express')

const router = express.Router()

const {
    addUsers,
    getUsers,
    getUser
} = require('../controllers/user')

router.post('/user', addUser)
router.get('/users', getUsers)
router.get('/user/:id', getUser)

module.exports = router
```

Berikut contoh endpoint yang dapat Anda gunakan untuk melakukan proses fetching single data:

```
https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user/1
```