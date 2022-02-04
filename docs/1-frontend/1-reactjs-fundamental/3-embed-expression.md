---
sidebar_position: 3
---

# 3. Embed Expression

import useBaseUrl from '@docusaurus/useBaseUrl';

**Embed Expression** adalah menyisipkan data yang disimpan dalam `variable` atau hasil return dari sebuah `function` kedalam tag-tag `html`, teknik ini biasa juga dikenal dengan nama `Embed Expression in JSX`.

Berikut contoh implementasi `Embed Expression` :

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/5-frontend-react-js-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx {2-4,6,11,12} title=App.js
function App() {
  function getMajor() {
    return ' Full-Stack';
  }

  const companyName = 'Dumbways.id';

  return (
    <div>
      <p>
        Welcome To {companyName} Class {getMajor()}
      </p>
    </div>
  );
}

export default App;
```

Pada contoh implementasi diatas, data dari hasil return function `getMajor` dan yang tersimpan didalam variabel `companyName` akan dirender pada component `App`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-13.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-5-frontend-2be89d-demo-dumbways.vercel.app/">
Demo
</a>
</div>
