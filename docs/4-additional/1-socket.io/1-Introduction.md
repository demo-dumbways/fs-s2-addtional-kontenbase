---
sidebar_position: 1
---

# 1. Introduction

import useBaseUrl from '@docusaurus/useBaseUrl';

## 1.1 Socket.IO

<center>
<img alt="image1-2" src="https://socket.io/images/logo.svg" style={{backgroundColor: 'white', borderRadius: 5}} width="30%"/>
</center>

<br />

**Socket.IO** adalah library JavaScript untuk aplikasi web `realtime`. Dengan `Socket.io` kita dapat berkomunikasi secara real-time, dua arah dan komunikasi berbasis `Event`. `Socket.IO` memiliki dua bagian: library sisi `client` yang berjalan di `browser`, dan library sisi `server` untuk `Node.js`.

Dengan komunikasi berbasis `event`, kita tidak perlu `request` untuk mendapatkan `data` terbaru, yang perlu kita lakukan hanyalah `listen / subcribe` ke suatu topik. Jadi selama `WebSocket` tetap aktif dan listen ke suatu topik, jika terdapat data baru di topik tersebut, kita akan mendapatkan datanya secara otomatis.

Referensi: [Link](https://socket.io/docs/v4/)

## 1.2 Explanation

Pada materi ini kita akan membuat fitur `chat` untuk membuktikan bahwa fungsi `Socket.IO` berjalan secara `real-time`.

<center>
  <img alt="image1-2" src={useBaseUrl('img/docs/image-socket-2.png')} width="70%"/>
</center>
