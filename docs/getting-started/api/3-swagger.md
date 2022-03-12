---
sidebar_position: 3
---

# API Documentation (Swagger)

import useBaseUrl from '@docusaurus/useBaseUrl';

Swagger merupakan open source project dan juga salah satu framework API populer yang digunakan untuk merancang, membangun, mendokumentasikan dan mengakses API. Dengan adanya swagger, kita bisa melakukan desain ulang atau membuat baru code API dengan editor yang memberikan log jika terjadi error secara real-time.

<img alt="image1-2" src={useBaseUrl('img/docs/intro-postman-3.png')} width="100%"/>
<br/>
<br/>

Dokumentasi adalah salah satu hal terpenting. Mengapa? Karena dokumentasi menjadi nilai jual kepada client atau manager. Client akan jadi sangat senang dan terbantu dengan adanya dokumentasi, daripada jika diperlihatkan dengan setumpuk baris code. Dengan adanya swagger, kita dapat melakukan request ataupun melihat response dari API. Sehingga menjadikan Swagger sebagai framework komplit untuk project API

## Create Documentation

- Install package swagger-autogen dan swagger-ui-express menggunakan command 
    ```shell
    npm i swagger-autogen
    ```
    ```shell
    npm i swagger-ui-express
    ```
- Import package swagger-autogen pada file swagger.js
    ```js title='swagger.js'
    const swaggerAutogen = require('swagger-autogen')()
    ```
- Tambahka pengaturan untuk membuat file swagger_output.json sebagai hasil dokumentasi nantinya
    ```js title='swagger.js' {3-8}
    const swaggerAutogen = require('swagger-autogen')()

    const outputFile = './swagger_output.json'
    const endpointsFiles = ['./endpoints.js']

    swaggerAutogen(outputFile, endpointsFiles).then(() => {
        require('./index.js')
    })                          
    ```

- Tambahkan script command pada package.json
    ```json {7} title='package.json'
    {
    "name": "exemplo-swagger-autogen",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
        "start": "node index.js",
        "swagger-autogen": "node swagger.js"
    },
    "dependencies": {
        "express": "^4.17.1",
        "swagger-autogen": "^2.18.8",
        "swagger-ui-express": "^4.1.4"
    }
    }
    ```
- Jalan command `npm run swagger-autogen` pada terminal untuk menjalankan pakcage swagger-autogen agar membuat dokumentasi API secara otomatis
    ```shell
    npm run swagger-autogen
    ```
- selesai, dokumentasi API telah dibuat secara otomatis dan untuk melihatnya bisa menggunakan endpoint 
    ```
    http://localhost:3000/doc
    ```