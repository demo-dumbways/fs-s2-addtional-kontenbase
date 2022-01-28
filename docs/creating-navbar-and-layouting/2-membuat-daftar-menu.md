---
sidebar_position: 2
---

# 2. Membuat Daftar Menu

Membuat daftar menu pada case, kita bisa memanfaatkan tag list pada HTML. Tag list sendiri terbagi menjadi 2 yakni unordered list `<ul></ul>` dan ordered list `<ol></ol>`.

**Unordered list** dapat kita gunakan ketika menampilkan list yang tidak berurutan, sedangkan **ordered list** dapat digunakan ketika kita membuat list secara berurutan. Disini kita akan menggunakan unordered list, untuk membuat daftar menu.

```html {8-15} title=index.html
<!DOCTYPE html>
<head>
  <title>Navigation Bar</title>
</head>
<body>
  <nav>
    <div>
      <ul>
        <li>
          <a href=""> Home </a>
        </li>
        <li>
          <a href="">Blog</a>
        </li>
      </ul>
    </div>
  </nav>
</body>
</html>
```
