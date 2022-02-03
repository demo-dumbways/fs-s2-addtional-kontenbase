---
sidebar_position: 1
---

# 1. Inline Styling

import useBaseUrl from '@docusaurus/useBaseUrl';

Pada pembelajaran kali ini kita akan mempelajari terkait styling dalam React, untuk cara pemakaiannya menggunakan property `style` dan menggunakan kurung kurawal `{{}}` seperti berikut:

```js
function App() {
  return (
    <div style={{ backgroundColor: 'grey', height: '100px' }}>
      <p style={{ color: 'orange' }}>Selamat datang</p>
    </div>
  );
}

export default App;
```

Silahkan jalankan aplikasinya dengan perintah `npm start`

Jika sudah berhasil, selanjutnya kita akan membuat form yang menggunakan style dalam variabel, sebelumnya kita pindah dulu ke component `Form.js` dan ketikan code berikut:

```js
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

selanjutnya di `App.js` import component `Form.js` seperti berikut:

```js
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

Selanjutnya jalankan aplikasinya dengan perintah `npm start` dan akan tampil seperti gambar berikut:

<img alt="image" src={useBaseUrl('img/docs/image-2-1.png')} height="100px"/>
