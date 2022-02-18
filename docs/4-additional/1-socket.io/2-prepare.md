---
sidebar_position: 2
---

# 2. Prepare

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum implementasi `Socket.IO`, kita perlu melakukan beberapa persiapan seperti `installasi package`dan `refactor code`.

## 2.1 Struktur Folder

Pada sisi `Server`, buatlah sebuah folder yang bernama `socket` didalam folder `src`, kemudian didalam folder `socket` buatlah file bernama `index.js`.

```text {10,11}
Server
 ┣ config
 ┣ migrations
 ┣ models
 ┣ seeders
 ┣ src
 ┃ ┣ controllers
 ┃ ┣ middlewares
 ┃ ┣ routes
 ┃ ┗ socket
 ┃ ┃ ┗ index.js
 ┣ uploads
 ┣ .gitignore
 ┣ index.js
 ┣ package-lock.json
 ┣ package.json
```

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/tree/master/src">
Contoh Folder
</a>

## 2.2 Installasi Package

Kita perlu menginstall beberapa package yang akan digunakan untuk implementasi `Socket.IO`

### Package for `Server Side`

- Socket.IO

  ```bash
  npm install socket.io
  ```

### Package for `Client Side`

- Socket.IO Client

  ```bash
  npm install socket.io-client
  ```

## 2.3 Code

Kita juga perlu menambahkan beberapa code dibawah ini pada sisi `Server`

- Tambahkan code dibawah ini pada file `index.js`

  ```js {2,3,6-11,14} title=server/index.js
  // import package
  const http = require('http');
  const { Server } = require('socket.io');

  // add after app initialization
  const server = http.createServer(app);
  const io = new Server(server, {
    cors: {
      origin: '*', // define client origin if both client and server have different origin
    },
  });

  // change app to server
  server.listen(port, () => console.log(`Listening on port ${port}!`));
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/blob/master/index.js">
  Contoh Code
  </a>
