---
sidebar_position: 6
---

# 6. Use Navigate

import useBaseUrl from '@docusaurus/useBaseUrl';

**Use Navigate** adalah sebuah fungsi `hook` dimana berfungsi untuk menavigasikan secara terprogram misalnya ketika mengeksekusi sebuah fungsi tertentu sebelum halaman yang dituju.

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/blob/6-frontend-react-js-advance/src/pages/Home.js">
Contoh code
</a>

<br />
<br />

```jsx title=pages/Home.js {2,5,7-9,24}
import { Container, Button } from "react-bootstrap";
import { useNavigate } from "react-router-dom";

function Home() {
  const navigate = useNavigate();

  const handleNaviateToSignIn = () => {
    navigate("/signin");
  };

  return (
    <Container className="text-center">
      <p className="h1">Home</p>
      <p>
        Cras sit amet mauris ac urna pellentesque rhoncus sed nec felis. Sed
        augue tortor, pretium euismod massa eu, fringilla viverra ante. Proin ut
        nisl neque. In varius nibh eget diam pharetra, sed gravida sem commodo.
        Proin in tortor tristique lorem dignissim elementum. Quisque gravida
        augue quis aliquam ultrices. Nullam risus est, malesuada vitae pretium
        eu, congue a magna. Orci varius natoque penatibus et magnis dis
        parturient montes, nascetur ridiculus mus. Donec et maximus tellus, sit
        amet hendrerit augue.
      </p>
      <Button onClick={handleNaviateToSignIn}>Click to Signin</Button>
    </Container>
  );
}

export default Home;
```

Dari code implementasi diatas kita menggunakan `useNavigate` untuk bernavigasi ke halaman yang dituju, ketika tombol `Click to SignIn` diklik, akan menjalan sebuah `function` yang didalamnya terdapat navigasi ke sebuah route `/signin`

<img alt="image1-2" src={useBaseUrl('img/docs/image-2-6.png')} width="100%"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-results-stage-2-git-6-frontend-35dc2f-demo-dumbways.vercel.app/">
Demo
</a>
</div>
