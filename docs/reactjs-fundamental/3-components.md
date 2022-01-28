---
sidebar_position: 3
---

# 3. Components

import useBaseUrl from '@docusaurus/useBaseUrl';

Buka folder project aplikasi react js kita di visual studio code,
di folder `src` klik file `App.js` kemudian hapus tag `<header>` ganti dengan tag `h1` dan ketikan `Hello World` seperti contoh berikut:

```
import React from "react";
import './App.css';

function App() {
  return (
    <div className="App">
      <h1>Hello World</h1>
    </div>
  );
}

export default App;

```

Maka akan tampil seperti gambar berikut:

<img alt="image1" src={useBaseUrl('img/docs/react-js.png')} height="400px"/>

Selanjutnya kita akan membuat tampilan aplikasi dengan menggunakan components, untuk membuatnya kita buat folder `components`, didalam folder `src` buat file `Header.js`, dan ketikan code berikut:

```
import React from "react";

function Header() {
  return (
    <div>
      <h1>This Is Header</h1>
    </div>
  );
}
export default Header;
```

Selanjutnya kita import file components `Header` yang sudah kita buat kedalam `App.js` dengan mengetikan `import Header from "./components/Header"`, dan kita panggil dalam tag `div` dengan `<Header />`, untuk contohnya sebagai berikut:
```
import React from "react";
import './App.css';
import Header from "./components/Header";

function App() {
  return (
    <div>
        <Header />
        <h1>Hello World</h1>
    </div>
  );
}

export default App;

```

Selanjutnya kita bisa membuat components dalam satu file `App.js`, untuk contohnya kita akan membuat components `contents` yang nantinya untuk menampung informasi content yang ada di dalam aplikasi kita, ketikan code berikut:

```
import React from "react";
import './App.css';
import Header from "./components/Header";

function App() {
  return (
    <div>
        <Header />
        <Content />
    </div>
  );
}

function Content() {
  return (
    <div>
      <h1>This Is A Content</h1>
      <button>Click Me</button>
    </div>
  );
}

export default App;

```