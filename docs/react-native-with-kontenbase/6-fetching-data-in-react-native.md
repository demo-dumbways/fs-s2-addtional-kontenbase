---
sidebar_position: 6
---

# 6. Fetching data in React Native

import useBaseUrl from '@docusaurus/useBaseUrl';

### 6.1 Prepare

Siapkan template code dan Install Package yang dibutuhkan.

- Clone template code [Here](https://github.com/demo-dumbways/todo-app-with-kontenbase)

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

\*Ambil API KEY dari Project KontenBase Anda

### 6.3 Fetching Todo Data

- Import useState dan useEffect

  ```jsx title=src/App.js
  import { useState, useEffect } from 'react';
  ```

- Import Config API KontenBase

  ```jsx title=src/App.js
  import kontenbase from './config/api';
  ```

- Deklarasi tempat penyimpanan data menggunakan `useState`

  ```jsx title=src/App.js
  const [todos, setTodos] = useState([]);
  ```

- Buat function untuk handle pengambilan data

  ```jsx title=src/App.js
  const getTodos = async () => {
    const { data, error } = await kontenbase.service('Todos').find();

    if (error) {
      return alert(error.message);
    }

    setTodos(data);
  };
  ```

- Gunakan useEffect untuk trigger `Did Mount` untuk menjalankan function `getTodos`

  ```jsx title=src/App.js
  useEffect(() => {
    getTodos();
  }, []);
  ```

<center>
    <img alt="kb-img-14" src={useBaseUrl('img/docs/kb-14.png')} width="80%"/> 
</center>
