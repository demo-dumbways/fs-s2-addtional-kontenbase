---
sidebar_position: 5
---

# 5. Styling Navbar Menggunakan CSS External

Pada pertemuan pertemuan sebelumnya kita menggunakan gaya penulisan CSS Inline, kali ini kita akan menggunakan gaya penulisan menggunakan CSS External. **Eksternal CSS** adalah kode CSS yang ditulis terpisah dengan kode HTML Eksternal CSS ditulis di sebuah file khusus yang berekstensi `.css`. File eksternal CSS biasanya diletakkan setelah bagian `<head>` pada halaman. Cara ini lebih sederhana dan simpel daripada menambahkan kode CSS di setiap elemen HTML yang ingin Anda atur tampilannya.
Kita menggunakan CSS External agar Ukuran file HTML akan menjadi lebih kecil dan struktur dari kode HTML jadi lebih rapi. Loading website menjadi lebih cepat. File CSS dapat digunakan di beberapa halaman website sekaligus.


```css title="index.css"
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

/* Navbar */
nav {
  display: flex;
  background: #f4f3f3;
  height: 7vh;
}

nav div {
  display: flex;
  align-items: center;
  flex: 50%;
}

nav div.left-side {
  padding-left: 90px;
}

nav div.right-side {
  padding-right: 90px;
  display: flex;
  justify-content: flex-end;
}

nav ul {
  list-style-type: none;
  margin-left: 40px;
}

nav ul li {
  display: inline;
  margin-left: 40px;
}

nav ul li a {
  color: #000000;
  text-decoration: none;
}

nav ul li a.list-active {
  color: #ec4d37;
  font-weight: 700;
}

nav .right-side a {
  font-size: 15px;
  padding: 8px 20px;
  background-color: #ec4d37;
  border: none;
  border-radius: 10px;
  color: #fff;
  text-decoration: none;
}
```
