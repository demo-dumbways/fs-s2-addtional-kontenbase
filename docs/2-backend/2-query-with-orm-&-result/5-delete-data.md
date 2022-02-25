---
sidebar_position: 5
---

# 5. Delete Data 

import useBaseUrl from '@docusaurus/useBaseUrl';

Melakukan proses delete data menggunakan ORM dapat menggunakan metode `Model.destroy()`. **Model.destroy** akan menghapus baris data pada tabel sesuai kondisi yang diberikan

Sama halnya seperti proses update data sebelumnya, proses kali ini juga akan kita simpan kedalam sebuah modul yang terdapat proses error handlingnya.

```js {26-33} title=user.js
// this code continues from the previous code
exports.updateUser = async (req, res) => {
    try {
      const { id } = req.params
      const newdata = req.body

      await user.update(newdata, {
        where: {
          id
        }
      })

      res.send({
        status: 'success',
        message: `Update user id: ${id} finished`,
        data: newdata
      })
    } catch (error) {
      res.send({
        status: 'failed',
        message: 'Server Error'
      })
    }
}

exports.deleteUser = async (req, res) => {
    try {
        
    } catch (error) {

    }
}
```

Sebelum melakukan proses delete, maka kita membutuhkan `id` dari data yang akan didelete. **Id** akan kita kirimkan melalui `query string`, sehingga untuk mendapatkannya bersumber dari `req.params`. 

```js {4} title=user.js
// this code continues from the above code
exports.deleteUser = async (req, res) => {
    try {
      const { id } = req.params
    } catch (error) {

    }
}
```

Pada proses delete data, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan tentu berupa id baris data yang dilakukan delete.

```js {6-10} title=user.js
// this code continues from the above code
exports.deleteUser = async (req, res) => {
    try {
      const { id } = req.params

      await user.destroy({
        where: {
          id
        }
      })
    } catch (error) {

    }
}
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil di delete ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/5-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js {12-16,18-22} title=user.js
// this code continues from the above code
exports.deleteUser = async (req, res) => {
    try {
      const { id } = req.params

      await user.destroy({
        where: {
          id
        }
      })

      res.send({
        status: 'success',
        message: `Delete user id: ${id} finished`,
        data: newdata
      })
    } catch (error) {
      res.send({
        status: 'failed',
        message: 'Server Error'
      })
    }
}
```

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses delete data, agar nantinya pengguna bisa menghapus data pada tabel user sesuai id yang dikirimkan.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/5-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js {10,17} title=routes/index.js
const express = require('express')

const router = express.Router()

const {
    addUsers,
    getUsers,
    getUser,
    updateUser,
    deleteUser
} = require('../controllers/user')

router.post('/user', addUser)
router.get('/users', getUsers)
router.get('/user/:id', getUser)
router.patch('/user/:id', updateUser)
router.delete('/user/:id', deleteUser)

module.exports = router
```

Berikut contoh endpoint yang dapat Anda gunakan untuk melakukan proses delete data:

```
https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user/1
```