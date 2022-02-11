---
sidebar_position: 7
---

# 7. URL Parameters

import useBaseUrl from '@docusaurus/useBaseUrl';

**URL Parameters** adalah `elemen` yang dimasukkan ke dalam `url` untuk membantu memfilter atau menampilkan `data` berdasarkan dengan `id` yang dimasukan dalam `url`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/7-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=pages/DetailUser.js {1,3,7-16,20-26}
import { useEffect, useState } from "react";
import { Container } from "react-bootstrap";
import { useParams } from "react-router-dom";

const DetailUser = () => {
  const [data, setData] = useState(null);
  const params = useParams();

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/users/${params.id}`)
      .then((response) => response.json())
      .then((json) => setData(json));
    return () => {
      setData(null);
    };
  }, []);

  return (
    <Container className="text-center">
      <h1>Data user with parameter {params.id} is</h1>
      <br />
      <p className="h2">{data?.name}</p>
      <p>{data?.username}</p>
      <p>{data?.email}</p>
      <p>{data?.phone}</p>
      <p>{data?.website}</p>
    </Container>
  );
};

export default DetailUser;
```

```jsx title=App.js {8,33}
import "bootstrap/dist/css/bootstrap.min.css";
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";

import Home from "./pages/Home";
import About from "./pages/About";
import Profile from "./pages/Profile";
import SignIn from "./pages/SignIn";
import DetailUser from "./pages/DetailUser";

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/profile">Profile</Link>
            </li>
          </ul>
        </nav>
      </div>
      <Routes>
        <Route exact path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/profile" element={<Profile />} />
        <Route path="/signin" element={<SignIn />} />
        <Route path="/users/:id" element={<DetailUser />} />
      </Routes>
    </Router>
  );
}

export default App;
```

Dari code implementasi diatas kita `fetch api`/`menampilkan data` dari json placeholder yang menampilkan data `user` berdasarkan dengan `id` yang dimasukan pada `url paramaternya`.

untuk menampilkan data user sesuai dengan `id` melalui `url params`, kita ketikan di `url` `localhost:3000/users/1`, akan tampil data dengan `id 1`, dikarenakan kita memasukan `users/1` 

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-7.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-941rjkovn-demo-dumbways.vercel.app/users/1">
Demo
</a>
</div>