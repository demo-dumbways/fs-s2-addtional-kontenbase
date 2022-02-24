---
sidebar_position: 9
---

# 9. List of Map

import useBaseUrl from '@docusaurus/useBaseUrl';

**Map** adalah hight order function pada javascript javascript yang biasa digunakan untuk merubah semua elemen di dalam suatu array menjadi elemen dengan nilai yang baru.

Berikut code implementasi `list of map`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/map.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text } from "react-native";

export default function Map() {
  // Create Dummy Data With Array
  const cars = ["BMW", "Mercedes-Benz", "Bugati", "Lexus"];

  return (
    <View>
      <StatusBar />
      <Text>This is List On React</Text>
      {/* Code Here */}
      {cars.map((car) => (
        <Text key={car}>{car}</Text>
      ))}
    </View>
  );
}
```

Selanjutnya kita import component `map` pada App.js
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
import Map from "./src/screens/map";

export default function App() {
  return (
    <View style={{ marginTop: 100 }}>
      <StatusBar />
      <Map />
    </View>
  );
}

```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@7.list-of-map">
Demo
</a>
</div>