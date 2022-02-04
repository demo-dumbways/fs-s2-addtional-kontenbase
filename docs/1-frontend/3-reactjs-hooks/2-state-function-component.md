---
sidebar_position: 2
---

# 2. State Function Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**State Functional Component** dengan adanya `hooks` kita bisa membuat state dalam `functional component` dengan menggunakan `useState`, Sebelumnya `state` hanya bisa dibuat pada `class components`.

Berikut contoh implementasi `State Functional Components`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/2-frontend-react-js-hooks/src/ExampleForm.js">
Contoh code
</a>

<br />
<br />

```jsx title=ExampleForm.js {1,5-9,12-15,19-20}
import React, { useState } from "react";
import { Container, Row, Col, Form, Button } from "react-bootstrap";

function ExampleForm() {
  const [state, setState] = useState({
    fullname: "",
    email: "",
    password: "",
  });

  const handleOnChange = (e) => {
    setState({
      ...state,
      [e.target.name]: e.target.value,
    });
  };

  const handleOnSubmit = (e) => {
    e.preventDefault();
    console.log(state);
  };

  return (
    <Container>
      <Row className="d-flex align-items-center justify-content-center vh-100">
        <Col md="6">
          <Form onSubmit={handleOnSubmit}>
            <div className="text-center h3">Register</div>
            <Form.Group className="mb-3" controlId="formFullName">
              <Form.Label>Full Name</Form.Label>
              <Form.Control
                onChange={handleOnChange}
                value={state.fullname}
                name="fullname"
                size="sm"
                type="text"
                placeholder="Enter Full Name"
              />
            </Form.Group>

            <Form.Group className="mb-3" controlId="formBasicEmail">
              <Form.Label>Email address</Form.Label>
              <Form.Control
                onChange={handleOnChange}
                value={state.email}
                name="email"
                size="sm"
                type="email"
                placeholder="Enter email"
              />
            </Form.Group>

            <Form.Group className="mb-3" controlId="formBasicPassword">
              <Form.Label>Password</Form.Label>
              <Form.Control
                onChange={handleOnChange}
                value={state.password}
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
  );
}

export default ExampleForm;
```

Dari code implementasi diatas kita membuat `state` dengan type data `object` yang propetynya `fullname`, `email` dan `password` dengan data `string kosong`, yang dimana datanya `diubah` dengan `data` yang diinputkan pada tag `input` dan disimpan kedalam `state`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-3-2.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-2-frontend-27e266-demo-dumbways.vercel.app/">
Demo
</a>
</div>