---
sidebar_position: 4
---

# 4. Group Routes

import useBaseUrl from '@docusaurus/useBaseUrl';

**Group Routes** adalah ...

### 4.1 Persiapan Struktur File

```text {3-7}
express-api-app
 ┣ node_modules
 ┣ src
 ┃ ┣ controllers
 ┃ ┃ ┗ todo.js
 ┃ ┗ routes
 ┃ ┃ ┗ index.js
 ┣ .gitignore
 ┣ index.js
 ┣ package-lock.json
 ┣ package.json
 ┗ vercel.json
```

### 4.2 Controllers

Kenapa harus ada controller ...

```js title=todo.js
let todos = [
  {
    id: 1,
    title: 'Cuci tangan',
    isDone: true,
  },
  {
    id: 2,
    title: 'Jaga jarak',
    isDone: false,
  },
  {
    id: 3,
    title: 'Gunakan maskaer',
    idDone: true,
  },
];

exports.getTodos = async (req, res) => {
  try {
    res.send({
      status: 'success',
      data: {
        todos,
      },
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: 'failed',
      message: 'Server Error',
    });
  }
};

exports.getTodo = async (req, res) => {
  try {
    const id = req.params.id;

    const data = todos.find((todo) => todo.id == id);
    res.send({
      status: 'success',
      data: {
        todo: data,
      },
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: 'failed',
      message: 'Server Error',
    });
  }
};

exports.addTodo = async (req, res) => {
  try {
    const data = req.body;
    todos.push(data);
    res.send({
      status: 'success',
      data: {
        todos,
      },
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: 'failed',
      message: 'Server Error',
    });
  }
};

exports.updateTodo = async (req, res) => {
  try {
    const { id } = req.params;

    todos = todos.map((todo) => {
      if (todo.id == id) {
        return req.body;
      } else {
        return todo;
      }
    });

    const data = todos.find((todo) => todo.id == id);

    res.send({
      status: 'success',
      data: {
        todo: data,
      },
    });
  } catch (error) {
    console.log(error);
    res.send({
      status: 'failed',
      message: 'Server Error',
    });
  }
};

exports.deleteTodo = async (req, res) => {
  try {
    const { id } = req.params;
    todos = todos.filter((todo) => todo.id != id);

    res.send({
      status: 'success',
      data: {
        todos,
      },
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

### 4.3 Routes

Fungsi routes file ...

```js title=index.js
const express = require('express');

const router = express.Router();

// Controller
const {
  getTodos,
  getTodo,
  addTodo,
  updateTodo,
  deleteTodo,
} = require('../controllers/todo');

// Route
router.get('/todos', getTodos);
router.get('/todo/:id', getTodo);
router.post('/todo', addTodo);
router.patch('/todo/:id', updateTodo);
router.delete('/todo/:id', deleteTodo);

module.exports = router;
```

### 4.4 Root file

Root file terdapat ...

```js title=index.js
const express = require('express');

// Get routes to the variabel
const router = require('./src/routes');

const app = express();

const port = 5000;

app.use(express.json());

// Add endpoint grouping and router
app.use('/api/v1/', router);

app.listen(port, () => console.log(`Listening on port ${port}!`));
```

### 4.5 Akses API Group route dengan Postman

Cara akses API Group route ...

```link title=baseUrl
https://ebook-code-results-stage-2-backend-git-4-e-a80eda-demo-dumbways.vercel.app
```

Berikut list route yang telah dibuat ...

| Method | Group     | Route       |
| ------ | --------- | ----------- |
| GET    | `/api/v1` | `/todos`    |
| GET    | `/api/v1` | `/todo/:id` |
| POST   | `/api/v1` | `/todo`     |
| PATCH  | `/api/v1` | `/todo/:id` |
| DELETE | `/api/v1` | `/todo/:id` |
