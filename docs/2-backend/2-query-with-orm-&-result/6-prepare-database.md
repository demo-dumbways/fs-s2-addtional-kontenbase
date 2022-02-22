---
sidebar_position: 6
---

# 6. Prepare Database

import useBaseUrl from '@docusaurus/useBaseUrl';

Sebelum membuat relasi antara tabel, kita perlu melengkapi tabel terlebih dahulu, sesuai dengan Design Database berikut:

<center>
<img alt="image1-2" src={useBaseUrl('img/docs/database-design.png')} width="80%"/>
</center>

Berdasarkan rancangan database diatas, maka kita perlu menyiapkan table - table / model - model berdasarkan rancangan diatas beserta attribute didalamnya menggunakan `sequelize-cli`
- Table profile 

    ```shell
    npx sequelize-cli model:generate --name profile --attributes phone:string,gender:string,address:string,idUser:integer
    ```

- Table product

    ```shell
    npx sequelize-cli model:generate --name product --attributes name:string,desc:text,price:integer,image:string,qty:integer,idUser:integer
    ```

- Table transaction

    ```shell
    npx sequelize-cli model:generate --name transaction --attributes idProduct:integer,idBuyer:integer,idSeller:integer,price:integer
    ```

- Table category

    ```shell
    npx sequelize-cli model:generate --name category --attributes name:string
    ```

- Table productCategory

    ```shell
    npx sequelize-cli model:generate --name productCategory --attributes idProduct:integer,idCategory:integer
    ```

Sebelum melakakukan migrasi model yang telah dibuat, maka kita akan menambahkan relasi pada setiap file model yang akan dimigration. Penambahan relasi disesuaikan dengan rancangan database.

- Relasi Model profile
    
    Pada model profile akan berelasi dengan model users, field yang menjadi penghubung adalah idUser pada model profile dan field id pada model user
    <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/7-orm-sequelize/migrations/20210712032234-create-profile.js">
    Contoh code
    </a>
    <br />
    <br />

    ```js title=migrations/20211221140540-create-profile.js {4-12}
      address: {
        type: Sequelize.TEXT
      },
      idUser: {
        type: Sequelize.INTEGER,
        references: {
          model: "users",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      createdAt: {
        allowNull: false,
        type: Sequelize.DATE
      },
    ```

- Relasi Model product
    
    Pada model product akan berelasi dengan model users, field yang menjadi penghubung adalah idUser pada model product dan field id pada model user

    <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/7-orm-sequelize/migrations/20210712032356-create-product.js">
    Contoh code
    </a>

    <br />
    <br />

    ```js title=migrations/20211221140540-create-product.js {4-12}
      qty: {
        type: Sequelize.INTEGER
      },
      idUser: {
        type: Sequelize.INTEGER,
        references: {
          model: "users",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      createdAt: {
        allowNull: false,
        type: Sequelize.DATE
      },
    ```

- Relasi Model transaction
    
    Pada model transaction akan berelasi dengan model users dan model product. 
    - Field yang menjadi penghubung antara transaction dan user adalah idUser pada model transaction dan field id pada model user. 
    - Field yang menjadi penghubung antara transaction dan product adalah idProduct pada model transaction dan field id pada model product.

    <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/7-orm-sequelize/migrations/20210712033433-create-transaction.js">
    Contoh code
    </a>
    
    <br />
    <br />

    ```js title=migrations/20211221140540-create-transaction.js {7-33}
      id: {
        allowNull: false,
        autoIncrement: true,
        primaryKey: true,
        type: Sequelize.INTEGER
      },
      idProduct: {
        type: Sequelize.INTEGER,
        references: {
          model: "products",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      idBuyer: {
        type: Sequelize.INTEGER,
        references: {
          model: "users",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      idSeller: {
        type: Sequelize.INTEGER,
        references: {
          model: "users",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      price: {
        type: Sequelize.INTEGER
      },
    ```

- Relasi Model categoryProduct
    
    Pada model categoryProduct akan berelasi dengan model product dan model category 
    - Field yang menjadi penghubung antara categoryProduct dan product adalah idProduct pada model categoryProduct dan field id pada model product. 
    - Field yang menjadi penghubung antara categoryProduct dan category adalah idCategory pada model categoryProduct dan field id pada model category.

    <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2-backend/blob/7-orm-sequelize/migrations/20210712034946-create-product-category.js">
    Contoh code
    </a>
    
    <br />
    <br />

    ```js title=migrations/20211221140540-create-categoryproduct.js {7-24}
      id: {
        allowNull: false,
        autoIncrement: true,
        primaryKey: true,
        type: Sequelize.INTEGER
      },
      idProduct: {
        type: Sequelize.INTEGER,
        references: {
          model: "products",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      idCategory: {
        type: Sequelize.INTEGER,
        references: {
          model: "categories",
          key: "id"
        },
        onUpdate: "CASCADE",
        onDelete: "CASCADE"
      },
      createdAt: {
        allowNull: false,
        type: Sequelize.DATE
      },
    ```

Setelah menambahkan relasi pada setiap model, maka selanjutnya kita migrasikan model kedalam database menggunakan command berikut

  ```bash
  npx sequelize db:migrate
  ```