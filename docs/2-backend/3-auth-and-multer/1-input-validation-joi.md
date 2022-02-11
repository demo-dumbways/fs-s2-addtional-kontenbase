---
sidebar_position: 1
---

# 1. Input Validation Joi

import useBaseUrl from '@docusaurus/useBaseUrl';

**Joi** merupakan package validation untuk menghandle sebuah form inputan, untuk mencegah user memasukan inputan yang tidak sesuai dengan kriteria yang ditentukan.

Sebelumnya kita install terlebih dahulu dengan perintah.

```npm install joi```

Selanjutnya kita akan mencoba implementasi Joi pada controller login dan register, berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-expressjs-fundamental/index.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/auth.js
const express = require('express');

const app = express();

const port = 5000;

app.get('/', (req, res) => {
  res.send('Hello Express!');
});

app.listen(port, () => console.log(`Listening on port ${port}!`));
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
