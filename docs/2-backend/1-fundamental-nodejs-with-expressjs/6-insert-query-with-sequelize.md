---
sidebar_position: 6
---

# 6. Insert Query with Sequelize

import useBaseUrl from '@docusaurus/useBaseUrl';

## 6.1 Controller

Untuk menambahkan data ke tabel yang ada didatabase, kita perlu memanggil `setup connection database`.

```js title=src/controllers/user.js
const db = require('../database/connection');
```

Lalu kita membuat sebuah controller yang menghandle proses penambahan data ke tabel seperti berikut:

```js {1-25} title=src/controllers/user.js
const db = require('../database/connection');

exports.addUsers = async (req, res) => {
  try {
    const { email, password, name, status } = req.body;

    const query = `INSERT INTO users (email,password,name,status) VALUES ('${email}','${password}','${name}','${status}')`;

    await db.sequelize.query(query);

    res.send({
      status: 'success',
      message: 'Add user finished',
      query,
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: 'failed',
      message: 'Server Error',
    });
  }
};
```

## 6.2 Route

Buat route untuk controller `addUsers` menggunakan HTTP method `post`

```js {4,6} title=src/routes/index.js
const express = require('express');
const router = express.Router();

const { addUsers } = require('../controllers/user');

router.post('/user', addUsers);

module.exports = router;
```
