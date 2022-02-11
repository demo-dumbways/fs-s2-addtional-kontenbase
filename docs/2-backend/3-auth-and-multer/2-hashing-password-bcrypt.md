---
sidebar_position: 2
---

# 2. Hashing Password Bcrypt

import useBaseUrl from '@docusaurus/useBaseUrl';

**Bcrypt** merupakan package untuk mengamankan data password kita agar datanya tidak diketahui orang lain dengan cara dienkrip passwordnya, enkripsi akan menjamin data-data tetap aman meskipun berada di tangan orang lain, karena mereka tidak tahu isi asli dari datanya.

contoh password belum di enkrip
```123456```

contoh password sudah di enkrip
```$2a$10$BLMmNP5ERgFYq3HZEH2b9.2uZG6qYrUbDbPx8GGluNGWbPz7/Oh72```

Sebelumnya kita install terlebih dahulu dengan perintah.

```npm install bcrypt```

Selanjutnya kita akan mencoba implementasikan, berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-expressjs-fundamental/index.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/auth.js

```

<img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
