---
sidebar_position: 7
---

# 7. Relation BelongsTo

import useBaseUrl from '@docusaurus/useBaseUrl';

**Method belongsTo** merupakan sebuah method yang digunakan pada tabel yang berelasi dengan relasi `One to One`.  Relasi **One to One** ada ketika satu record di tabel ke-1 memiliki hubungan dengan hanya satu record di tabel ke-2, dan dengan cara yang sama, kita dapat mengatakan bahwa satu record di tabel ke-2 terkait dengan hanya satu record di tabel ke-1.

Pada rancangan database yang memiliki relaso One to One adalah
- profile -> user
- product -> user
- transaction -> user

Kita akan mencoba melakukan fetching dan insert data pada `Tabel Transaction`. oleh karna itu pertama kita perlu menentukan relasi `belongsTo` kedalam model - model yang saling berkaitan yakni product dan transaction.

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

```js title=models/transaction.js {5-22}
const { Model } = require("sequelize");
module.exports = (sequelize, DataTypes) => {
  class transaction extends Model {
    static associate(models) {
      transaction.belongsTo(models.product, {
        as: 'product',
        foreignKey: {
          name: 'idProduct'
        }
      }),
      transaction.belongsTo(models.user, {
        as: 'buyer',
        foreignKey: {
          name: 'idBuyer'
        }
      }),
      transaction.belongsTo(models.user, {
        as: 'seller',
        foreignKey: {
          name: 'idSeller'
        }
      })
    }
    // continuation code is the same as in the template
  }
};
```

Setelah menentukan relasi pada setiap model, maka selanjutnya kita akan melakukan proses untuk melakuakn fetching data product. Pertama kita akan melakukan import model - model yang nantinya akan kita gunakan yakni model product dan user.

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



