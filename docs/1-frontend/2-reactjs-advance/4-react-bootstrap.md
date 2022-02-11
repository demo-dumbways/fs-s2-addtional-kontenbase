---
sidebar_position: 4
---

# 4. React Bootstrap

import useBaseUrl from '@docusaurus/useBaseUrl';

**React Bootstrap** adalah `framework CSS` yang dimana nantinya akan mempermudah kita dalam melakukan `styling` pada saat membuat aplikasi menggunakan `React Js`, dalam tag `html` tinggal memanggil `class` yang sudah disediakan oleh `React Bootstrap`.

Lakukan instalasi `React Bootstrap` dengan perintah: 
```bash
npm install react-bootstrap bootstrap@5.1.3
```

Import `react-bootstrap` pada `App.js`

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/4-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js {1}
import "bootstrap/dist/css/bootstrap.min.css";
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

```jsx title=components/Form.js {1,68-77}
import { Form, Col } from "react-bootstrap";
import cssModules from "./Form.module.css";

// inline style
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

function FormComponent() {
  return (
    //inline styling
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
      {/* css module */}
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
      {/* css global */}
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

      {/* react-bootstrap componen */}
      <Form.Row>
        <Form.Group as={Col} md="6">
          <Form.Label>City</Form.Label>
          <Form.Control type="text" placeholder="City" required />
        </Form.Group>
        <Form.Group as={Col} md="6">
          <Form.Label>State</Form.Label>
          <Form.Control type="text" placeholder="State" required />
        </Form.Group>
      </Form.Row>
    </form>
  );
}

export default FormComponent;
```

Dari code implementasi diatas kita membuat `Form` menggunakan `React Bootstrap` yang dimana terdapat component react bootrstap `Form` dan `Row`, harus di import terlebih dahulu agar bisa digunakan.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-3.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-37d2af-demo-dumbways.vercel.app/">
Demo
</a>
</div>