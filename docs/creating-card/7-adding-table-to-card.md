---
sidebar_position: 7
---

# 7. Adding Table to Card

import useBaseUrl from '@docusaurus/useBaseUrl';

Membuat elemen table kita membutuhkan beberapa tag, yakni `tag table, tag table row, dan tag table data`. Menggunakan tag table kita bisa menyajikan data dalam bentuk grid yang terdiri dari kolom dan baris.
Table di dalam HTML dibentuk dengan sebuah baris (row), tepatnya menggunakan element `<tr>` yang merupakan kepanjangan dari table row. Adapun elemen pendukung lain yang membentuk sebuah table adalah `<th>` (table header) dan `<td>` (table data). `<td>` menunjukkan sebuah cell, sedangkan `<th>` menunjukkan cell induk dan ditandai dengan tulisan cetak tebal.
Table juga bisa diberikan styling menggunakan css, styling yang bisa kita gunakan adalah `border radius, dll`

<br />
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-1/tree/day1-7.card-table">
Contoh code
</a>

<br />
<br />

```html {24-40} title="index.html"
<!DOCTYPE html>
<head>
  <title>Creating Card</title>
</head>
<body>
  <div style="
    margin-top: 150px;
    width: 350px;
    border-radius: 16px;
    padding: 15px;
    border: 1px solid #00000033;
    box-shadow: 0px 0px 20px #00000040;
    ">
    <div class="image">
      <img src="assets/my-img.jpg" alt="my image" style="width: 100%; border-radius: 16px" />
    </div>
    <div>
      <h1 style="text-align: left">Rhoma Irama</h1>
    </div>
    <div>
      <p style="text-align: left; color: rgba(0, 0, 0, 0.6)">
        I became a superstar to make awesome app and software to bring new life for mankind.
      </p>
      <table border="1" style="
        width: 100%;
        border: 2px solid rgb(156, 156, 156);
        border-radius: 10px;
        border-collapse: collapse;
        ">
          <tr>
            <th style="padding: 5px">Project Name</th>
            <th>Year</th>
          </tr>
          <tr>
            <td style="padding: 5px; text-align: center">
              Dumbways Mobile App
            </td>
            <td style="padding: 5px; text-align: center">2021</td>
          </tr>
        </table>
    </div>
  </div>
</body>
</html>
```

<img alt="image1-6" src={useBaseUrl('img/docs/image-1-6.png')} height="500px"/>
<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-1-git-day1-7card-table-demo-dumbways.vercel.app">
Demo
</a>
</div>
