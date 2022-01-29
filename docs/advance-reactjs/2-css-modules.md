---
sidebar_position: 2
---

# 2. Css Modules

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan memeplajari terkait Css Modules, yang dimana kita menuliskan css menggunakan ekstensi `.module.css` yang wajib diketikan dalam pembuatan file css modulenya.
Oke langsung aja kita praktekan dengan menuliskan code berikut di dalam file `Form.module.css`:

```css
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

Selanjutnya import `Form.module.css` yang tadi kita buat kedalam `Form.js` seperti berikut:

```css
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
Untuk penjelasan terkait code diatas adalah pemanggilan `class css`nya menggunakan `className` tidak lagi menggunakan `class` dalam react, setelah menuliskan property `className` kemudian masuk panggil `cssModules` yang sudah di `import` dan kemudian masukan nama `class` yang ada di css modulenya.

Selanjutnya jalankan aplikasinya dengan perintah `npm start` dan akan tampil seperti gambar berikut:

<img alt="image" src={useBaseUrl('img/docs/inline-style-1.png')} height="100px"/>