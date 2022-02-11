---
sidebar_position: 1
---

# 1. Inline Styling

import useBaseUrl from '@docusaurus/useBaseUrl';

**Inline Styling** adalah teknik `styling` yang digunakan didalam tag `html`

Berikut contoh codenya: 


```jsx {1}
<div style={{ backgroundColor: 'grey', height: '100px' }}>
  Selamat datang
</div>
```

Pada code diatas, terdapat contoh implementasi `inline styling` pada tag `div`, menambahkan attribute style didalamnya terdapat property `backgroundColor` yang memiliki value `grey` dan property `height` memiliki value `100px`, dimana `inline styling` tersebut bertipe `object`.

Berikut code implementasi `inline styling`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/1-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=components/Form.js {1-23,27-29,35}
const styles = {
  form: {
    margin: '16px 20% 0',
  },
  formGroup: {
    marginBottom: '16px',
  },
  formLabel: {
    marginBottom: '8px',
    display: 'inline-block',
  },
  formInput: {
    display: 'block',
    width: '100%',
    padding: '.375rem .75rem',
    fontSize: '1rem',
    lineHeight: 1.5,
    color: '#212529',
    backgroundColor: '#fff',
    border: '1px solid #ced4da',
    borderRadius: '.25rem',
  },
};

function Form() {
  return (
    <form style={styles.form}>
      <div style={styles.formGroup}>
        <label htmlFor="username" style={styles.formLabel}>
          Username
        </label>
        <input
          id="username"
          placeholder="Input username"
          style={styles.formInput}
        />
      </div>
    </form>
  );
}

export default Form;
```

```jsx title=App.js
import Form from './components/Form';

function App() {
  return (
    <div>
      <Form />
    </div>
  );
}

export default App;
```
Dari code implementasi diatas, terdapat component `Form` yang memilki tag `form`, `div`, `label` dan `input` yang akan di `styling` menggunakan teknik `inline styling` agar terlihat menarik.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-2.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-1-frontend-05a450-demo-dumbways.vercel.app/">
Demo
</a>
</div>
