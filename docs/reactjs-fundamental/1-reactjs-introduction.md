---
sidebar_position: 2
---

# 1. ReactJs Introduction

## 1.1. Apa itu ReactJs?

**React Js** adalah sebuah library JavaScript yang di buat oleh facebook. React bukanlah sebuah framework. React adalah library yang bersifat composable user interface, yang artinya kita dapat membuat berbagai UI yang bisa kita bagi menjadi beberapa komponen.

## 1.2. Kenapa Mempelajari React Js

1. Cepat dan Efisien
Karena berbasis komponen maka react hanya perlu me-render  resource yang berhubungan dengan data yang berganti, tidak perlu me-render seluruh resource .

2. Reusable (dapat digunakan berulangkali)
Komponen yang telah kita buat dapat kita gunakan berkali-kali pada saat dibutuhkan. Ini sangat berguna bagi kita untuk mempersingkat waktu dan mengurangi resource yang ada.

3. Library JavaScript
JSX (JavaScript Extension) singkatnya kita dapat menyematkan syntax HTML kedalam Javascript. Ini sangat membantu kita dalam proses development, apalagi dengan adanya  fungsi dari ES6 (Ecma Script).

4. Immutable State
Kita dapat memanajemen state yang ada dengan menggunakan Redux. Kita dapat mengatasi permasalahan mutable state dengan RamdaJs. Untuk state yang berinteraksi dengan API kita dapat menggunakan Redux-Saga.

## 1.3. Apa itu JSX?

JSX atau bisa kita bilang extended javascript adalah suatu pengembangan javascript dimana kode HTML bisa di ikut sertakan dalam javascript.

Hal pertama yang perlu diperhatikan ketika menggunakan sintaks JSX adalah bahwa React harus dalam ruang lingkupnya berdasarkan cara kompilasi JSX. <br />
Contoh :

`function Hello() {  return <h1>Hallo World!</h1>}`

## 1.4 Menyematkan Ekspresi di JSX

Dalam contoh di bawah ini, kita mendeklarasikan variabel bernama name dan kemudian menggunakannya di dalam JSX dengan cara membungkusnya di dalam tanda kurung kurawal (curly braces):

```
const name = 'Budi';
const element = <h1>Halo, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```