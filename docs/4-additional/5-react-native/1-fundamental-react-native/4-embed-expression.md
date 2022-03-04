---
sidebar_position: 4
---

# 4. Embedding Expression

import useBaseUrl from '@docusaurus/useBaseUrl';

**Embed Expression** adalah menyisipkan data yang disimpan dalam `variable` atau hasil return dari sebuah `function` kedalam tag, teknik ini biasa juga dikenal dengan nama `Embed Expression`.

Berikut contoh implementasi `Embed Expression` :

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/embedExpression.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text } from "react-native";

export default function EmbedExpression() {
  function getMajor() {
    return "Full-Stack";
  }
  const companyName = "Dumbways.id";

  return (
    <View>
      <StatusBar />
      <Text>
        Welcome To {companyName} Class {getMajor()}
      </Text>
    </View>
  );
}
```

Keterangan code diatas adalah kita membuat sebuah fungsi dan variabel dimana dari fungsi tersebut akan kita gabungkan dengan text, untuk menggabungkan atau memanggil fungsi tersebut kita dapat menggunakan kurung kurawal `{}`.

Selanjutnya kita import component `EmbedExpression` pada App.js
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View } from "react-native";

//Import Screen
import EmbedExpression from "./src/screens/embedExpression";

export default function App() {
  return (
    <View style={{ marginTop: 200 }}>
      <StatusBar />
      {/* Use Component */}
      <EmbedExpression />
    </View>
  );
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@2.embedding-expression">
Demo
</a>
</div>
