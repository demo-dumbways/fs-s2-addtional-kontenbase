---
sidebar_position: 7
---

# 7. State

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari terkait State,
State merupakan data yang tersimpan dalam sebuah component. State bersifat private dan hanya relevan terhadap component itu sendiri. Berbeda dengan props yang value atau datanya dikirimkan dari component lain, state justru dapat menyimpan dan mengubah datanya sendiri dari dalam, Ketika data state ada perubahan komponen akan di render atau muat ulang.

Untuk penulisan state menggunakan `[]` dikarenakan mempunyai dua variabel, variabel pertama untuk penampung datanya dan kedua untuk melakukan perubahan ketika data akan dirubah.  

Oke langsung kita praktekan aja untuk cara pemakaiannya, sebelumnya `import useState` terlebih dahulu sebelum menggunakan state, contohnya seperti berikut:
```
import React, { useState } from "react";

function State() {

  //init State
  const [ name, setName ] = useState('Samsul')

  return (
    <div>

      <p>{name}<p/>

      //make changes to data when the button is clicked
      <button onClick={() => setName('Rijal')}>Klik</button>
    
    </div>
  );
}

export default State;

```

<img alt="image" src={useBaseUrl('img/docs/state-1.png')} height="100px"/>

akan tampil seperti gambar dibawah ini ketika button diklik
<img alt="image" src={useBaseUrl('img/docs/state-2.png')} height="100px"/>


Selanjutnya kita akan mempraktikan pengunaan state lagi yang dimana nantinya ketika `button` di klik akan melakukan penambahan dan pengurangan, untuk codenya seperti berikut:

```
import React, { useState } from "react";

function State() {
  //init State
  const [counter, setCounter] = useState(0);

  //Create Function Add
  function Add() {
    return setCounter(counter + 1);
  }

  //Create Function Less
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

export default State;
```

akan tampil seperti gambar dibawah ini ketika button diklik

<img alt="image" src={useBaseUrl('img/docs/state-3.png')} height="100px"/>

Kita sudah berhasil membuat state dan melakukan perubahan pada datanya.