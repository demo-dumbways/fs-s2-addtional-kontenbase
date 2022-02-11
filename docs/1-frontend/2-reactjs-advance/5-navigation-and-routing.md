---
sidebar_position: 5
---

# 5. Navigation And Routing

import useBaseUrl from '@docusaurus/useBaseUrl';

**Navigation dan Routing** pada Ract Js menggunakan `react-router-dom` yang berfungsi untuk membuat `route` dan berpindah antar `halaman` sesuai dengan `routenya`.

Lakukan instalasi dengan perintah: 
```bash
npm install react-router-dom
```

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/5-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js {3,5-8,12-37}
import "bootstrap/dist/css/bootstrap.min.css";

import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";

import Home from "./pages/Home";
import About from "./pages/About";
import Profile from "./pages/Profile";
import SignIn from "./pages/SignIn";

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
            <li>
              <Link to="/signin">Sign in</Link>
            </li>
          </ul>
        </nav>
      </div>
      <Routes>
        <Route exact path="/" element={<Home />} />
        <Route exact path="/about" element={<About />} />
        <Route exact path="/profile" element={<Profile />} />
        <Route exact path="/signin" element={<SignIn />} />
      </Routes>
    </Router>
  );
}

export default App;
```

Dari code implementasi diatas kita menggunakan package `react-router-dom` yang berfungsi untuk membuat `route` dengan menggunakan `Router`, `Switch`, `Route` dan `Link` untuk berpindah antar halaman.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-5.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-5-frontend-b3f573-demo-dumbways.vercel.app/">
Demo
</a>
</div>