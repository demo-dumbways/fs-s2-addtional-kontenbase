---
sidebar_position: 4
---

# 4. Menambahkan Button "Contact Me" pada Navigation Bar

Button tidak hanya bisa digunakan pada sebuah formulir, button juga bisa kita gunakan tanpa formulir. Hanya saja kita mengubah nilai properti type pada button menjadi `bertipekan button`. Selain mengubah properti type, kita juga akan menambahkan sebuah `tag anchor` agar nantinya button bisa diklik dan mengarahkan ke halaman lainnya. **Tag anchor** merupakan sebuah tag yang dapat menampung hypertext link.

```html {18-22} title=index.html
<!DOCTYPE html>
<head>
  <title>Navigation Bar</title>
</head>
<body>
  <nav>
    <div>
      <img src="assets/logo.png" />
      <ul>
        <li>
          <a href=""> Home </a>
        </li>
        <li>
          <a href="">Blog</a>
        </li>
      </ul>
    </div>
    <div>
      <a href="">
        Contact Me
      <a>
    </div>
  </nav>
</body>
</html>
```
