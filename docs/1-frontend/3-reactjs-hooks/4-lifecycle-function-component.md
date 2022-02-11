---
sidebar_position: 4
---

# 4. Lifecycle Function Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**Lifecycle Functional Component** secara fungsi lifecycle pada functional component kurang lebih sama seperti class component, dimana yang berbeda hanya pada bentuk penulisan yang dimana kita diharuskan menggunakan sebuah `hooks` yaitu `useEffect`.

Berikut contoh code implementasi:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/4-frontend-react-js-hooks/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js {1,18-21,24-29}
import React, { useState, useEffect } from "react";
import { Container, Row, Col, Form, Button } from "react-bootstrap";

import Welcome from "./Welcome";
import GuestGreeting from "./GuestGreeting";

function App() {
  const [state, setState] = useState({
    isLogin: false,
    user: {
      email: "",
      password: "",
    },
  });

  // Did Mount
  useEffect(() => {
    console.log("App Component Did Mount");
    console.log(state);
  }, []);

  // Did Update
  useEffect(() => {
    if (state.user.email) {
      console.log("App Component Did Update");
      console.log(state);
    }
  }, [state]);

  const handleOnSubmit = (e) => {
    e.preventDefault();
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;
    setState({
      isLogin: true,
      user: {
        email,
        password,
      },
    });
  };

  return (
    <>
      {state.isLogin ? (
        <Welcome />
      ) : (
        <>
          <GuestGreeting />
          <Container>
            <Row className="d-flex justify-content-center mt-5">
              <Col md="4">
                <Form onSubmit={handleOnSubmit}>
                  <div className="text-center h5">Login</div>

                  <Form.Group className="mb-3" controlId="formBasicEmail">
                    <Form.Label>Email address</Form.Label>
                    <Form.Control
                      id="email"
                      name="email"
                      size="sm"
                      type="email"
                      placeholder="Enter email"
                    />
                  </Form.Group>

                  <Form.Group className="mb-3" controlId="formBasicPassword">
                    <Form.Label>Password</Form.Label>
                    <Form.Control
                      id="password"
                      name="password"
                      size="sm"
                      type="password"
                      placeholder="Password"
                    />
                  </Form.Group>

                  <Button variant="primary" type="submit" size="sm">
                    Submit
                  </Button>
                </Form>
              </Col>
            </Row>
          </Container>
        </>
      )}
    </>
  );
}

export default App;
```

```jsx title=GuestGreeting.js {1,5-10}
import React, { useEffect } from "react";

export default function GuestGreeting() {
  useEffect(() => {
    console.log("Guest Greeting Component Did Mount");
    return () => {
      console.log("Guest Greeting Component Will Unmount");
    };
  }, []);

  return (
    <div className="text-center h1 bg-secondary text-light py-5">
      Please Login !
    </div>
  );
}
```

```jsx title=Welcome.js {1,5-10}
import React, { useEffect } from "react";

export default function Welcome() {
  useEffect(() => {
    console.log("Welcome Component Did Mount");
    return () => {
      console.log("Welcome Component Will Unmount");
    };
  }, []);

  return (
    <div className="vh-100 bg-warning d-flex justify-content-center align-items-center h1 mb-0">
      Welcome
    </div>
  );
}
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-3-3.png')} width="100%"/>
<img alt="image1-2" src={useBaseUrl('img/docs/image-3-4.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-eui2mcltz-demo-dumbways.vercel.app/">
Demo
</a>
</div>
