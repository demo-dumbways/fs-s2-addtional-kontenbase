---
sidebar_position: 3
---

# 3. Global Css

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan memeplajari terkait Global Css, global css ini sama fungsinya ketika kita membuat file `css` yang dimana kita buat menggunkan ekstensi `.css`, global css ini yang nantinya kita bisa panggil secara global, jadi bisa dipanggil di component apa saja. kita buat file baru dengan nama `style.css`, Selanjutnya kita buat codenya seperti berikut.

```js
.form-group {
  margin-bottom: 16px;
}

.form-label {
  margin-bottom: 8px;
  display: inline-block;
}

.form-select {
  display: block;
  width: 100%;
  height: 38px;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.form-select:focus {
  color: #212529;
  background-color: #fff;
  border-color: #86b7fe;
  outline: 0;
  box-shadow: 0 0 0 0.25rem rgba(13, 110, 253, 0.25);
}
```

Selanjutnya import file css yang sudah dibuat kedalam file `App.js`

```js
// import global stylesheet in app.js
import "./styles/styles.css";
// import the components here
import Form from "./components/Form";

function App() {
  return (
    <div>
      <Form />
    </div>
  );
}

export default App;
```

kemudian buat div di dalam `Form.js` untuk menampung tag `label` dan `select`, untuk codenya seperti berikut:

```js
// import css module file
import cssModules from "./Form.module.css";

const styles = {
  form: {
    margin: "16px 20% 0",
  },
  formGroup: {
    marginBottom: "16px",
  },
  formLabel: {
    marginBottom: "8px",
    display: "inline-block",
  },
  formInput: {
    display: "block",
    width: "100%",
    padding: ".375rem .75rem",
    fontSize: "1rem",
    lineHeight: 1.5,
    color: "#212529",
    backgroundColor: "#fff",
    border: "1px solid #ced4da",
    borderRadius: ".25rem",
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
      <div className={cssModules.formGroup}>
        <label htmlFor="email" className={cssModules.formLabel}>
          Email
        </label>
        <input
          id="email"
          type="email"
          placeholder="Input email"
          className={cssModules.formInput}
        />
      </div>
      
      {/* code here */}
      <div className="form-group">
        <label htmlFor="gender" className="form-label">
          Gender
        </label>
        <select id="gender" className="form-select" defaultValue="Choose...">
          <option>Choose...</option>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
    </form>
  );
}

export default Form;
```

Untuk penjelasan terkait code diatas adalah untuk pembuatan classnya sama dengan kita membuat di `html`, bedanya untuk di React menggunaka property `className`.