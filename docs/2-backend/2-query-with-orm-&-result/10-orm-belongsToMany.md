---
sidebar_position: 10
---

# 10. Relation belongsToMany

import useBaseUrl from '@docusaurus/useBaseUrl';

## 10.1 Models

**Method belongsToMany** merupakan sebuah method yang digunakan pada tabel yang berelasi dengan relasi `Many to Many`.  Relasi **Many to Many** ada ketika satu record di tabel ke-1 memiliki hubungan lebih dari satu record di tabel ke-2, dan dengan cara yang sama, kita dapat mengatakan bahwa satu record di tabel ke-2 terkait dengan lebih dari satu record di tabel ke-1.

Pada rancangan database yang memiliki relasi Many to Many adalah product &rarr; category. Sehingga kita membutuhkan satu tabel untuk menjadi `jembatan` yang menyimpan `foreignkey` untuk dua tabel tersebut. Di sini, tabel `jembatan` kami adalah `productCategory`. Mari kita definisikan Many to Many menggunakan metode `ManyToMany()` pada model product dan category.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/10-orm-sequelize/models/product.js">
Contoh code
</a>

<br />
<br />

```js title=models/product.js {12-19}
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

      product.belongsToMany(models.category, {
        as: "categories",
        through: {
          model: "productCategory",
          as: "bridge",
        },
        foreignKey: "idProduct",
      });
    }
  }
  // continuation code is the same as in the template
};
```

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/7-orm-sequelize/models/category.js">
Contoh code
</a>

<br />
<br />

```js title=models/category.js {5-12}
const { Model } = require("sequelize");
module.exports = (sequelize, DataTypes) => {
  class category extends Model {
    static associate(models) {
      category.belongsToMany(models.product, {
        as: "products",
        through: {
          model: "productCategory",
          as: "bridge",
        },
        foreignKey: "idCategory",
      });
    }
  }
  // continuation code is the same as in the template
};

```

## 10.2 Controllers

Setelah menentukan relasi pada model product dan categiry, maka selanjutnya kita akan melakukan proses untuk melakukan fetching data category product. Pada bagian sebelumnya kita telah membuat proses fetching product, maka kali ini kita cukup menambahkan proses `fetching multitable` yakni table product dan category. Melakukan fethcing multitable make kita perlu menjadikan properti `include` menyimpan data berupa `array of object`

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/8-orm-sequelize/src/controllers/product.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/product.js {6,14-26}
const { product, user } = require('../../models')

exports.getProducts = async (req, res) => {
  try {
    const data = await product.findAll({
      include: [
        {
          model: user,
          as: 'user',
          attributes: {
            exclude: ['createdAt', 'updatedAt', 'password']
          }
        },
        {
          model: category,
          as: "categories",
          through: {
            model: productCategory,
            as: "bridge",
            attributes: [],
          },
          attributes: {
            exclude: ["createdAt", "updatedAt"],
          },
        },
      ]
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
// continuation code is the same as in the template
```

## 10.3 Routes

Routes yang digunakan untuk melakukan fetching data product beserta category nya masih sama dengan section sebelumnya, yakni 

```
router.get('/products', getProducts)
```

## 10.4 Penggunaan

Cara mengambil data menggunakan `Postman` sebagai berikut:

- Gunakan HTTP Method: `GET`
- Gunakan endpoint: `/products` 
- Contoh endpoint :

  ```
 https://ebook-code-results-stage-2-be.herokuapp.com/orm/api/v1/products
  ```

- Tekan tombol `Send` dan pastikan response yang Anda terima sesuai dengan data yang tersimpan pada tabel `product` dan `category`
        