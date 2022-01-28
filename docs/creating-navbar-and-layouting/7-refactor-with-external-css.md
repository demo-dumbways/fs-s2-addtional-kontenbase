---
sidebar_position: 7
---

# 7. Refactor Styling Menggunakan CSS Eksternal

Pada pertemuan pertemuan sebelumnya kita menggunakan gaya penulisan CSS Inline, kali ini kita akan refactor gaya penulisan menggunakan CSS External. **Eksternal CSS** adalah kode CSS yang ditulis terpisah dengan kode HTML Eksternal CSS ditulis di sebuah file khusus yang berekstensi .css.

File eksternal CSS biasanya diletakkan setelah bagian `<head>` pada halaman. Cara ini lebih sederhana dan simpel daripada menambahkan kode CSS di setiap elemen HTML yang ingin Anda atur tampilannya.

Kita menggunakan CSS External agar Ukuran file HTML akan menjadi lebih kecil dan struktur dari kode HTML jadi lebih rapi. Loading website menjadi lebih cepat. File CSS dapat digunakan di beberapa halaman website sekaligus.

```css {1,10-160} title="index.css"
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

/* Card Profile */

.personal {
  display: flex;
  height: 93vh;
}

.personal .left {
  flex: 40%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

.card {
  width: 450px;
  border: 1px solid #00000033;
  border-radius: 16px;
  padding: 15px 15px 25px 15px;
  box-shadow: 0px 0px 20px #00000040;
}

.card .image img {
  width: 100%;
  border-radius: 16px;
}

.card .header h1 {
  text-align: left;
  margin: 10px 0;
}

.card .content p {
  text-align: left;
  color: rgba(0, 0, 0, 0.6);
  line-height: 120%;
  margin-bottom: 20px;
}

.card .content table {
  width: 100%;
  border: 2px solid rgb(116, 116, 116);
  border-radius: 1em;
  border-collapse: collapse;
}

.card .content table tr th {
  font-weight: 600;
  padding: 5px;
}

.card .content table tr td {
  font-weight: 300;
  padding: 5px;
  text-align: center;
}

.personal .right {
  flex: 60%;
  display: flex;
  position: relative;
}

.personal .right div {
  position: absolute;
  top: 100px;
  left: 40px;
  right: 80px;
}

.personal .right div p {
  text-align: justify;
  color: #959595;
  margin-top: 20px;
  margin-bottom: 20px;
}

.personal .right .skill {
  display: flex;
}

.personal .right .skill span {
  flex: 1;
  margin-right: 10px;
}

.personal .right .skill img {
  width: 60px;
  height: 60px;
  object-fit: cover;
}
.personal .right .skill p {
  text-align: left;
}

.personal .right .sosmed-list {
  position: absolute;
  margin-top: 20px;
}

.personal .right .sosmed-list a {
  cursor: pointer;
  margin-right: 10px;
}

.personal .right .sosmed-list a img {
  cursor: pointer;
  width: 40px;
}

/* Form Contact */

.form-contact {
  height: 93vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.form-contact form label {
  font-size: 20px;
  font-weight: 400;
}

.form-contact form input,
textarea,
select {
  width: 100%;
  font-size: 20px;
  font-weight: 400;
  padding: 8px;
  margin-top: 5px;
  margin-bottom: 20px;
  background: #f4f3f3;
  border: 1px solid #c4c4c4;
  border-radius: 8px;
}

.form-contact form textarea {
  height: 100px;
}

.form-contact form button {
  padding: 8px 30px;
  font-size: 17px;
  background: #ec4d37;
  border-radius: 10px;
  border: none;
  color: #fff;
  cursor: pointer;
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

Pada file `.css` ini kita juga menambahkan styling untuk `font-family`, **font-family** merupakan properti yang digunakan untuk menentukan dan merubah jenis font yang digunakan pada teks. Selain styling pada font, kita juga menambahkan styling pada card kita dengan menambahkan property `box-shadow` agar memiliki bayangan pada setiap sisinya.

Agar sudut dari card tidak lancip, kita bisa menggunakan` border-radius` untuk mengubah nya menjadi rounded. Tampilan card pada mockup terlihat memiliki bayangan pada setiap sisinya, untuk melakukan styling tersebut kita bisa menggunakan atribut `box-shadow`.
