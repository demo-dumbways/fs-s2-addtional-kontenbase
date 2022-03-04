---
sidebar_position: 3
---

# 3. Component

import useBaseUrl from '@docusaurus/useBaseUrl';

**Component** adalah salah satu blok bangunan inti dari `React Native`. Dengan kata lain, setiap aplikasi yang akan Anda kembangkan di `React Native` akan terdiri dari bagian-bagian yang disebut Component.

Dengan Component tugas membangun Tampilan jauh lebih mudah. Anda dapat melihat Tampilan dipecah menjadi beberapa bagian individual yang disebut `Component` dan menggabungkan semuanya dalam `Component` induk yang akan menjadi Tampilan akhir Anda.

## 3.1 Membuat Component

Untuk membuat `Component` pada react native sama dengan kita membuat component pada React js

Selanjutnya kita akan implementasi membuat component header, berikut codenya:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/components/header.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text } from "react-native";

export default function header() {
  return (
    <View>
      <Text>This is Header</Text>
    </View>
  );
}
```

Pada component header diatas terdapat `View` dan `Text`, View berfungsi sama seperti `div` pada html, yang berfungsi untuk membungkus blok code, selanjutnya tag `Text` digunakan untuk membungkus sebuah text, pada `React Native` kita tidak bisa langsung memasukan sebuah text di dalam code jadi kita perlu membungkus dengan tag `Text` jika tidak maka code akan terjadi error.

Selanjutnya kita membuat component content
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/components/content.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text } from "react-native";

export default function content() {
  return (
    <View>
      <Text>This Is Content</Text>
      <Text>
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry. Lorem Ipsum has been the industry's standard dummy text ever
        since the 1500s, when an unknown printer took a galley of type and
        scrambled it to make a type specimen book. It has survived not only five
        centuries, but also the leap into electronic typesetting, remaining
        essentially unchanged. It was popularised in the 1960s with the release
        of Letraset sheets containing Lorem Ipsum passages, and more recently
        with desktop publishing software like Aldus PageMaker including versions
        of Lorem Ipsum.
      </Text>
    </View>
  );
}
```

Selanjutnya import component header dan content pada file App.js

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View } from "react-native";

//Import Component
import Content from "./src/components/content";
import Header from "./src/components/header";

export default function App() {
  return (
    <View style={{ marginTop: 200 }}>
      <StatusBar />
      <Header />
      <Content />
    </View>
  );
}
```

Penjelasan pada code diatas, Menggabungkan component header dan content dalam file `App.js` agar pertama kali saat project di jalankan akan menampilkan component tersebut selain itu kita juga menambahkan `StatusBar` pada file `App.js` dimana fungsi dari `StatusBar` adalah agar seluruh component dapat memiliki tampilan headers `StatusBar` yang selaras dari satu screen maupun comonent yang lain.

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@1.component">
Demo
</a>
</div>
