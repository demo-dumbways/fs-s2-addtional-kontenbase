---
sidebar_position: 6
---

# 6. Broadcast

import useBaseUrl from '@docusaurus/useBaseUrl';

Untuk melengkapi fitur `chat` ini, kita akan coba membuat `broadcast` message ke masing-masing user yang sedang melakukan percakapan, sehingga jika user A mengirim pesan, user B dapat langsung menerima pesan tersebu atau bisa disebut `real-time`.

## 6.1 Server

> path: `server/src/socket/index.js`

- Deklarasi variable `connectedUser` diluar function `socketIo`

  ```js
  const connectedUser = {};
  ```

- Tambahkan code berikut didalam Event `connection`, variable `connectedUser` akan menyimpan `id client` dalam bentuk object dan yang menjadi key `id client` tersebut adalah `id user`

  ```js
  // get user connected id
  const userId = socket.handshake.query.id;

  // save to connectedUser
  connectedUser[userId] = socket.id;
  ```

- Buat sebuah event `send message` yang bertugas untuk menyimpan data pesan dan melakukan `broadcast` event `new message` ke kedua client yang sedang melakukan percakapan.

  ```js {18-20}
  socket.on('send message', async (payload) => {
    try {
      const token = socket.handshake.auth.token;

      const tokenKey = process.env.TOKEN_KEY;
      const verified = jwt.verify(token, tokenKey);

      const idSender = verified.id; //id user
      const { message, idRecipient } = payload; // catch recipient id and message sent from client

      await chat.create({
        message,
        idRecipient,
        idSender,
      });

      // emit to just sender and recipient default rooms by their socket id
      io.to(socket.id)
        .to(connectedUser[idRecipient])
        .emit('new message', idRecipient);
    } catch (error) {
      console.log(error);
    }
  });
  ```

- Full code socket `server side`

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-backend/blob/master/src/socket/index.js">
    Contoh code
    </a>

## 6.2 Client

> path: `client/src/pages/Complain.js`

> path: `client/src/pages/ComplainAdmin.js`

- Tambahkan property `query` yang menyimpan `id user` yang sedang login

  ```js {5-7}
  socket = io('http://localhost:5000', {
    auth: {
      token: localStorage.getItem('token'),
    },
    query: {
      id: state.user.id,
    },
  });
  ```

- Function `onSendMessage` untuk mengirim pesan melalui Event `send message`

  ```js {4-7,10}
  const onSendMessage = (e) => {
    // listen only enter key event press
    if (e.key === 'Enter') {
      const data = {
        idRecipient: contact.id,
        message: e.target.value,
      };

      //emit event send message
      socket.emit('send message', data);
      e.target.value = '';
    }
  };
  ```

- Tambahkan penerima Event `new message` pada life cycle component `did update`. Server akan melakukan `broadcast` Event `new message` ketika user lain mengirim pesan, sehingga jika ada pesan baru, maka client akan langsung mengirim Event `load messages` untuk mengambil data pesan terbaru.

  ```js {2-5}
  // define listener for every updated message
  socket.on('new message', () => {
    console.log('contact', contact);
    socket.emit('load messages', contact?.id);
  });
  ```

- Full code untuk component `Complain (customer)`

  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-frontend/blob/master/src/pages/Complain.js">
  Contoh code
  </a>

- Full code untuk component `Complain (Admin)`
  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-socket-io-frontend/blob/master/src/pages/ComplainAdmin.js">
  Contoh code
  </a>
