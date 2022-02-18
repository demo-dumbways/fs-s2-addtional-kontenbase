---
sidebar_position: 5
---

# 5. Middlewares

import useBaseUrl from '@docusaurus/useBaseUrl';

**Socket.IO** menyediakan `API` untuk memungkinkan kita membuat `middlewares`. Untuk membuat `middlewares`, kita dapat memanggil method `io.use()` sebelum Event koneksi dan membuat validasi pada handshake.

Catatan: Handshake adalah properti yang menyimpan objek dengan nilai opsi yang dikirim dari client

Referensi: [Link](https://socket.io/docs/v3/middlewares/)

## 5.1 Client

- Tambahkan code berikut pada file index.js yang terdapat didalam folder `socket`

  ```js {4-10} title=server/src/socket/index.js
  const socketIo = (io) => {
    // create middlewares before connection event
    // to prevent client access socket server without token
    io.use((socket, next) => {
      if (socket.handshake.auth && socket.handshake.auth.token) {
        next();
      } else {
        next(new Error('Not Authorized'));
      }
    });

    // Connection section bellow here...
  };

  module.exports = socketIo;
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/blob/master/src/socket/index.js">
  Contoh code
  </a>

  Pada code diatas, kita membuat `middlewares` pada `Socket`, dimana `server` akan mengecek `token` yang dikirim dari `client`, jika `client` mengirim token maka dapat melanjutkan ke tahap berikutnya yaitu penanganan `Event`.

## 5.2 Server

- Tambahkan code berikut pada file `Complain.js`

  ```js {2-6,11-13} title=client/src/pages/Complain.js
  useEffect(() => {
    socket = io(process.env.REACT_APP_SERVER_URL || 'http://localhost:5000', {
      auth: {
        token: localStorage.getItem('token'), // we must set options to get access to socket server
      },
    });

    loadContacts();

    // listen error sent from server
    socket.on('connect_error', (err) => {
      console.error(err.message); // not authorized
    });

    return () => {
      socket.disconnect();
    };
  }, []);
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-frontend/blob/master/src/pages/Complain.js">
  Contoh code
  </a>

  Karena server mengharuskan `client` mengirim `token`, kita dapat menambahkan `token` pada `parameter kedua` di function `io` dengan mengambil token dari salah satu tempat penyimpanan pada browser yaitu `localStorage`. Kemudian jika seandainya `client` tidak mengirim `token` maka `server` akan mengirim event `connect_error`, `client` dapat menerima `event` tersebut dan juga dapat melihat pesan `error` dengan mengambil attribute `message`.
