---
sidebar_position: 8
---

# 8. Relation hasOne

import useBaseUrl from '@docusaurus/useBaseUrl';

## 8.1 Models

**Method hasOne** merupakan sebuah method yang digunakan pada tabel yang berelasi dengan relasi `One to One` (ada hubungan antara A dan B, dengan `foreignkey` didefinisikan dalam model target (B)).  Relasi **One to One** ada ketika satu record di tabel ke-1 memiliki hubungan dengan hanya satu record di tabel ke-2, dan dengan cara yang sama, kita dapat mengatakan bahwa satu record di tabel ke-2 terkait dengan hanya satu record di tabel ke-1.

Pada rancangan database yang memiliki relasi One to One adalah user &rarr; profile

Kita akan mencoba melakukan fetching dan insert data product. oleh karna itu pertama kita perlu menentukan relasi `hasOne` kedalam model user.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/8-orm-sequelize/models/user.js">
Contoh code
</a>

<br />
<br />

```js title=models/user.js {5-9}
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

## 8.2 Controllers

Setelah menentukan relasi pada model user, maka selanjutnya kita akan melakukan proses untuk melakukan fetching data user. Pada bagian sebelumnya kita telah membuat proses CRUD terkait data user, maka kali ini kita cukup menambahkan proses `fetching multitable` yakni table profile dan user.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/8-orm-sequelize/src/controllers/user.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/user.js {5-10,38-44}
// this code continues from the previous code
exports.getUsers = async (req, res) => {
    try {
      const users = await user.findAll({
        include: {
        model: profile,
        as: "profile",
        attributes: {
          exclude: ["createdAt", "updatedAt", "idUser"],
        },
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
    const { id } = req.params;

    const data = await user.findOne({
      where: {
        id,
      },
      include: {
        model: profile,
        as: "profile",
        attributes: {
          exclude: ["createdAt", "updatedAt", "idUser"],
        },
      },
      attributes: {
        exclude: ["password", "createdAt", "updatedAt"],
      },
    });

    res.send({
      status: "success",
      data: {
        user: data,
      },
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: "failed",
      message: "Server Error",
    });
  }
};
// continuation code is the same as in the template
```

## 8.3 Routes

Routes yang digunakan untuk melakukan fetching data user beserta profilenya masih sama dengan section sebelumnya, yakni 

```
router.get('/users', getUsers)
router.get('/user/:id', getUser)
```

## 8.4 Penggunaan

Cara mengambil data menggunakan `Postman` sebagai berikut:

- Buat dua request baru, yang bernama `user` dan `user by id`
- Gunakan HTTP Method: `GET`
- Gunakan endpoint: `/user` dan `/user/:id`
- Contoh endpoint pengambilan data user berdasarkan `id`:

  ```
 https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/user/1
  ```
  \*Angka `1` merupakan `id` dari `user`
- Silakan tekan tombol `Send` dan pastikan response yang Anda terima sesuai dengan data yang tersimpan pada tabel `user`
        