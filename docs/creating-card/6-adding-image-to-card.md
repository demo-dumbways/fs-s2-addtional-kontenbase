---
sidebar_position: 6
---

# 6. Adding Image to Card

import useBaseUrl from '@docusaurus/useBaseUrl';

Menambahkan image atau gambar kedalam card, kita bisa menggunakan `tag img`. Pada tag img kita membutuhkan `atribut src` untuk memanggil alamat/direktori dari gambar yang akan ditampilkan.
<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-1/tree/day1-5.card-image">
Contoh code
</a>

<br />
<br />

```html {15} title="index.html"
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
      <img src="assets/my-img.jpg" alt="my image" />
    </div>
    <div>
      <h1 style="text-align: left">Rhoma Irama</h1>
    </div>
    <div>
      <p style="text-align: left; color: rgba(0, 0, 0, 0.6)">
        I became a superstar to make awesome app and software to bring new life for mankind.
      </p>
    </div>
  </div>
</body>
</html>
```

<img alt="image1-4" src={useBaseUrl('img/docs/image-1-4.png')} height="500px"/>
<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-1-git-day1-5card-image-demo-dumbways.vercel.app">
Demo
</a>
</div>

<br />
<br />

Ditambahkan pula styling agar image yang ditambahkan tampak lebih rapi dan indah. Styling bisa digunakan adalah width.

<br />
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-1/tree/day1-6.card-image-styling">
Contoh code
</a>

<br />
<br />

```html {15} title="index.html"
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
    </div>
  </div>
</body>
</html>
```

<img alt="image1-5" src={useBaseUrl('img/docs/image-1-5.png')} height="500px"/>
<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-1-git-day1-6card-ad1cad-demo-dumbways.vercel.app">
Demo
</a>
</div>
