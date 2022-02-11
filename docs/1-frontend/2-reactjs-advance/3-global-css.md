---
sidebar_position: 3
---

# 3. Global Css

import useBaseUrl from '@docusaurus/useBaseUrl';

**Global CSS** adalah teknik styling yang digunakan untuk membuat `styling` secara `global` teknik pengimplementasian `CSS Global` adalah teknik yang paling di rekomendasikan. Dimana pada teknik ini kita bisa menggunakan seluruh styling yang telah kita buat di semua `components`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/main/src">
Contoh code
</a>

<br />
<br />

```css title=styles/styles.css
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

```jsx title=components/Form.js
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

```jsx title=App.js
import "./styles/styles.css";
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

Dari code implementasi diatas, terdapat file `styles.css` yang memiliki `styling` untuk mengatur tampilan pada tag `label gender` dan `select` dalam `component` `Form.js`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-3.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-37d2af-demo-dumbways.vercel.app/">
Demo
</a>
</div>
