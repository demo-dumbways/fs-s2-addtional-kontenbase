---
sidebar_position: 3
---

# 3. Authentication JWT

import useBaseUrl from '@docusaurus/useBaseUrl';

**JWT** JSON Web Token atau lebih dikenal dengan JWT yang mana JWT ini adalah sebuah token berbentuk string yang nantinya akan menyimpan data user ketika melakukan login.

contoh token seperti berikut:
```js
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

Contoh toke diatas terdiri 3 bagian yaitu:

baris pertama adalah Header: Algorithm & Token Type

```js
{
  "alg": "HS256",
  "typ": "JWT"
}
```
baris kedua adalah Payload: DATA

```js
{
  "sub": "1234567890",
  "name": "John Doe",
  "iat": 1516239022
}
```
baris ketiga adalah Verify Signature
```js
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  
your-256-bit-secret

) secret base64 encoded

```

Untuk menggunakan jwt kita harus install dengan perintah:

```npm install jsonwebtoken```

Selanjutnya kita akan mencoba implementasikan, berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/1-expressjs-fundamental/index.js">
Contoh code
</a>

<br />
<br />

```js title=controllers/auth.js

```

```js title=middlewares/auth.js

```

```js title=routes/index.js.js

```

<img alt="image1-2" src={useBaseUrl('img/docs/image-4-1.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-backend-git-1-e-bef277-demo-dumbways.vercel.app/">
Demo
</a>
</div>
