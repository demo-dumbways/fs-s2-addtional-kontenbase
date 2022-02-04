---
sidebar_position: 4
---

# 4. Event

import useBaseUrl from '@docusaurus/useBaseUrl';

**Event** adalah peristiwa dari hasil interaksi pengguna terhadap Aplikasi. Sebagai contoh, kita menggunakan tag `button` yang memiliki event `onClick`, artinya jika tag `button` diklik oleh pengguna, maka event `onClick` akan terpicu. Kemudian kita harus membuat `Event Handling`, agar tag `button` tersebut dapat berjalan sesuai dengan fungsinya.

Berikut contoh implementasi `Event`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/6-frontend-react-js-fundamental/src/App.js">
Contoh code
</a>

<br />
<br />

```jsx {2-4,9-11,14} title=App.js
function App() {
  function Greeting() {
    return alert('good morning everyone have a nice day');
  }

  return (
    <div>
      <p>If you press Click Here then an alert will appear</p>
      <button onClick={() => alert('Hello full-stack bootcamp participants')}>
        Click Here
      </button>

      <p>If you press Greeting then an alert will appear</p>
      <button onClick={Greeting}>Greeting</button>
    </div>
  );
}

export default App;
```

Pada contoh implementasi diatas, ketika pengguna klik salah satu tombol, maka akan muncul sebuah `alert` sesuai dengan `Event handling` yang diberikan.

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-14.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-6-frontend-438cf2-demo-dumbways.vercel.app/">
Demo
</a>
</div>
