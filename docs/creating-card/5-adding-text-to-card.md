---
sidebar_position: 5
---

# 5. Adding Text to Card

import useBaseUrl from '@docusaurus/useBaseUrl';

Pada bagian content kita bisa menambahkan penggunaan `tag paragraf` atau dituliskan tag p untuk menampilkan profil singkat terkait diri kita, bisa berupa motto. Tag p digunakan karena sesuai dalam menampilkan teks motto dalam bentuk paragraf.

<br />
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-1/tree/day1-4.card-text">
Contoh code
</a>

<br />
<br />

```html {18-20} title="index.html"
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

<img alt="image1-3" src={useBaseUrl('img/docs/image-1-3.png')} height="500px"/>
<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-1-git-day1-4card-text-demo-dumbways.vercel.app">
Demo
</a>
</div>

<br />

Dan jangan lupa untuk kita berikan styling agar tampak lebih rapi, styling yang bisa kita gunakan adalah `font-size, font-weight, padding, dll`.

Mengatur ukuran dari font yang kita gunakan bisa menggunakan atribut font-size dengan memberikan nilai - nilai tertentu. Sedangkan untuk ketebalan dari font, kita bisa gunakan font weight.
