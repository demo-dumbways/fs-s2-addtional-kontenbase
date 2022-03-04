---
sidebar_position: 5
---

# 5. Event

import useBaseUrl from '@docusaurus/useBaseUrl';

**Event** adalah peristiwa dari hasil interaksi pengguna terhadap Aplikasi. Sebagai contoh, kita menggunakan tag `TouchableOpacity` yang memiliki event `onPress`, artinya jika tag `TouchableOpacity` ditekan oleh pengguna, maka event `onPress` akan terpicu. Kemudian kita harus membuat `Event Handling`, agar tag `TouchableOpacity` tersebut dapat berjalan sesuai dengan fungsinya.

Berikut contoh implementasi `Event`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/event.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import { View, Text, TouchableOpacity } from "react-native";

export default function Event() {
  // Create Function Here
  function Greeting() {
    return alert("Good Morning Everyone Have a Nice Day");
  }

  return (
    <View>
      <StatusBar />
      {/* Code Here */}
      <Text>If you press Click Here then an alert will appear</Text>
      <TouchableOpacity
        onPress={() => alert("Hello Full-Stack Bootcamp Participants")}
      >
        <Text>Click Here</Text>
      </TouchableOpacity>

      <Text>If you press Click Here then an alert will appear</Text>
      <TouchableOpacity onPress={Greeting}>
        <Text>Greeting</Text>
      </TouchableOpacity>
    </View>
  );
}
```

Keterangan code diatas adalah jika kita membuat sebuah `button` dengan menggunakan tag `TouchableOpacity` yang dimana jika tag tersebut terpicu akan menjalankan sebuah fungsi yang telah dibuat.

Selanjutnya kita import component `event` pada App.js
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
import Event from "./src/screens/event";

export default function App() {
  return (
    <View style={{ marginTop: 200 }}>
      <StatusBar />
      <Event />
    </View>
  );
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@3.event">
Demo
</a>
</div>
