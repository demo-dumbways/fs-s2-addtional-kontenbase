---
sidebar_position: 6
---

# 6. Props

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari terkait `Props`, Props adalah argumen yang diteruskan antar components. Props diteruskan dari komponen melalui atribut HTML. Kemudian apa yang bisa di dikirim dalam props? Yang bisa dikirim dalam props bisa berupa data, variables, state function dan bahkan sebuah class. Jadi initinya Props adalah suatu cara untuk mengirim dan mengakses data dari component ke component lain secara langsung.

Untuk contohnya kita akgjan membuat component `list` yang dimana nantinya datanya akan dikirimkan dari component `props`, sebelumnya kita buat terlebih dahulu component `list.js`, kemudian ketikan code berikut:

```
import React from "react";

function List(props) {
  return (
    <div>
      <h1>{props.listName}</h1>
    </div>
  );
}
export default List;

```

Code diatas di dalam tag `h1` kita mempunyai data `props.listName` yang datanya akan dikirimkan melalui component props, selanjutnya ketikan code berikut di component `props.js` 

```
import React from "react";

import List from "./components/list";

function Props() {
  return (
    <div>
      <List listName="Budi" />
    </div>
  );
}

export default Props;

```
Penjelasannya kita import terlebih dahulu components List ke dalam component Props, kemudian lakukan pemanggilan component List dengan `<List />`, kemudian kita kirimkan datanya ke component `List` dengan cara `<List listName='Budi'/>`, Jadi kita mengirimkan data `listName` dengan data budi kedalam component `List`, dan kita juga bisa mengirimkan lebih dari satu nama, tinggal lakukan pemanggilan component list lagi dibawahnya dan isikan dengan data nama yang berbeda, contoh seperti berikut:

```
import React from "react";

import List from "./components/list";

function Props() {
  return (
    <div>
      <List listName="Budi" />
      <List listName="Asep" />
      <List listName="Samsul" />
    </div>
  );
}

export default Props;
```

contoh tampilan dibrowser seperti berikut:

<img alt="image" src={useBaseUrl('img/docs/props-1.png')} height="100px"/>

Kita sudah berhasil untuk mengirimkan data antar component menggunakan `props`.
