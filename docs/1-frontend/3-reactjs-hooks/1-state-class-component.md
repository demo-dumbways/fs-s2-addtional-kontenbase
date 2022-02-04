---
sidebar_position: 1
---

# 1. State Class Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**Hooks** merupakan fitur baru pada React versi 16.8. `Hooks` memungkinkan kita menggunakan `state` dan fitur React lainnya tanpa membuat sebuah `class component`.

contoh menggunakan functional component
```
function Welcome() {
  return <h1>Hallo World/h1>;
}
```

contoh menggunakan class component
```
class Welcome extends React.Component {
  render() {
    return <h1>Hallo World</h1>;
  }
}
```

Berikut contoh implementasi `State Class Components`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/1-frontend-react-js-hooks/src/ExampleForm.js">
Contoh code
</a>

<br />
<br />

```jsx title=ExampleForm.js {7-10,16-17,22-23}
import React, { Component } from "react";
import { Container, Row, Col, Form, Button } from "react-bootstrap";

class ExampleForm extends Component {
  constructor(props) {
    super(props);
    this.state = {
      fullname: "",
      email: "",
      password: "",
    };
  }

  handleOnChange = (e) => {
    this.setState({
      ...this.state,
      [e.target.name]: e.target.value,
    });
  };

  handleOnSubmit = (e) => {
    e.preventDefault();
    console.log(this.state);
  };

  render() {
    return (
      <Container>
        <Row className="d-flex align-items-center justify-content-center vh-100">
          <Col md="6">
            <Form onSubmit={this.handleOnSubmit}>
              <div className="text-center h3">Register</div>
              <Form.Group className="mb-3" controlId="formFullName">
                <Form.Label>Full Name</Form.Label>
                <Form.Control
                  onChange={this.handleOnChange}
                  value={this.state.fullname}
                  name="fullname"
                  size="sm"
                  type="text"
                  placeholder="Enter Full Name"
                />
              </Form.Group>

              <Form.Group className="mb-3" controlId="formBasicEmail">
                <Form.Label>Email address</Form.Label>
                <Form.Control
                  onChange={this.handleOnChange}
                  value={this.state.email}
                  name="email"
                  size="sm"
                  type="email"
                  placeholder="Enter email"
                />
              </Form.Group>

              <Form.Group className="mb-3" controlId="formBasicPassword">
                <Form.Label>Password</Form.Label>
                <Form.Control
                  onChange={this.handleOnChange}
                  value={this.state.password}
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
}

export default ExampleForm;
```

Dari code implementasi diatas kita membuat `state` dengan type data `object` yang propetynya `fullname`, `email` dan `password` dengan data `string kosong`, yang dimana datanya `diubah` dengan `data` yang diinputkan pada tag `input` dan disimpan kedalam `state`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-3-1.png')} width="60%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-1-frontend-45c330-demo-dumbways.vercel.app/">
Demo
</a>
</div>