---
sidebar_position: 6
---

# 6. State

import useBaseUrl from '@docusaurus/useBaseUrl';

**State** merupakan data yang tersimpan dalam sebuah `component`. `State` bersifat `private` dan hanya relevan terhadap `component` itu sendiri. Berbeda dengan `props` yang value atau datanya dikirimkan dari `component` lain, `state` justru dapat menyimpan dan mengubah datanya sendiri dari dalam. Ketika data didalam `state` ada perubahan, komponen akan di render atau di muat ulang.

### Membuat State dengan useState

Untuk membuat `state`, kita perlu memanggil `useState` dari `react` seperti berikut:

```jsx
import { useState } from "react";
```

Setelah memanggil `useState`, kita dapat membuat state dengan melakukan deklarasi data didalam parameter `useState`. Berikut contoh deklarasi number didalam state:

```jsx
useState(34);
```

Kita dapat mendeklarasi berbagai `type data` didalam `state`, karena sifat dati `state` seperti `variabel`, yaitu menyimpan data.

`useState` akan mengembalikan data berupa `Array`, didalam array tersebut memiliki 2 buah index, index `pertama [0]` digunakan jika kita ingim melihat/mengambil data dan index `kedua [1]` jika ingin mengubah data yang terdapat didalam state tersebut. Berikut contohnya:

```jsx
const [number, setNumber] = useState(34);
```

### Implementasi State

Kita akan implementasi `state` dengan menerapkan `Event` agar terdapat interaksi jika pengguna klik tombol `add` maka akan terjadi penjumlahan dan jika klik tombol `less` maka akan terjadi pengurangan terhadap data yang tersimpan didalam state.

Berikut code implementasi `State`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/8-frontend-react-js-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx {1,4,6-8,10-12,21,23,24} title=App.js
import { useState } from "react";

function App() {
  const [counter, setCounter] = useState(0);

  function Add() {
    return setCounter(counter + 1);
  }

  function Less() {
    return setCounter(counter - 1);
  }

  return (
    <div>
      <p>
        If you click the add button it will increase by one, vice versa if you
        click the less button it will decrease by one
      </p>

      <h2>{counter}</h2>

      <button onClick={Add}>Add</button>
      <button onClick={Less}>Less</button>
    </div>
  );
}

export default App;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-16.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-8-frontend-8602a9-demo-dumbways.vercel.app/">
Demo
</a>
</div>
