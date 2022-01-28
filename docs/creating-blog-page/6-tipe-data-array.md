---
sidebar_position: 6
---

# 6. Menyimpan Data Postingan Blog kedalam Array

import useBaseUrl from '@docusaurus/useBaseUrl';

Setelah kita menyimpan seluruh data postingan blog kedalam object, kita akan menyimpannya kedalam sebuah `array`. Tujuannya yakni agar seluruh postingan nantinya tersimpan dan bisa ditampilkan kedalam halaman blog secara dinamis. **Tipe data array** adalah tipe data yang mampu menyimpan daftar data didalam satu buah variabel. Menyimpan data kedalam array menggunkan method push.

Ilustrasi array dapat dilihat pada gambar berikut:

<img alt="image2" src={useBaseUrl('img/docs/image-20.png')} height="300px"/>

```js {1, 28}
let blogs = [];

function addBlog(event) {
    event.preventDefault();
  
    let title = document.getElementById('input-blog-title').value;
    let content = document.getElementById('input-blog-content').value;
    let image = document.getElementById('input-blog-image');
  
    image = URL.createObjectURL(image.files[0]);
    
    console.log(image)
    if (title == '' || image == '' || content == '') {
      return alert('All input fields must be not empty');
    }
  
    document.getElementById('input-blog-title').value = ''
    document.getElementById('input-blog-content').value = ''
  
    let blog = {
      author: 'Rhoma Irama',
      title: title,
      image: image,
      content: content,
      postedAt: new Date(),
    };

    blogs.push(blog);

    renderBlog();
}
```