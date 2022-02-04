---
sidebar_position: 3
---

# 3. Routing

import useBaseUrl from '@docusaurus/useBaseUrl';

**Routing** adalah ...

**API** adalah ...

### 2.1 Express.json()

### 2.2 Membuat API

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/2-expressjs-fundamental/package.json">
Contoh code
</a>

<br />
<br />

```js title=index.js
const express = require('express');

const app = express();
const port = 5000;

app.use(express.json());

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
];

app.get('/todos', (req, res) => {
  res.send({ data: todos });
});

app.get('/todo/:id', (req, res) => {
  const id = req.params.id;

  const data = todos.find((todo) => todo.id == id);

  res.send(data);
});

app.post('/todo', (req, res) => {
  const data = req.body;
  todos.push(data);
  res.send({ data: todos });
});

app.patch('/todo/:id', (req, res) => {
  const { id } = req.params;

  todos = todos.map((todo) => {
    if (todo.id == id) {
      return req.body;
    } else {
      return todo;
    }
  });

  const data = todos.find((todo) => todo.id == id);

  res.send({ data });
});

app.delete('/todo/:id', (req, res) => {
  const { id } = req.params;
  todos = todos.filter((todo) => todo.id != id);
  res.send({ data: todos });
});

app.listen(port, () => console.log(`Listening on port ${port}!`));
```

### 2.3 Akses API dengan Postman

```link title=baseUrl
https://ebook-code-results-stage-2-backend-git-3-e-d5f17e-demo-dumbways.vercel.app
```

| Method | Route       |
| ------ | ----------- |
| GET    | `/todos`    |
| GET    | `/todo/:id` |
| POST   | `/todo`     |
| PATCH  | `/todo/:id` |
| DELETE | `/todo/:id` |
