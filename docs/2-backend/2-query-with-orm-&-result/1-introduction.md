---
sidebar_position: 1
---

# 1. Introduction

import useBaseUrl from '@docusaurus/useBaseUrl';

## 1.1 ORM

<center>
<img alt="image1-2" src="https://miro.medium.com/max/1400/0*X4u4FSka7FxSct-_.png" style={{ borderRadius: 5, padding: 10, backgroundColor: 'white'}} width="100%"/>
</center>

<br></br>

**ORM (Object Relation Mapping)** merupakan teknik yang merubah suatu table menjadi sebuah object yang nantinya mudah untuk digunakan. Object yang dibuat memiliki property yang sama dengan field — field yang ada pada table tersebut.

### 1.1.1 Kelebihan Menggunakan ORM

- Terdapat fitur penunjang yang dapat memudahkan kita dalam tahap developing seperti connection pooling, migrations, seeds dan lain sebagainya.
- Perintah query memiliki kinerja yang lebih baik.
- Distribusi Model yang lebih terstruktur sehingga memudahkan kita untuk melakukan update, maintain dan reusble code.
- Mempermudah akses dat di karenakan sistem pengaksesan data di lakukan secara abstrak.
- Memungkinkan kita mengoptimalkan konsep OOP.

### 1.1.2 Kekurangan Menggunakan ORM

- Sulit untuk di kembangkan.
- Tidak cocok di gunakan dalam project berskala besar.
- Sulit jika menghandle query-query yang sifat nya kompleks.
- Konfigurasi yang cukup sulit.

## 1.2 Sequelize

<center>
<img alt="image1-2" src="https://www.vectorlogo.zone/logos/sequelizejs/sequelizejs-ar21.svg" style={{ borderRadius: 5, padding: 10, backgroundColor: 'white'}} width="100%"/>
</center>

**Sequelize** adalah salah satu ORM Node.js yang berbasis promise. sequelize dapat digunakan dengan PostgreSQL, MySQL, MariaDB, SQLite, dan MSSQL. Dengan kata lain kita tidak perlu menuliskan sebuah query.
