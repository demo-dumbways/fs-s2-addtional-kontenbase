---
sidebar_position: 2
---

# 2. Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**Component** adalah salah satu blok bangunan inti dari `React`. Dengan kata lain, setiap aplikasi yang akan Anda kembangkan di `React` akan terdiri dari bagian-bagian yang disebut Component.

Dengan Component tugas membangun Tampilan jauh lebih mudah. Anda dapat melihat Tampilan dipecah menjadi beberapa bagian individual yang disebut `Component` dan menggabungkan semuanya dalam `Component` induk yang akan menjadi Tampilan akhir Anda.

## 2.1 Membuat Component

Untuk membuat `Component` terdiri atas dua cara, yaitu menggunakan `Function` dan `Class` pada Javascript.

### Function Component

`Component` yang dibuat menggunakan `Function` disebut dengan `Function Component`, berikut contoh code `Function Component`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=components/Header.js
function Header() {
  return (
    <div>
      <h1>This Is Header</h1>
    </div>
  );
}
export default Header;
```

```jsx title=App.js
//Import Header Component
import Header from './components/header';

// Content Component
function Content() {
  return (
    <div>
      <h1>This Is A Content</h1>
      <button>Click Me</button>
    </div>
  );
}

function App() {
  return (
    <div>
      <Header />
      <Content />
    </div>
  );
}

export default App;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-11.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-afdf2d-demo-dumbways.vercel.app/">
Demo
</a>
</div>

<br />

### Class Component

`Component` yang dibuat menggunakan `Class` disebut dengan `Class Component`, berikut contoh code `Class Component`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/4-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=components/Header.js
import { Component } from 'react';

class Header extends Component {
  render() {
    return (
      <div>
        <h1>This Is Header</h1>
      </div>
    );
  }
}
export default Header;
```

```jsx title=App.js
import { Component } from 'react';

//Import Header Component
import Header from './components/Header';

// Content Component
class Content extends Component {
  render() {
    return (
      <div>
        <h1>This Is A Content</h1>
        <button>Click Me</button>
      </div>
    );
  }
}

class App extends Component {
  render() {
    return (
      <div>
        <Header />
        <Content />
      </div>
    );
  }
}

export default App;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-12.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-4-frontend-78d800-demo-dumbways.vercel.app/">
Demo
</a>
</div>

<br />
