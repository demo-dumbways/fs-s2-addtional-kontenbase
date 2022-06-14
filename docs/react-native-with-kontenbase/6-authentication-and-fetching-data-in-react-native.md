---
sidebar_position: 6
---

# 6. Implementation in React Native

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

  let API_KEY = 'YOUR API KEY';

  // Create base URL API
  export const API = axios.create({
    baseURL: `https://api.kontenbase.com/query/api/v1/${API_KEY}/`,
  });

  export const setAuthToken = (token) => {
    if (token) {
      API.defaults.headers.common['Authorization'] = `Bearer ${token}`;
    } else {
      delete API.defaults.headers.commin['Authorization'];
    }
  };
  ```

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase/blob/master/src/config/api.js" className="btn-example-code">Code</a>

\*Ambil API KEY dari Project `KontenBase` Anda

### 6.3 Authentication

- Register

  Tambahkan code dibawah ini pada function `handleOnPress` file `Register.js`

  ```jsx title=src/screens/Register.js
  const config = {
    headers: {
      'Content-type': 'application/json',
    },
  };

  const body = JSON.stringify(form);

  const response = await API.post('/auth/register', body, config);

  if (response) {
    await AsyncStorage.setItem('token', response.data.token);
    loggedChecked();
  }
  ```

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase/blob/master/src/screens/Register.js" className="btn-example-code">Code</a>

- Login

  Tambahkan code dibawah ini pada function `handleOnPress` file `Login.js`

  ```jsx title=src/screens/Login.js
  const config = {
    headers: {
      'Content-type': 'application/json',
    },
  };

  const body = JSON.stringify(form);

  const response = await API.post('/auth/login', body, config);

  if (response) {
    await AsyncStorage.setItem('token', response.data.token);
    loggedChecked();
  }
  ```

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase/blob/master/src/screens/Login.js" className="btn-example-code">Code</a>

### 6.4 Fetching Todo Data

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

      const { data: userData } = await API.get('/auth/user');

      // Get Todo data by Owner
      const { data } = await API.get(`/Todo?owner=${userData._id}`);

      setUser(userData);

      if (data.length != 0) {
        setTodos(data);
      }

      setIsLoading(false);
      loggedChecked();
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

### 6.5 Full Code and Result

- Anda dapat melihat `Full Code` implementasi KontenBase dengan React Native pada Tombol dibawah ini:

  <a href="https://github.com/DumbwaysDotId/reactNative-with-KontenBase" className="btn-example-code">Full Code</a>

- Aplikasi akan menampilkan list data Todo yang meliputi `title` dan `isDone` berupa checkbox, tetapi Anda perlu melakukan `registrasi` dan `login` terlebih dahulu. Seperti pada gambar dibawah ini

<center>
    <img alt="kb-img-ss-1" src={useBaseUrl('img/docs/ss-1.jpeg')} width="30%" style={{marginRight: 5}}/> 
    <img alt="kb-img-ss-2" src={useBaseUrl('img/docs/ss-2.jpeg')} width="30%" style={{marginRight: 5}}/> 
    <img alt="kb-img-ss-3" src={useBaseUrl('img/docs/ss-3.jpeg')} width="30%"/> 
</center>
