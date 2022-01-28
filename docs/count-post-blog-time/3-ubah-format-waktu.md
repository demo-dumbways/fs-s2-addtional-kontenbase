---
sidebar_position: 3
---

# 3. Mengubah Format Waktu

Ketika kita menggunakan tipe data non primitive `Date()` maka format waktu yang digunakan secara default akan berbeda dengan format waktu yang gunakan di Indonesia. Kita akan memformatnya menjadi format tanggal-nama bulan-tahun jam-menit.

Hal pertama yang kita butuhkan adalah sebuah variabel yang menampung nama - nama bulan dalam bahasa indonesia.

```js
const month = [
  'Januari',
  'Februari',
  'Maret',
  'April',
  'Mei',
  'Juni',
  'Juli',
  'Agustus',
  'September',
  'Oktober',
  'November',
  'Desember',
];
```

setelah itu, kita akan membuat sebuah function yang akan melakukan proses mengubah format default `Date()` menjadi format yang kita inginkan. Tujuan kita membuat proses pengubahan format didalam sebuah function yakni supaya cukup melakukan satu kali penulisan code, yaang nantinya bisa digunakan berulang kita function ini dipanggil

```js
function getFullTime(time) {
  const date = time.getDate();
  const monthIndex = time.getMonth();
  const year = time.getFullYear();

  const hours = time.getHours();
  const minutes = time.getMinutes();

  return `${date} ${month[monthIndex]} ${year} ${hours}:${minutes} WIB`;
}
```