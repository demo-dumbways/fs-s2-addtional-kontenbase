---
sidebar_position: 3
---

# 3. Connection

import useBaseUrl from '@docusaurus/useBaseUrl';

Untuk menginisialisasi koneksi antara klien dan server, kita dapat menambahkan code pada sisi `server` dan `client` seperti ini:

## 3.1 Server

- Tambahkan code berikut pada file `index.js` yang terdapat didalam folder `socket`

  ```js {1-2,4-8,10} title=server/src/socket/index.js
  const http = require('http');
  const { Server } = require('socket.io');

  const socketIo = (io) => {
    io.on('connection', (socket) => {
      console.log('client connect:', socket.id);
    });
  };

  module.exports = socketIo;
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io/blob/2.socket.io-connection/server/src/socket/index.js">
    Contoh Code
    </a>

- Tambahkan code berikut pada file root `index.js`

  ```js {1-5,7} title=server/index.js
  const io = new Server(server, {
    cors: {
      origin: '*',
    },
  });

  require('./src/socket')(io);
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io/blob/2.socket.io-connection/server/index.js">
    Contoh Code
    </a>

## 3.2 Client

- Tambahkan code berikut pada file pages `Complain.js` dan `ComplainAdmin.js`

  > Path : `client/src/pages/Complain.js`

  > Path : `client/src/pages/ComplainAdmin.js`

  ```js
  // import socket.io-client
  import { io } from 'socket.io-client';
  ```

  ```js
  // initial variable outside component
  let socket;
  ```

  ```js
  // connect to server in useEffect function
  useEffect(() => {
    socket = io(process.env.REACT_APP_SERVER_URL || 'http://localhost:5000');

    return () => {
      socket.disconnect();
    };
  }, []);
  ```

   <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io/blob/2.socket.io-connection/client/src/pages/Complain.js">
    Contoh Code
    </a>

## 3.3 Result

Jika `Client` berhasil `connect` ke `Server` maka pada terminal Anda akan muncul tulisan seperti berikut:

```bash
client connect:  GJotZJhkDe2p5FcPAAAD
```

`GJotZJhkDe2p5FcPAAAD` merupakan `id client` yang secara otomatis tergenerate jika ada client yang connect ke server.
