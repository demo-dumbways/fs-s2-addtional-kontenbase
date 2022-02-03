---
sidebar_position: 5
---

# 5. Props

import useBaseUrl from '@docusaurus/useBaseUrl';

**Props** adalah argumen yang diteruskan antar components. `Props` diteruskan dari `Component` melalui atribut HTML. Yang bisa dikirim dalam props bisa berupa `data`, `variables`, `function` dan bahkan sebuah `class`. Jadi initinya `Props` adalah suatu cara untuk `mengirim` dan `mengakses` data dari component ke component lain secara langsung.

Berikut contoh implementasi `Props`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/7-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx {4} title=components/List.js
function List(props) {
  return (
    <div>
      <h1>{props.data}</h1>
    </div>
  );
}
export default List;
```

```jsx {2,8-11,13-15} title=App.js
//Import List Components
import List from './components/List';

function App() {
  return (
    <div>
      <p>On the image element using the default props, namely src</p>
      <img
        alt="kumparan"
        src="https://blue.kumparan.com/image/upload/fl_progressive,fl_lossy,c_fill,q_auto:best,w_640/v1542354895/ulaqus4ev5ihhqkpbhuz.jpg"
      />

      <List data="BMW" />
      <List data="Mercedes-Benz" />
      <List data="Lamborghini" />
    </div>
  );
}

export default App;
```

Pada implementasi `Props` diatas, kita mengirim data nama mobil ke component `List` melalui props yang diberi nama `data`. Perlu diperhatikan, didalam component terdapat Props `default` dan Props `costume`. Pada tag `img` terdapat props `default` yaitu `alt` dan `src`, sedangkan pada component `List` terdapat props `costume` yaitu `data`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-15.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-7-frontend-f91b8e-demo-dumbways.vercel.app/">
Demo
</a>
</div>
