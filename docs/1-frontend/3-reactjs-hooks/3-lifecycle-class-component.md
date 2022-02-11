---
sidebar_position: 3
---

# 3. Lifecycle Class Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**Lifecycle Class Component** Setiap React component akan melewati 3 fase lifecycle, yang dimana ada component DidMount Fase dimana component dibuat dan mulai ditambahkan ke DOM, component DidUpdate Fase dimana component di-render ulang karena perubahan props dan state, component WillUnMount Fase dimana sebuah component dihapus dari DOM.

Berikut contoh code implementasi:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-hooks/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js {20-23,25-28}
import React, { Component } from 'react'
import { Container, Row, Col, Form, Button } from 'react-bootstrap'

import Welcome from './Welcome'
import GuestGreeting from './GuestGreeting'

export default class App extends Component {

  constructor(){
      super()
      this.state = {
          isLogin: false,
          user: {
              email: '',
              password: ''
          }
      }
  }

  componentDidMount(){
      console.log("App Component Did Mount")
      console.log(this.state)
  }

  componentDidUpdate(){
      console.log("App Component Did Update")
      console.log(this.state)
  }

  handleOnSubmit = (e) => {
      e.preventDefault()
      const email = document.getElementById('email').value
      const password = document.getElementById('password').value
      this.setState({
          isLogin: true,
          user: { 
              email,
              password
          }
      })
      console.log(this.state)
  }

  render() {
    return (
      <>
        {this.state.isLogin ? <Welcome /> : 
          (<>
            <GuestGreeting />
            <Container>
              <Row 
              className="d-flex justify-content-center mt-5">
                <Col md="4">
                  <Form onSubmit={this.handleOnSubmit}>
                      <div className="text-center h5">Login</div>

                      <Form.Group className="mb-3" controlId="formBasicEmail">
                      <Form.Label>Email address</Form.Label>
                      <Form.Control 
                          id="email"
                          name="email" size="sm" type="email" 
                          placeholder="Enter email" />
                      </Form.Group>

                      <Form.Group className="mb-3" controlId="formBasicPassword">
                      <Form.Label>Password</Form.Label>
                      <Form.Control 
                          id="password"
                          name="password" size="sm" type="password" 
                          placeholder="Password" />
                      </Form.Group>

                      <Button variant="primary" type="submit" size="sm">
                          Submit
                      </Button>
                  </Form>
                </Col>
              </Row>
            </Container>
          </>) }
      </>
    )
  }
}
```

```jsx title=GuestGreeting.js {5-7}
import React, { Component } from 'react'

export default class GuestGreeting extends Component {

    componentWillUnmount(){
        console.log("Guest Greeting Component Will Unmount")
    }

    render() {
        return (
            <div className="text-center h1 bg-secondary text-light py-5">
                Please Login !
            </div>
        )
    }
}
```

```jsx title=Welcome.js {5-7,9-11}
import React, { Component } from 'react'

export default class Welcome extends Component {

  componentDidMount(){
      console.log("Welcome Component Did Mount")
  }

  componentWillUnmount(){
      console.log("Welcome Component  Will Unmount")
  }

  render() {
      return (
          <div className="vh-100 bg-warning d-flex justify-content-center align-items-center h1 mb-0">
              Welcome
          </div>
      )
  }
}

```

<img alt="image1-2" src={useBaseUrl('img/docs/image-3-3.png')} width="100%"/>
<img alt="image1-2" src={useBaseUrl('img/docs/image-3-4.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-132813-demo-dumbways.vercel.app/">
Demo
</a>
</div>