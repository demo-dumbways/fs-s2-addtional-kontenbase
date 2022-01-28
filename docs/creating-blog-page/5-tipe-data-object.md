---
sidebar_position: 5
---

# 5. Tipe Data Object

Setelah kita menampung data inputan kedalam variabel dan memvalidasinya, kita akan menyatukan seluruh variabel tersebut kedalam sebuah variabel bertipekan `object`. **Tipe data object** berisi data yang banyak didalam sebuah variabel. Setiap data yang disimpan memiliki nama masing - masing yang biasa disebut sebagai properti.

```js {18-24}
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
}
```