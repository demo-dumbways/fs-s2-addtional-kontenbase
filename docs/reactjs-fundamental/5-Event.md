---
sidebar_position: 5
---

# 5. Event

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari tentang `Event`, yang dimaksud dengan event ini ketika kita melakukan klik pada `button` dan button akan menjalankan event yaitu `onClick` yang dimana ketika button diklik akan menjalankan sebuah anonymous function yang berupa arrow function dengan menampilkan `alert`, untuk contohnya seperti berikut:

```
import React from "react";

function Event() {

  return (
    <div>
      <p>If you press Click Here then an alert will appear</p>
      <button onClick={() => alert("Hello full-stack bootcamp participants")}>
        Click Here
      </button>
    </div>
  );
}

export default Event;
```

contoh tampilan ketika button Click Here diklik seperti berikut:

<img alt="image" src={useBaseUrl('img/docs/event-1.png')} height="100px"/>

Selanjutnya kita akan menampilkan data dari function, sebelumnya buat terlebih dahulu function yang bernama `Greeting` yang mereturn `alert("good morning everyone have a nice day")`, kemudian buat `button` dengan event `onClick` yang dimana nantinya button ketika diklik akan menjalankan sebuah funtion dengan nama `Greeting`, contoh seperti berikut

```
import React from "react";

function Event() {
  function Greeting() {
    return alert("good morning everyone have a nice day");
  }

  return (
    <div>
      <p>If you press Click Here then an alert will appear</p>
      <button onClick={() => alert("Hello full-stack bootcamp participants")}>
        Click Here
      </button>

      <p>If you press Greeting then an alert will appear</p>
      <button onClick={Greeting}>Greeting</button>
    </div>
  );
}

export default Event;
```

contoh tampilan ketika button Greeting diklik seperti berikut:

<img alt="image" src={useBaseUrl('img/docs/event-2.png')} height="100px"/>


Kita sudah berhasil untuk membuat event pada button, ketika button diklik akan menjalankan data sebuah `funtion`.
