---
sidebar_position: 4
---

# 4. Event

import useBaseUrl from '@docusaurus/useBaseUrl';

Untuk membangun fitur `chat`, ada dua hal yang perlu kita tentukan, yaitu `contact` dan `message`. Pada section ini kita akan mempelajari `method` yang ada di `Socket.IO` dengan menerapkan pengambilan data `contact`.

## 4.1 Method

Di `Socket.io` kita dapat menggunakan method `on()` dan `emit()` untuk mengdefinisikan `Event`.

- `on()`: Metode untuk `mendengarkan/menerima` suatu event yang telah dipancarkan. Jika event dipicu, function `callback` akan dijalankan.

- `emit()`: Metode untuk `memancarkan` suatu `Event`. Jadi, ini berguna jika Anda ingin `mengirim` data.

## 4.2 Server

- Tambahkan code berikut pada file index.js yang terdapat didalam folder `socket`

  ```js {3-20} title=server/src/socket/index.js
  const socketIo = (io) => {
    io.on('connection', (socket) => {
      // define listener on event “load admin contact”
      socket.on('load admin contact', async () => {
        try {
          const adminContact = await user.findOne({
            where: {
              status: 'admin',
            },
            attributes: {
              exclude: ['createdAt', 'updatedAt', 'password'],
            },
          });

          // emit event to send admin data on event “admin contact”
          socket.emit('admin contact', adminContact);
        } catch (err) {
          console.log(err);
        }
      });
    });
  };

  module.exports = socketIo;
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io/blob/3.socket.io-event-contacts/server/src/socket/index.js">
  Contoh code
  </a>

  Pada code diatas, terdapat Event `load admin contact`, artinya jika client mengirim Event `load admin contact` maka `server` akan terpicu dan akan mengirim data yang ada didalam tabel `user` yang berstatus sebagai `admin`, `server` akan mengirim data `user` tersebut melalui Event `admin contact`.

## 4.3 Client

- Tambahkan code berikut pada file `Complain.js`

  ```js {4,11-20} title=client/src/pages/Complain.js
  useEffect(() => {
    socket = io(process.env.REACT_APP_SERVER_URL || 'http://localhost:5000');

    loadContacts();

    return () => {
      socket.disconnect();
    };
  }, []);

  const loadContact = () => {
    // emit event to load admin contact
    socket.emit('load admin contact');

    // listen event to get admin contact
    socket.on('admin contact', (data) => {
      // do whatever to the data sent from server
      console.log(data);
    });
  };
  ```

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io/blob/3.socket.io-event-contacts/client/src/pages/Complain.js">
  Contoh code
  </a>

  Ketika terjadi life cycle `did mount` pada component `Complain`, maka function `loadContacts` akan dijalankan dan `client` akan mengirim Event `load admin contact` ke `server`. Kemudian client akan menerima Event `admin contact` yang didalam event tersebut client akan mendapatkan data contact `admin`.
