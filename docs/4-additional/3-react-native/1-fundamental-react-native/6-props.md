---
sidebar_position: 6
---

# 6. Props

import useBaseUrl from '@docusaurus/useBaseUrl';

**Props** adalah argumen yang diteruskan antar components. `Props` diteruskan dari `Component` melalui attribute HTML. Yang bisa dikirim dalam props bisa berupa `data`, `variables`, `function` dan bahkan sebuah `class`. Jadi initinya `Props` adalah suatu cara untuk `mengirim` dan `mengakses` data dari component ke component lain secara langsung.

Berikut contoh implementasi `Props`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/components/list.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text } from "react-native";

export default function List(props) {
  return (
    <View>
      <StatusBar />
      <Text>{props.listData}</Text>
    </View>
  );
}
```

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/props.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text, Image } from "react-native";

import List from "../components/list";

export default function Props() {
  // Create variable to insert link Image
  let pic = {
    uri: "https://www.nipponexpress.com/press/report/img/06-Nov-20-ogp.jpeg",
  };

  return (
    <View>
      <StatusBar />
      {/* Code Here */}
      <Text>On the Image element using the default props, namely source</Text>
      <Image source={pic} style={{ width: "100%", height: 200 }} />

      <List listData="BMW" />
      <List listData="Mercedes-Benz" />
      <List listData="Lamborghini" />
    </View>
  );
}
```

Pada implementasi `Props` diatas, kita mengirim kan sebuah data kumpulan nama mobil ke component `List` melalui props yang diberi nama `data`. Perlu diperhatikan, didalam component terdapat Props `default` dan Props `yang dapat dibuat sesuai dengan ke inginan`. Pada tag `img` terdapat props `default` yaitu `alt` dan `src`, sedangkan pada component `List` terdapat props `costume-props` yaitu `data`.

Selanjutnya kita import component `props` pada App.js
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
import Props from "./src/screens/props";

export default function App() {
  return (
    <View style={{ marginTop: 200 }}>
      <StatusBar />
      <Props />
    </View>
  );
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@4.props">
Demo
</a>
</div>
