---
sidebar_position: 7
---

# 7. Relation belongsTo

import useBaseUrl from '@docusaurus/useBaseUrl';

## 7.1 Models

**Method belongsTo** merupakan sebuah method yang digunakan pada tabel yang berelasi dengan relasi `One to One` (ada hubungan antara A dan B, dengan `foreignkey` didefinisikan dalam model target (A)).  Relasi **One to One** ada ketika satu record di tabel ke-1 memiliki hubungan dengan hanya satu record di tabel ke-2, dan dengan cara yang sama, kita dapat mengatakan bahwa satu record di tabel ke-2 terkait dengan hanya satu record di tabel ke-1.

Pada rancangan database yang memiliki relasi One to One adalah
- profile &rarr; user
- product &rarr; user
- transaction &rarr; user

Kita akan mencoba melakukan fetching dan insert data product. oleh karna itu pertama kita perlu menentukan relasi `belongsTo` kedalam model - model yang saling berkaitan yakni product.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/tree/5-expressjs-fundamental/src">
Contoh code
</a>

<br />
<br />

```js title=models/product.js {5-9}
const { Model } = require("sequelize");
module.exports = (sequelize, DataTypes) => {
  class product extends Model {
    static associate(models) {
      product.belongsTo(models.user, {
        as: "user",
        foreignKey: {
          name: "idUser",
        },
      });
    }
  }
  // continuation code is the same as in the template
};
```

## 7.2 Controllers

### 7.2.1 getProducts
Setelah menentukan relasi pada setiap model, maka selanjutnya kita akan melakukan proses untuk melakukan fetching data product. Pertama kita akan melakukan import model - model yang nantinya akan kita gunakan yakni model product dan user.

```js title=controllers/product.js
const { product, user } = require('../../models')
```

Selanjutnya melakukan proses fetching data akan kita simpan kedalam sebuah `modul`. Pada modul ini juga akan menangani `error handling` dengan menggunakan `try and catch`.

```js title=controllers/product.js {3-9}
const { product, user } = require('../../models')

exports.getProducts = async (req, res) => {
  try {

  } catch (error) {

  }
};
```

Melakukan fetching data sama saja seperti proses fecthing sebelumnya, yakni bisa menggunakan metode `findAll()` ataupun `findOne()`. Pada proses melakukan fetching, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan dapat berupa sebuah kondisi field - field yang tidak ingin kita fetching dan tentunya adalah `model yang akan direlasikan` yakni model `user`. 

```js title=controllers/product.js {5-16}
const { product, user } = require('../../models')

exports.getProducts = async (req, res) => {
  try {
    const data = await product.findAll({
      include: {
        model: user,
        as: 'user',
        attributes: {
          exclude: ['createdAt', 'updatedAt', 'password']
        }
      },
      attributes: {
        exclude: ['createdAt', 'updatedAt', 'idUser']
      }
    })
  } catch (error) {

  }
};
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil difetching ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

```js title=controllers/product.js {18-21,23-26}
const { product, user } = require('../../models')

exports.getProducts = async (req, res) => {
  try {
    const data = await product.findAll({
      include: {
        model: user,
        as: 'user',
        attributes: {
          exclude: ['createdAt', 'updatedAt', 'password']
        }
      },
      attributes: {
        exclude: ['createdAt', 'updatedAt', 'idUser']
      }
    })

    res.send({
      status: 'success...',
      data
    })
  } catch (error) {
    res.send({
      status: 'failed',
      message: 'Server Error'
    })
  }
};
```

### 7.2.2 addProduct

Selanjutnya melakukan proses insert data akan kita simpan kedalam sebuah `modul`. Pada modul ini juga akan menangani `error handling` dengan menggunakan `try and catch`.

```js title=controllers/product.js {2-7}
//  this code continues from the above code
exports.addProduct = async (req, res) => {
  try {

  } catch (error) {
    
  }
```

Pada bagian try, kita akan melakukan proses entri data kedalam database. Diawali dengan menampung data inputan formulir kedalam variabel. Variabel yang telah berisikan data inputan, selanjutnya akan kita entri kedalam database menggunakan method create()

```js title=controllers/product.js {3-4}
exports.addProduct = async (req, res) => {
  try {
    const data = req.body
    await product.create(data)
  } catch (error) {
    
  }
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil dimasukkan kedalam database ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/tree/5-expressjs-fundamental/src">
Contoh code
</a>

<br />
<br />

```js title=controllers/product.js {6-9,11-14}
exports.addProduct = async (req, res) => {
  try {
    const data = req.body
    await product.create(data)

    res.send({
      status: 'success...',
      data
    })
  } catch (error) {
    res.send({
      status: 'failed',
      message: 'Server Error'
    })
  }
```

## 7.3 Routes

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses fetching dan insert data product

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/tree/5-expressjs-fundamental/src">
Contoh code
</a>

<br />
<br />

```js {7-10,19-20} title=routes/index.js
const express = require('express')

const router = express.Router()

const { addUsers, getUsers, getUser, updateUser, deleteUser } = require("../controllers/user");

const { 
    getProducts, 
    addProduct 
} = require('../controllers/product')


router.post('/user', addUser)
router.get('/users', getUsers)
router.get('/user', getUser)
router.patch('/user/:id', updateUser)
router.delete('/user/:id', deleteUser)

router.get('/products', getProducts)
router.post('/product', addProduct)

module.exports = router
```

## 7.4 Penggunaan

Cara mengambil data menggunakan `Postman` sebagai berikut:

- Buat dua request baru, yang bernama `products` dan `product`
- Gunakan HTTP Method: `GET` dan `POST`
- Gunakan endpoint: `/products` dan `/add-product`
- Contoh endpoint :

  ```
  http://localhost:5000/api/v1/products
  ```
  ```
  http://localhost:5000/api/v1/add-product
  ```
- Tekan tombol `Send` dan pastikan response yang Anda terima sesuai dengan data yang tersimpan pada tabel `product`

- Proses menambahkan product, maka tambahkan proses berikut

    - Pilih `Body` &rarr; `form-data` &rarr; 
    - Ketik pada bagian `Key` dan `value` seperti berikut:

        | KEY       | VALUE                  |
        | --------- | ---------------------- |
        | name      | kemeja kerah           |
        | desc      | kemeja outfit kekinian |
        | price     | 120000                 | 
        | image     | kemeja.png             |
        | qty       | 130                    |
        | idUser    | 7                      |
        | category  | null                   |

    - Silakan tekan tombol `Send`, kemudian Anda akan mendapatkan `Response` seperti berikut:

    ```json title=Response
    {
        "status": "success"
    }
    ```
        