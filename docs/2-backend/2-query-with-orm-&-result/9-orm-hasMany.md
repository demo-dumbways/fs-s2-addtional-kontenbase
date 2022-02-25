---
sidebar_position: 9
---

# 9. Relation hasMany

import useBaseUrl from '@docusaurus/useBaseUrl';

## 9.1 Models

**Method hasMany** merupakan sebuah method yang digunakan pada tabel yang berelasi dengan relasi `One to Many` (ada hubungan antara A dan B, dengan `foreignkey` didefinisikan dalam model target (B)).  Relasi **One to Many** ada ketika satu record di tabel ke-1 memiliki hubungan lebih dari satu record di tabel ke-2.

Pada rancangan database yang memiliki relasi One to Many adalah user &rarr; product

Kita akan mencoba melakukan fetching . oleh karna itu pertama kita perlu menentukan relasi `hasMany` kedalam model user.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/9-orm-sequelize/models/user.js">
Contoh code
</a>

<br />
<br />

```js title=models/user.js {12-17}
const { Model } = require("sequelize");
module.exports = (sequelize, DataTypes) => {
  class user extends Model {
    static associate(models) {
      user.hasOne(models.profile, {
        as: "profile",
        foreignKey: {
          name: "idUser",
        },
      });

      user.hasMany(models.product, {
        as: "products",
        foreignKey: {
          name: "idUser",
        },
      });
    }
  }
  user.init(
    {
      email: DataTypes.STRING,
      password: DataTypes.STRING,
      name: DataTypes.STRING,
      status: DataTypes.STRING,
    },
    {
      sequelize,
      modelName: "user",
    }
  );
  return user;
};
```

## 9.2 Controllers

Setelah menentukan relasi pada model user, maka selanjutnya kita akan melakukan proses fetching data akan kita simpan kedalam sebuah modul. Pada modul ini juga akan menangani error handling dengan menggunakan try and catch. 

```js title=controllers/user.js {25-31}
// this code continues from the previous code
exports.deleteUser = async (req, res) => {
  try {
    const { id } = req.params;

    await user.destroy({
      where: {
        id,
      },
    });

    res.send({
      status: "success",
      message: `Delete user id: ${id} finished`,
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};

exports.getUserProducts = async (req, res) => {
  try {
      
  } catch (error) {

  }
}
```

Melakukan fetching data sama saja seperti proses fecthing sebelumnya, yakni bisa menggunakan metode `findAll()`. Pada proses melakukan fetching, kita bisa mengirimkan `parameter` berupa `object`. Parameter yang dikirimkan dapat berupa sebuah kondisi field - field yang tidak ingin kita fetching dan tentunya adalah `model yang akan direlasikan` yakni model `product`. 

```js title=controllers/user.js {4-12}
//  this code continues from the above code
exports.getUserProducts = async (req, res) => {
  try {
    const data = await user.findAll({
      include: {
        model: product,
        as: "products"
      },
      attributes: {
        exclude: ['createdAt', 'updatedAt']
      }
    })      
  } catch (error) {

  }
}
```

Selanjutnya yang akan kita lakukan adalah mengirimkan response ketika data berhasil dimasukkan kedalam database ataupun gagal. Response ketika sukses akan kita letakkan kedalam bagian `try`, sedangkan ketika gagal akan kita masukkan kedalam bagian `catch`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/9-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/user.js {14-17,19-22}
//  this code continues from the above code
exports.getUserProducts = async (req, res) => {
  try {
    const data = await user.findAll({
      include: {
        model: product,
        as: "products"
      },
      attributes: {
        exclude: ['createdAt', 'updatedAt']
      }
    })

    res.send({
      status: "success",
      data
    });      
  } catch (error) {
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
}
```

## 9.3 Routes

Hal terakhir yang perlu kita lakukan adalah menyedikan route API untuk menangani proses fetching data user product

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/9-orm-sequelize/src/routes/index.js">
Contoh code
</a>

<br />
<br />

```js {11,26} title=routes/index.js
const express = require('express')

const router = express.Router()

const {
    addUsers,
    getUsers,
    getUser,
    updateUser,
    deleteUser,
    getUserProducts
} = require('../controllers/user')

const { getProducts, addProduct } = require('../controllers/product')


router.post('/user', addUser)
router.get('/users', getUsers)
router.get('/user/:id', getUser)
router.patch('/user/:id', updateUser)
router.delete('/user/:id', deleteUser)

router.get('/products', getProducts)
router.post('/product', addProduct)

router.get('/user-products', getUserProducts)

module.exports = router
```

## 9.4 Penggunaan

Cara mengambil data menggunakan `Postman` sebagai berikut:

- Buat request baru, yang bernama `user-products`
- Gunakan HTTP Method: `GET`
- Gunakan endpoint: `/user-products
- Contoh endpoint

  ```
  https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user-products
  ```
- Silakan tekan tombol `Send` 
        