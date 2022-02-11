---
sidebar_position: 9
---

# 9. Prop Types

import useBaseUrl from '@docusaurus/useBaseUrl';

**Prop Types** berfungsi untuk membuat `type data` pada `props`, yang nantinya ketika dikirimkan pada `component` harus mengikuti aturan type data yang sudah ditentukan dalam `propTypes`.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/9-frontend-react-js-advance/src">
Contoh code
</a>

<br />
<br />

```jsx title=components/DetailAbout.js {1,6-8,13-17}
import PropTypes from "prop-types";

const DetailAbout = (props) => {
  return (
    <>
      <h1>title: {props.title}</h1>
      <p>summary: {props.summary}</p>
      <p>total guest: {props.total}</p>
    </>
  );
};

DetailAbout.propTypes = {
  title: PropTypes.string.isRequired,
  summary: PropTypes.string,
  total: PropTypes.number,
};

export default DetailAbout;
```

```jsx title=pages/About.js {2,13-17}
import { Container } from "react-bootstrap";
import DetailAbout from "../components/DetailAbout";

const About = () => {
  return (
    <Container className="text-center">
      <p className="h1">About Us</p>
      <p>
        Maecenas bibendum vel tortor non congue. Maecenas at sodales turpis, id
        maximus odio. Donec aliquet elementum mauris, vel semper tortor ultrices
        a.
      </p>
      <DetailAbout
        title="Success.ltd"
        summary="No. 1 Automobile company in USA"
        total={1300}
      />
    </Container>
  );
};

export default About;
```

Dari code implementasi diatas kita membuat `type data` pada `props title bertipe string, summary type string dan total number`, dicomponent `About` yang dikirimkan harus sesuai dengan yang dibuat pada `propTypes` component `DetailAbout`.

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-9.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-3-frontend-37d2af-demo-dumbways.vercel.app/">
Demo
</a>
</div>