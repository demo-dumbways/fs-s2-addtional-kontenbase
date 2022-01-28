---
sidebar_position: 4
---

# 4. Menampung Data Postingan Blog

Sebelum kita menyimpan data postingan blog kedalam `array`, kita perlu menampung data setiap inputan ke masing - masing `variabel`. setelah ditampung kedalam variabel, maka kita perlu melakukan pengecekan apakah data inputan terdapat data yang dikirimkan. Hal ini kita lakukan menggunakan `DOM`, sama halnya seperti pada pertemuan sebelumnya terkait menampung data dari formulir contact me.

```js 
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
}
```