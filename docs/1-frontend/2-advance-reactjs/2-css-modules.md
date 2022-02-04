---
sidebar_position: 2
---

# 2. Css Modules

import useBaseUrl from '@docusaurus/useBaseUrl';

**CSS Modules** adalah teknik styling yang digunakan untuk membuat styling secara sepesifik dalam component.

Berikut contoh codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/main/src/components">
Contoh code
</a>

<br />
<br />

```css title=components/Form.module.css
.formGroup {
    margin-bottom: "16px";
}
.formLabel {
    margin-bottom: 8px;
    display: inline-block;
}
.formInput {
    display: block;
    width: 100%;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    color: #212529;
    background-color: #fff;
    border: 1px solid #ced4da;
    border-radius: 0.25rem;
    appearance: none;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
.formInput:focus {
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
    // inline styling
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
      {/* css modules */}
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
    </form>
  );
}

export default Form;
```

Dari code implementasi diatas, terdapat file `Form.module.css` yang memiliki `styling` untuk mengatur tampilan pada tag `label email` dan `input` dalam `component` `Form.js`.


<img alt="image1-2" src={useBaseUrl('img/docs/image-2-2A.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-2-frontend-ca331a-demo-dumbways.vercel.app">
Demo
</a>
</div>
