---
sidebar_position: 4
---

# 4. Fetching

import useBaseUrl from '@docusaurus/useBaseUrl';

Berikut langkah-langkah mengambil data dari `Server`:

### 4.1 Product (Customer)

> Path: `client/src/pages/Product.js`

- Import `useQuery` dari package `react-query`

  ```js
  import { useQuery } from 'react-query';
  ```

- Ambil konfigurasi function `API`

  ```js
  import { API } from '../config/api';
  ```

- Fetching data products dari endpoint `/products`

  ```js
  let { data: products } = useQuery('productsCache', async () => {
    const response = await API.get('/products');
    return response.data.data;
  });
  ```

  Data akan tersimpan didalam variable `products`

  Referensi: [useQuery](https://react-query.tanstack.com/reference/useQuery)

- Render

  Untuk menampilkan data yang diperoleh dari `API backend` kita dapat menggunakan function `MAP`

  ```jsx {2,5,7,10-12}
  <>
    {products?.map((item, index) => (
      <div className="card-product mt-3">
        <img
          src={item.image}
          className="img-fluid img-rounded"
          alt={item.name}
        />
        <div className="p-2">
          <div className="text-header-product-item">{item.name}</div>
          <div className="text-product-item">{item.price}</div>
          <div className="text-product-item">Stock : {item.qty}</div>
        </div>
      </div>
    ))}
  </>
  ```

### 4.2 Product (Admin)

### 4.3 Detail Product

### 4.4 Profile & Transaction

### 4.5 Category
