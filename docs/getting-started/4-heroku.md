---
sidebar_position: 4
---

# Heroku

import useBaseUrl from '@docusaurus/useBaseUrl';

<center>
<img src="https://www3.assets.heroku.com/assets/logo-purple-08fb38cebb99e3aac5202df018eb337c5be74d5214768c90a8198c97420e4201.svg" style={{backgroundColor: 'white', padding: 10, borderRadius: 10, width: '50%'}} />
</center>

<div style={{marginTop: 50}}>
<b>Heroku</b> adalah sebuah cloud platform yang menjalankan bahasa pemrograman tertentu, Heroku mendukung bahasa pemrograman seperti Ruby, Node.js, Python, Java, PHP, dan lain-lain.
</div>

<div style={{marginTop: 10}}>
Heroku termasuk ke dalam kriteria Platform As A Service (PaaS), sehingga bagi anda yang ingin melakukan deploy aplikasi ke heroku cukup hanya dengan melakukan konfigurasi aplikasi yang ingin di deploy dan menyediakan platform yang memungkinkan pelanggan untuk mengembangkan, menjalankan, dan mengelola aplikasi tanpa kompleksitas membangun dan memelihara infrastruktur yang biasanya terkait dengan pengembangan dan peluncuran aplikasi.
</div>

<br />

Visit: [heroku](https://www.heroku.com)

## Deploy Backend App

- Setup Config pada property `production`
  <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-integration-backend/blob/main/config/config.json">
  Contoh code
  </a>

  <br />
  <br />

  ```json title=config/config.json
  "production": {
      "use_env_variable": "DATABASE_URL",
      "dialect": "postgres",
      "protocol": "postgres",
      "dialectOptions": {
          "ssl": {
          "require": true,
          "rejectUnauthorized": false
          }
      }
  }
  ```

- Buatlah file bernama `Profile` dan tambahkan code dibawah ini

    <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-integration-backend/blob/main/Procfile">
  Contoh code
  </a>

  <br />
  <br />

  ```bash
  Release: node_modules/.bin/sequelize db:migrate:undo:all; node_modules/.bin/sequelize db:migrate; node_modules/.bin/sequelize db:seed:all;

  web: node index.js
  ```

- Pada website [heroku](https://www.heroku.com), silakan buat app dan deploy code backend Anda

- Pada bagian `Resources` pastikan `toggle` pada `Release` telah `active`
    <center>
    <img src={useBaseUrl('img/docs/heroku-1.png')} style={{ width: '70%'}} />
    </center>

- Untuk setup `Environment Variable`, silakan masuk pada menu `Settings` dan klik tombol `Reveal Config Vars` pada bagian `Config Vars`
    <center>
    <img src={useBaseUrl('img/docs/heroku-2.png')} style={{ width: '70%'}} />
    </center>
    <center>
    <img src={useBaseUrl('img/docs/heroku-3.png')} style={{ width: '70%'}} />
    </center>
