---
sidebar_position: 7
---

# 7. State

import useBaseUrl from '@docusaurus/useBaseUrl';

**State** merupakan data yang tersimpan dalam sebuah `component`. `State` bersifat `private` dan hanya relevan terhadap `component` itu sendiri. Berbeda dengan `props` yang value atau datanya dikirimkan dari `component` lain, `state` justru dapat menyimpan dan mengubah datanya sendiri dari dalam. Ketika data didalam `state` ada perubahan, komponen akan di render atau di muat ulang.

### Membuat State dengan useState

Untuk membuat `state`, kita perlu memanggil `useState` dari `react` seperti berikut:

```js
import { useState } from "react";
```

Setelah memanggil `useState`, kita dapat membuat state dengan melakukan deklarasi data didalam parameter `useState`. Berikut contoh deklarasi number didalam state:

```js
useState(34);
```

Kita dapat mendeklarasi berbagai `type data` didalam `state`, karena sifat dati `state` seperti `variabel`, yaitu menyimpan data.

`useState` akan mengembalikan data berupa `Array`, didalam array tersebut memiliki 2 buah index, index `pertama [0]` digunakan jika kita ingim melihat/mengambil data dan index `kedua [1]` jika ingin mengubah data yang terdapat didalam state tersebut. Berikut contohnya:

```js
const [number, setNumber] = useState(34);
```

Kita akan implementasi `state` dengan menerapkan `Event` agar terdapat interaksi jika pengguna klik tombol `add` maka akan terjadi penjumlahan dan jika klik tombol `less` maka akan terjadi pengurangan terhadap data yang tersimpan didalam state.

Berikut code implementasi `State`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/state.js
import { StatusBar } from "expo-status-bar";
import React, { useState } from "react";
import { View, Text, TouchableOpacity } from "react-native";

export default function State() {
  // Init State
  const [counter, setCounter] = useState(0);

  //Create Function Add
  function Add() {
    return setCounter(counter + 1);
  }

  // Create Function Less
  function Less() {
    return setCounter(counter - 1);
  }

  return (
    <View>
      <StatusBar />
      {/* Code Here */}
      <Text>
        If you click the add button it will increase by one, vice versa if you
        click the less button it will decrease by one
      </Text>

      <Text>{counter}</Text>

      <TouchableOpacity onPress={Add}>
        <Text>Add</Text>
      </TouchableOpacity>
      <TouchableOpacity onPress={Less}>
        <Text>Less</Text>
      </TouchableOpacity>
    </View>
  );
}
```

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

Selanjutnya kita import component `state` pada App.js
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View } from "react-native";

//Import Screen
import State from "./src/screens/state";

export default function App() {
  return (
    <View style={{ marginTop: 200 }}>
      <StatusBar />
      <State />
    </View>
  );
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@5.state">
Demo
</a>
</div>