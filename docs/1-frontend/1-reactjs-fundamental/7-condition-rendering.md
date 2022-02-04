---
sidebar_position: 7
---

# 7. Conditional Rendering

import useBaseUrl from '@docusaurus/useBaseUrl';

**Conditional Rendering** yaitu ketika sistem dapat menentukan sebuah `component` atau `tag html` dapat dirender atau tidak. Dalam penggunaan `Conditional Rendering` terdapat cara paling umum yang sering digunakan yaitu `ternary operator`.

Berikut code implementasi `Conditional Rendering`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/9-frontend-react-js-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx {1,7,16,22,25-29} title=App.js
import { useState } from 'react';

function PrivatePage(props) {
  return (
    <div>
      <h1>Welcome</h1>
      <button onClick={props.logout}>Logout</button>
    </div>
  );
}

function GuestPage(props) {
  return (
    <div>
      <h1>Please Sign</h1>
      <button onClick={props.login}>Login</button>
    </div>
  );
}

function App() {
  const [isLoggedin, setIsLoggedin] = useState(false);
  return (
    <div>
      {isLoggedin ? (
        <PrivatePage logout={() => setIsLoggedin(!isLoggedin)} />
      ) : (
        <GuestPage login={() => setIsLoggedin(!isLoggedin)} />
      )}
    </div>
  );
}

export default App;
```

Pada code diatas, terdapat deklarasi state yang menyimpan value `boolean` dan terdapat 2 component yaitu component `GuestPage` dan `PrivatePage`. Jika pengguna menekan tombol maka nilai yang tersimpan dalam state berganti menjadi kebalikan dari nilai boolean semula, sebagai contoh jika awalnya nilai boolean `false`, maka akan berubah menjadi `true`.

Jika nilai boolean `true` maka yang akan tampil adalah hasil dari render component `PrivatePage` dan sebaliknya jika nilai boolean `false` maka yang tampil adalah hasil dari render component `GuestPage`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-17.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-9-frontend-4dc40d-demo-dumbways.vercel.app/">
Demo
</a>
</div>
