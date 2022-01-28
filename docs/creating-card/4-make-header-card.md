---
sidebar_position: 4
---

# 4. Make Card Header 

import useBaseUrl from '@docusaurus/useBaseUrl';

Card yang dibuat dibagi kedalam dua bagian, yakni untuk `header dan content`. Bagian header diisikan menggunakan tag heading atau dituliskannya adalah tag H untuk menampilkan nama kita. Tag heading kita gunakan agar tampak berbeda dengan konten lainnya.

<br />
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-1/tree/day1-3.card-header">
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
    <div>
      <h1 style="text-align: left">Rhoma Irama</h1>
    </div>
  </div>
</body>
</html>
```

<img alt="image1-2" src={useBaseUrl('img/docs/image-1-2.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-1-git-day1-3card-header-demo-dumbways.vercel.app">
Demo
</a>
</div>
