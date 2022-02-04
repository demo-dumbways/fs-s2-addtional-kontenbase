---
sidebar_position: 8
---

# 8. Private Route

import useBaseUrl from '@docusaurus/useBaseUrl';

**Private Route** yang berfungsi untuk mengamankan route agar tidak bisa diakses ketika user belum login.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/8-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=pages/DetailUser.js
import { Outlet, Navigate } from "react-router-dom";

const PrivateRoute = ({ element: Component, ...rest }) => {
  const isSignin = false;

  return (
    isSignin ? <Outlet /> : <Navigate to="/signin" />
  );
};

export default PrivateRoute;
```

```jsx title=App.js {}
import "bootstrap/dist/css/bootstrap.min.css";
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import Profile from "./pages/Profile";
import SignIn from "./pages/SignIn";
import DetailUser from "./pages/DetailUser";
import PrivateRoute from "./components/PrivateRoute";

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
        <Route exact path="/signin" element={<SignIn />} />
        {/* protect this routes with <PrivateRoute> */}
        <Route exact path="/" element={<PrivateRoute />}>
          <Route exact path="/about" element={<About />} />
          <Route exact path="/profile" element={<Profile />} />
          <Route exact path="/users/:id" element={<DetailUser />} />
        </Route>
      </Routes>
    </Router>
  );
}

export default App
```

Dari code implementasi diatas kita membuat `private route` untuk component About, Profile dan Detail User, yang hanya bisa diakses ketika `islogin true`, jika mengakses private route ketika `islogin false `akan dialihkan ke component `SignIn`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-3.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-37d2af-demo-dumbways.vercel.app/">
Demo
</a>
</div>