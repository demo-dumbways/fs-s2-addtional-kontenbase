---
sidebar_position: 7
---

# 7. Menampilkan List Blog

Data postingan blog yang sudah tersimpan didalam array akan ditampilkan ke halaman blog. Menampilkan data postingan blog yang tersimpan didalam array dapat menggunakan `perulangan`. **Perulangan** adalah suatu proses mengeksekusi blok program secara berulang sebanyak yang diinginkan. Sehingga kita bisa menggunakan perulangan untuk mengakses setiap data yang tersimpan didalam indeks array.

```js
function renderBlog() {
  let blogContainer = document.getElementById('contents');

  blogContainer.innerHTML = firstBlogContent();

  for (let i = 0; i < blogs.length; i++) {
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

Pada code diatas, kita mengakses data pada array menggunakan perulangan yang selanjutnya kita kombinasikan menggunakan DOM `.innerHTML` untuk mengirimkan data - data postingan blog kedalam tampilan list blog. 
**innerHTML** merupakan sebuah atribut didalam object elemen HTML yang berisi string HTML, sehingga memungkinakan kita mengirimkan string disertai tag - tag HTML yang nantinya akan dirender oleh browser sebagai code HTML.