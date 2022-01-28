---
sidebar_position: 4
---

# 4. Embed Expression

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari tentang Embed Expression yaitu kita akan menggabungkan data dari tag `html` dengan data `variable` dan `function`, sebelum kita gabungkan datanya, buat terlebih dahulu code seperti berikut:

```
import React from "react";

function EmbedExpression() {
  return (
    <div>
      <p>Welcome To Class</p>
    </div>
  );
}

export default EmbedExpression;
```

Selanjutnya kita buat variable `companyName` yang datanya adalah `Dumbways.id` dan kita gabungkan data variable yang dibuat sebelumnya dengan tag `p`, sematkan data variable `companyName` setelah text `Welcome To`, untuk contohnya seperti berikut:

```
import React from "react";

function EmbedExpression() {
  const companyName = "Dumbways.id";

  return (
    <div>
      <p>Welcome To {companyName} Class </p>
    </div>
  );
}

export default EmbedExpression;

```

Selanjutnya kita akan menyamatkan data dari function, buat function dengan name `getMajor` yang mereturn data `Full-Stack`, kemudian sematkan dalam tag `p` setelah kata `Class`, ketikan perintah pemanggilan data functionnya menggunakan `{}` diisi dengan nama function yang sudah dibuat sebelumnya `{getMajor()}`, untuk contohnya seperti berikut:

```
import React from "react";

function EmbedExpression() {
  function getMajor() {
    return " Full-Stack";
  }

  const companyName = "Dumbways.id";

  return (
    <div>
      <p>Welcome To {companyName} Class {getMajor()} </p>
    </div>
  );
}

export default EmbedExpression;


```

contoh tampilannya seperti berikut:

<img alt="image" src={useBaseUrl('img/docs/embed-expression.png')} height="80px"/>


Kita sudah berhasil untuk menyematkan data dari variable dan function digabungkan dengan text yang ada dalam tag `p`.
