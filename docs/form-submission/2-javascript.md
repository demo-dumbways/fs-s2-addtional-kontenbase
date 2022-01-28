---
sidebar_position: 2
---

# 2. JavaScript

**JavaScript** adalah bahasa pemrograman yang digunakan dalam pengembangan website agar lebih dinamis dan interaktif. Kalau sebelumnya kamu hanya mengenal HTML dan CSS, nah sekarang kamu jadi tahu bahwa JavaScript dapat meningkatkan fungsionalitas pada halaman web.

Kita akan menggunakan function dalam case ini.**Fungsi atau function** di JavaScript adalah sebuah blok kode yang digunakan untuk membungkus suatu proses dengan tujuan agar penulisan kode atau proses yang sama tidak ditulis secara berulang kali. Function dapat dituliskan sebagai berikut:

```
function functionName () {
    //code here
}
```

Kita akan menampikan data melalui `alert` menggunakan javascript. Pertama yang kita lakukan adalah menentukan darimana data yang akan dikirimkan, kita bisa menggunakan `DOM` untuk menentukannya.

```js
const emailReciver = 'rhomairama.dev@gmail.com';

let name = document.getElementById('input-name');
let email = document.getElementById('input-email');
let phone = document.getElementById('input-phone');
let subject = document.getElementById('input-subject');
let message = document.getElementById('input-message');
```

Setelah kita mengetahui darimana data akan dikirimkan maka kita akan menampung inputan form kedalam variabel. Variabel adalah sebuah nama yang mewakili sebuah nilai. `Variabel` bisa diisi dengan berbagai macam nilai seperti `string (teks)`, `number (angka)`, dll.

```js
function submitForm() {
  name = name.value;
  email = email.value;
  phone = phone.value;
  subject = subject.value;
  message = message.value;
}
```

Selain digunakan untuk menerima submission dari form, function disini kita gunakan juga untuk melakukan validasi inputan dengan menggunakan kondisional seperti `if`, JavaScript memungkinkan kita untuk menulis kode dengan kinerja yang berbeda tindakan berdasarkan hasil dari kondisi pengujian logis atau komparatif pada saat dijalankan. Artinya, kita bisa buat kondisi pengujian dalam bentuk ekspresi yang mengevaluasi benar atau salah dan berdasarkan hasil pengecekan kondisi.

```js {8-18}
function submitForm() {
  name = name.value;
  email = email.value;
  phone = phone.value;
  subject = subject.value;
  message = message.value;

  if (name == '') {
    return alert('Name input fields must be not empty');
  } else if (email == '') {
    return alert('Email input fields must be not empty');
  } else if (phone == '') {
    return alert('Phone input fields must be not empty');
  } else if (subject == '') {
    return alert('Subject input fields must be not empty');
  } else if (message == '') {
    return alert('Message input fields must be not empty');
  }
}
```

Kita bisa pula menambahkan hal lainnya selain menampilkan datanya, yakni kita bisa mengirim pesan email menggunakan data yang sudah kita tampung kedalam `variabel`. Kita akan memanfaatkan sebuah method dengan nama `createElement()` untuk melakukan penambahan elemen `anchor`.

Berikut adalah Full Code di atas :

```js {20-25} title=index.js
const emailReciver = "rhomairama.dev@gmail.com";

let name = document.getElementById("input-name");
let email = document.getElementById("input-email");
let phone = document.getElementById("input-phone");
let subject = document.getElementById("input-subject");
let message = document.getElementById("input-message");

function submitForm() {
  name = name.value;
  email = email.value;
  phone = phone.value;
  subject = subject.value;
  message = message.value;

  if (name == '') {
    return alert('Name input fields must be not empty');
  } else if (email == '') {
    return alert('Email input fields must be not empty');
  } else if (phone == '') {
    return alert('Phone input fields must be not empty');
  } else if (subject == '') {
    return alert('Subject input fields must be not empty');
  } else if (message == '') {
    return alert('Message input fields must be not empty');
  }

  const a = document.createElement("a");

  a.href = `mailto:${emailReciver}?subject=${subject}&body=Hello my name ${name}, ${subject}, ${message}`;
  a.target = "_blank";
  a.click();
}
```

selain disimpan kedalam variabel seperti diatas, data bisa disimpan pula kedalam `object`. **Tipe data object** berisi data yang banyak didalam sebuah variabel. Setiap data yang disimpan memiliki nama masing - masing yang biasa disebut sebagai properti.

```js {34-41} title=index.js
const emailReciver = "rhomairama.dev@gmail.com";

let name = document.getElementById("input-name");
let email = document.getElementById("input-email");
let phone = document.getElementById("input-phone");
let subject = document.getElementById("input-subject");
let message = document.getElementById("input-message");

function submitForm() {
  name = name.value;
  email = email.value;
  phone = phone.value;
  subject = subject.value;
  message = message.value;

  if (name == '') {
    return alert('Name input fields must be not empty');
  } else if (email == '') {
    return alert('Email input fields must be not empty');
  } else if (phone == '') {
    return alert('Phone input fields must be not empty');
  } else if (subject == '') {
    return alert('Subject input fields must be not empty');
  } else if (message == '') {
    return alert('Message input fields must be not empty');
  }

  const a = document.createElement("a");

  a.href = `mailto:${emailReciver}?subject=${subject}&body=Hello my name ${name}, ${subject}, ${message}`;
  a.target = "_blank";
  a.click();

  let dataObject = {
    name: name,
    email: email,
    phoneNumber: phone,
    subject: subject,
    message: message,
  };
  console.log(dataObject);
}
```

Pada fungsi berikut berisikan beberapa penerapan code dasar pada JavaScript seperti:
- **Variable :** Sebuah nama yang mewakili sebuah nilai.
- **Operator :** Simbol yang digunakan untuk melakukan operasi pada suatu nilai dan variabel.
- **Seleksi Kondisi :** Sebuah proses logika dalam menentukan langkah berikutnya berdasarkan kondisi yang telah ditetapkan.
