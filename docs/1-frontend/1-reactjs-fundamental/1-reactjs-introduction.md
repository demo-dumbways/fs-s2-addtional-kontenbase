---
sidebar_position: 2
---

# 1. ReactJs Introduction

import useBaseUrl from '@docusaurus/useBaseUrl';

## 1.1. ReactJs

**React Js** adalah sebuah library JavaScript yang di buat oleh `facebook`. React bukanlah sebuah framework. React adalah library yang bersifat composable user interface, yang artinya kita dapat membuat berbagai UI yang bisa kita bagi menjadi beberapa komponen.

## 1.2. Kenapa Mempelajari ReactJs

1. Cepat dan Efisien
   Karena berbasis komponen maka react hanya perlu me-render resource yang berhubungan dengan data yang berganti, tidak perlu me-render seluruh resource .

2. Reusable (dapat digunakan berulangkali)
   Komponen yang telah kita buat dapat kita gunakan berkali-kali pada saat dibutuhkan. Ini sangat berguna bagi kita untuk mempersingkat waktu dan mengurangi resource yang ada.

3. Library JavaScript
   JSX (JavaScript Extension) singkatnya kita dapat menyematkan syntax HTML kedalam Javascript. Ini sangat membantu kita dalam proses development, apalagi dengan adanya fungsi dari ES6 (Ecma Script).

4. Immutable State
   Kita dapat memanajemen state yang ada dengan menggunakan Redux. Kita dapat mengatasi permasalahan mutable state dengan RamdaJs. Untuk state yang berinteraksi dengan API kita dapat menggunakan Redux-Saga.

## 1.3. Apa itu JSX?

JSX atau bisa kita bilang extended javascript adalah suatu pengembangan javascript dimana kode HTML bisa di ikut sertakan dalam javascript.

Hal pertama yang perlu diperhatikan ketika menggunakan sintaks JSX adalah bahwa React harus dalam ruang lingkupnya berdasarkan cara kompilasi JSX. <br />
Contoh :

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/1-frontend-reactjs-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
function App() {
  return (
    <div>
      <h1>Hallo World!</h1>
    </div>
  );
}

export default App;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-9.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-1-frontend-e6f5e7-demo-dumbways.vercel.app/">
Demo
</a>
</div>

## 1.4 Menyematkan Ekspresi di JSX

Dalam contoh di bawah ini, kita mendeklarasikan variabel bernama name dan kemudian menggunakannya di dalam JSX dengan cara membungkusnya di dalam tanda kurung kurawal (curly braces):

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/2-frontend-react-js-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
function App() {
  const name = 'Budi';
  const element = <h1>Halo, {name}</h1>;

  return <div>{element}</div>;
}

export default App;
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-10.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-kkk12tp75-demo-dumbways.vercel.app/">
Demo
</a>
</div>
