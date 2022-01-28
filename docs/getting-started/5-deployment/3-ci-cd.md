---
sidebar_position: 3
---

import useBaseUrl from '@docusaurus/useBaseUrl';

# 3.CI/CD with Vercel

:::info
Bagian ini boleh diabaikan terlebih dahulu, karena pada beberapa bagian selanjutnya akan diarahkan kembali ke bagian ini
:::

### 3.1 Apa itu CI/CD

_CI (Continuous Integration)_ dan _CD (Continuous Delivery)_ proses otomatisasi untuk memastikan bahwa kode aplikasi baru selalu diuji, aman dan siap untuk digunakan tepat pada waktunya.

### 3.2 Persiapan

Pastikan sudah memiliki Repository dan terdapat 2 branch, dimana branch `main` yang kita gunakan sebagai default branch yang akan dideploy ke Vercel, dan branch `staging` sebagai branch yang menyimpan code sementara sebelum digabung dengan branch `main`. Penamaan selain `default branch` bersifat bebas.

<a class="btn-example-code" href="https://github.com/demo-dumbways/learn-ci-cd-auto-deploy/tree/main">
Contoh Repository
</a>

<br />
<br />

<img alt="image-started-1" src={useBaseUrl('img/docs/image-started-1.png')} height="auto" width="auto"/>

### 3.3 Push ke Github

Karena pada tahapan ini kita akan melakukan CI/CD atau Auto Deploy, pastikan sudah melakukan koneksi dan deploy ke Vercel terlebih dahulu ([Cara Deploy ke Vercel](https://dumbways-ebook.netlify.app/getting-started/deployment/deploy-to-vercel)).

Pada branch `staging`, silakan melakukan perubahan code atau file, kemudian lakukan commit dan push.

<img alt="image-started-2" src={useBaseUrl('img/docs/image-started-2.png')} height="auto" width="auto"/>

### 3.4 Pull Request

Pada repository masuk ke branch `staging`, kemudian lakukan `Pull Request` dengan cara klik `Compare & pull request` atau dengan klik `Contribute` kemudian pilih `Open pull request`.

<img alt="image-started-3" src={useBaseUrl('img/docs/image-started-3.png')} height="auto" width="auto"/>

kemudian klik `Create pull request`

<img alt="image-started-4" src={useBaseUrl('img/docs/image-started-4.png')} height="auto" width="auto"/>

### 3.5 Vercel Preview

Setelah melakukan `Pull Request`, kita dapat melihat link preview yang secara otomatis didapatkan dari Vercel

<img alt="image-started-5" src={useBaseUrl('img/docs/image-started-5.png')} height="auto" width="auto"/>

### 3.6 Linked Issues

Hubungkan `Pull Request` dengan Issues pada repository, dengan klik `Linked issues` dan pilih `Issues` yang diinginkan.

<img alt="image-started-6" src={useBaseUrl('img/docs/image-started-6.png')} height="auto" width="auto"/>

Jika belum memiliki Issues silahkan dibuat terlebih dahulu atau dapat mengikuti cara [disini](https://dumbways-ebook.netlify.app/getting-started/project-management/issue-dan-status-project)

### 3.7 Menggabungkan Pull Request

Silakan klik tombol `Merge pull request` dan klik tombol `Confirm merge` agar code yang baru ditambahkan pada branch `staging` dapat digabungkan dengan code yang ada di branch `main`.

<img alt="image-started-7" src={useBaseUrl('img/docs/image-started-7.png')} height="auto" width="auto"/>

Dan _Issues_ yang terhubung dengan _Pull Request_ tersebut akan ditutup.

<img alt="image-started-8" src={useBaseUrl('img/docs/image-started-8.png')} height="auto" width="auto"/>

### 3.8 Deployments

Setiap commit atau pull request yang dilakukan pada default branch, maka Vercel akan melakukan Auto Deploy atau melakukan proses CI/CD. Sehingga semua hasil Deploy code baik dari awal sampai terakhir dapat kita lihat previewnya.

<img alt="image-started-9" src={useBaseUrl('img/docs/image-started-9.png')} height="auto" width="auto"/>
