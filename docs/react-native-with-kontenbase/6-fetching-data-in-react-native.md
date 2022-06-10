---
sidebar_position: 6
---

# 6. Fetching data in React Native

import useBaseUrl from '@docusaurus/useBaseUrl';

### 6.1 Prepare

Siapkan template code dan Install Package yang dibutuhkan.

- Clone template code [Here](https://github.com/DumbwaysDotId/reactNative-with-KontenBase-template)

- Install Axios

  ```bash
  npm install axios
  ```

### 6.2 Setup KB with Axios

- Tambahkan code dibawah ini pada file `api.js` untuk setup API_URL dan API_KEY

  ```jsx title=src/config/api.js
  import axios from 'axios';

  let API_KEY = 'YOUR_API_KEY';

  // Create base URL API
  export const API = axios.create({
    baseURL: `https://api.kontenbase.com/query/api/v1/${API_KEY}/`,
  });
  ```

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase/blob/master/src/config/api.js" className="btn-example-code">Code</a>

\*Ambil API KEY dari Project `KontenBase` Anda

### 6.3 Fetching Todo Data

- Import useState dan useEffect

  ```jsx title=src/screens/Todos.js
  import { useState, useEffect } from 'react';
  ```

- Import Config API KontenBase

  ```jsx title=src/screens/Todos.js
  import API from '../config/api';
  ```

- Deklarasi tempat penyimpanan data menggunakan `useState`

  ```jsx title=src/screens/Todos.js
  const [todos, setTodos] = useState([]);
  ```

- Buat function untuk handle pengambilan data

  ```jsx title=src/screens/Todos.js
  const getTodos = async () => {
    try {
      setIsLoading(true);
      const { data } = await API.get('/Todo');

      if (data) {
        setTodos(data);
      }

      setIsLoading(false);
    } catch (error) {
      console.log(error);
    }
  };
  ```

- Gunakan useEffect untuk trigger `Did Mount` untuk menjalankan function `getTodos`

  ```jsx title=src/screens/Todos.js
  useEffect(() => {
    getTodos();
  }, []);
  ```

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase/blob/master/src/screens/Todos.js" className="btn-example-code">Code</a>

### 6.4 Full Code and Result

- Anda dapat melihat `Full Code` implementasi KontenBase dengan React Native pada Tombol dibawah ini:

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase" className="btn-example-code">Full Code</a>

- Aplikasi akan menampilkan list data Todo yang meliputi `title` dan `isDone` berupa checkbox seperti pada gambar dibawah ini

<center>
    <img alt="kb-img-26" src={useBaseUrl('img/docs/kb-26.jpeg')} width="30%"/> 
</center>
