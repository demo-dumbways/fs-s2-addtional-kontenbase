---
sidebar_position: 8
---

# 8. Full Code Post Blog

Berikut adalah Full Code terkait proses memposting blog :

```js title=blog.js
let blogs = [];

function addBlog(event) {
  event.preventDefault();

  let title = document.getElementById('input-blog-title').value;
  let content = document.getElementById('input-blog-content').value;
  let image = document.getElementById('input-blog-image');

  console.log(image)
  if (title == '' || image == '' || content == '') {
    return alert('All input fields must be not empty');
  }
  image = URL.createObjectURL(image.files[0]);

  document.getElementById('input-blog-title').value = ''

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

function renderBlog() {
  console.table(blogs);

  let blogContainer = document.getElementById('contents');

  blogContainer.innerHTML = firstBlogContent();

  for (let i = 0; i < blogs.length; i++) {
    console.log(blogs[i]);

    blogContainer.innerHTML += `
    <div id="${i}" class="blog-list-item">
      <div class="blog-image">
        <img src="${blogs[i].image}" alt="" />
      </div>
      <div class="blog-content">
        <div class="btn-group">
          <button class="btn-edit">Edit Post</button>
          <button class="btn-post">Post Blog</button>
        </div>
        <h1>
          <a href="blog-detail.html" target="_blank"
            >${blogs[i].title}</a
          >
        </h1>
        <div class="detail-blog-content">
          12 Jul 2021 22:30 WIB | ${blogs[i].author}
        </div>
        <p>${blogs[i].content}</p>
      </div>
    </div>
    `;
  }
}
```

Pada fungsi berikut berisikan beberapa penerapan code dasar pada JavaScript seperti:

- **Object :** tipe data non primitif untuk menyimpan banyak data dalam sebuah variabel dengan penamaan masing - masing
- **Array :** tipe data non primitif yang dapat digunakan untuk menyimpan daftar nilai
- **Looping / Perulangan :** proses mengeksekusi blok program secara berulang sebanyak yang diinginkan
