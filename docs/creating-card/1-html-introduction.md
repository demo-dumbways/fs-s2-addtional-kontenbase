---
sidebar_position: 1
---

# 1. HTML Introduction

## 1.1. Apa itu HTML?

**Hypertext Markup Language atau HTML** adalah bahasa markup yang digunakan untuk membuat struktur halaman website. HTML terdiri dari kombinasi teks dan simbol yang disimpan dalam sebuah file.

## 1.2. Tujuan Mempelajari HTML

1. Untuk Membuat sebuah halaman web.
   Bahasa HTML digunakan untuk membuat halaman web. Semua halaman web pasti dibuat menggunakan HTML

2. Sebagai pondasi bagi sebuah web.
   Jika diibaratkan sebuah rumah jika tidak memiliki pondasi maka akan cepat roboh. Begitu juga dengan website. Jika tidak memiliki HTML sebagai pondasi, kita tidak dapat mengimplementasikan bahasa lainnya seperti CSS (bahasa untuk mendesain website), JavaScript (bahasa untuk menambah prilaku website)

## 1.3. Struktur HTML

HTML memiliki 3 bagian utama yakni `deklarasi, head, dan body`. `<!DOCTYPE html>` adalah tag deklarasi untuk menyatakan tipe dokumen dan versinya. Bagian HEAD adalah bagian kepala dari HTML. Dimulai dari tag `<head>` dan ditutup dengan `</head>`.Bagian BODY adalah bagian yang akan ditampilkan pada web browser. Penulisannya di mulai dari tag `<body>` dan ditutup dengan `</body>`.

## 1.4 Tag HTML

Tag merupakan kode yang digunakan untuk memperkenalkan pada web browser untuk apa text HTML yang ditulis. Tag dibutuhkan oleh HTML agar browser mengetahui apakah teks yang dituliskan sebagai list, paragraf, link, dan sebagainya.

### 1.4.1 Struktur Tag

Hampir keseluruhan tag terdiri dari tag pembuka dan tag penutup (container tag), hanya saja ada beberapa tag yang tidak menggunakan tag penutup atau disebut juga sebagai empty tag.

```
<tagname>Content goes here</tagname>
```

atau

```
<tagname>
```

Tag pada bagian Head:

- title
- script
- noscript
- link
- style
- base
- meta

Tag yang sering digunakan pada bagian Body:

- p
- a
- div
- list
- h
- table
- b

### 1.4.2 Attribute pada Tag

**Atribut** merupakan informasi tambahan yang digunakan didalam tag pembuka. Informasi ini bisa berupa instruksi untuk memberikan efek warna, ketebalan, dll. Atribut memiliki 2 bagian yaitu `nama dan nilai (name = “value”)`.
