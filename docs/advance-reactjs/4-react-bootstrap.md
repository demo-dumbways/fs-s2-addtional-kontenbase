---
sidebar_position: 4
---

# 4. Global Css

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan memeplajari terkait `React Bootstrap` yaitu `package` yang dimana nantinya akan mempermudah kita dalam melakukan styling pada saat membuat aplikasi menggunakan `React`.

Sebelumnya install terlebih dahulu React Bootstrap dengan perintah `npm install react-bootstrap bootstrap@5.1.3`

Selanjutnya kita wajib mengimport `react-bootstrap` yang sudah di install ke dalam `Index.js` atau ke `App.js`, Oke langusng aja kita praktekan dengan mengimportnya kedalam `App.js` untuk codenya seperti berikut:

```js
// import css bootstrap
import "bootstrap/dist/css/bootstrap.min.css";

// import styles.css
import "./styles/styles.css";

// import components
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

Selanjutnya import React Bootstrap component di `Form.js`, Selanjutnya ubah function `Form` dengan `FormComponent` untuk codenya seperti berikut:

```js
// import React Bootstrap components
import { Form, Col } from "react-bootstrap";

// import css module file
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

// change component name because it has used by react-bootstrap
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

Penjelasan code diatas, kita membuat `Form` menggunakan `React Bootstrap` yang dimana terdapat component react bootrstap `Form` dan `Row`, jadi harus di import terlebih dahulu sebelum kita menggunakannya.