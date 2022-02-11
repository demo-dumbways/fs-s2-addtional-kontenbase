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

```js {1,3} title=src/routes/index.js
const { addUsers } = require('../controllers/user');

router.post('/user', addUsers);
```

## 6.3 Penggunaan

Cara menambahkan data menggunakan `Postman` sebagai berikut:

- Buat sebuah request baru, yang bernama `user`
- Gunakan HTTP Method: `POST`
- Gunakan endpoint: `/user`
- Pilih `Body` &rarr; `raw` &rarr; ubah `Text` menjadi `JSON`
- Ketik pada bagian `Request Body` seperti berikut:

  ```json title=Request
  {
    "email": "user1@mail.com",
    "password": "123456",
    "name": "user satu",
    "status": "customer"
  }
  ```

- Silakan tekan tombol `Send`, kemudian Anda akan mendapatkan `Response` seperti berikut:

  ```json title=Response
  {
    "status": "success",
    "message": "Add user finished"
  }
  ```

- Silakan cek Database Anda, untuk memastikan data berhasil disimpan
