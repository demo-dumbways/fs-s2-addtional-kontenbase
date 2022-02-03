---
sidebar_position: 5
---

# 5. Navigation And Routing

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan memeplajari terkait `Navigation and Routing` yang berfungsi untuk berpindah halaman sesuai dengan routenya. 

tambahkan code berikut di `App.js`

```js
import "bootstrap/dist/css/bootstrap.min.css";

// import necessary object from react-router-dom
import { BrowserRouter as Router, Route, Switch, Link } from "react-router-dom";

// import our "page-like" component
import Home from "./pages/Home";
import About from "./pages/About";
import Profile from "./pages/Profile";
import SignIn from "./pages/SignIn";

function App() {
  return (
    <Router>
      <div>
        {/* Setup navigation element */}
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
      {/* define Route and component that will 
      render if the URL match by using Switch */}
      <Switch>
        <Route exact path="/" component={Home} />
        <Route exact path="/about" component={About} />
        <Route exact path="/profile" component={Profile} />
        <Route exact path="/signin" component={SignIn} />
      </Switch>
    </Router>
  );
}

export default App;
```

Penjelasan code diatas adalah kita menggunakan package `react-router-dom` yang dimana berfungsi untuk berpindah antar halaman menggunakan `Router`, `Switch`, `Route` dan `Link` yang terdapat `pada react-router-dom`