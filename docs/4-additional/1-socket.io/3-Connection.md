---
sidebar_position: 3
---

# 3. Connection

import useBaseUrl from '@docusaurus/useBaseUrl';

Untuk menginisialisasi koneksi antara klien dan server, kita dapat menambahkan code pada sisi `server` dan `client` seperti ini:

## 3.1 Server

- Tambahkan code berikut pada file `index.js` yang terdapat didalam folder `socket`

  ```js {1-5,7} title=server/src/socket/index.js
  const socketIo = (io) => {
    io.on('connection', (socket) => {
      console.log('client connect:', socket.id);
    });
  };

  module.exports = socketIo;
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/blob/master/src/socket/index.js">
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

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/blob/master/index.js">
    Contoh Code
    </a>

## 3.2 Client

- Tambahkan code berikut pada file pages `Complain.js` dan `ComplainAdmin.js`

  > Path : `client/src/pages/Complain.js`

  > Path : `client/src/pages/ComplainAdmin.js`

  ```js
  // initial variable outside component
  let socket;
  ```

  ```js
  // connect to server in useEffect function
  useEffect(() => {
    socket = io('http://localhost:5000');

    return () => {
      socket.disconnect();
    };
  }, []);
  ```
