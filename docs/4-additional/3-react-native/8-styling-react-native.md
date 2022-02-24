---
sidebar_position: 8
---

# 8. Styling in React Native

import useBaseUrl from '@docusaurus/useBaseUrl';

**Inline Styling** adalah salah satu teknik `styling` yang digunakan didalam sebuah tag, pada React Native sendiri dapat mengimplementasikan `inline styling` tetapi dengan penerapan yang sedikit berbeda

Berikut contoh code nya:

```jsx
<View style={{ backgroundColor: "grey", height: "100px" }}>Selamat datang</View>
```

Pada code diatas, terdapat contoh implementasi `inline styling` pada tag `view`, menambahkan attribute style didalamnya terdapat property `backgroundColor` yang memiliki value `grey` dan property `height` memiliki value `100px`, dimana `inline styling` tersebut bertipe `object`.

Berikut code implementasi `inline styling`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/form.js
import { StatusBar } from "expo-status-bar";
import React from "react";
import {
  View,
  Text,
  StyleSheet,
  TouchableOpacity,
  TextInput,
} from "react-native";

export default function Form() {
  return (
    <View style={style.container}>
      <StatusBar />
      {/* Code Here */}
      <Text style={style.header}>Sign In</Text>

      <Text style={style.textStyle}>Email</Text>
      <TextInput style={style.textInput} defaultValue="ex.radif@dumbways.com" />

      <Text style={style.textStyle}>Password</Text>
      <TextInput style={style.textInput} defaultValue="ex.8E0112D!" />

      <TouchableOpacity style={style.button}>
        <Text style={style.textButton}>Sign In</Text>
      </TouchableOpacity>
    </View>
  );
}

// Create Variable for CSS

const style = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
  },
  header: {
    color: "#e74c3c",
    fontSize: 30,
    fontWeight: "bold",
    textAlign: "center",
    marginBottom: 50,
  },
  button: {
    backgroundColor: "#e74c3c",
    height: 45,
    width: "100%",
    borderRadius: 10,
    justifyContent: "center",
  },
  textButton: {
    color: "#FFF",
    fontWeight: "bold",
    fontSize: 16,
    textAlign: "center",
  },
  textStyle: {
    color: "#e74c3c",
    fontSize: 16,
    fontWeight: "bold",
    marginBottom: 5,
  },
  textInput: {
    height: 45,
    borderWidth: 1,
    borderRadius: 5,
    marginBottom: 15,
    padding: 10,
    color: "#95a5a6",
    borderColor: "#7f8c8d",
  },
});
```

Selanjutnya kita import component `form` pada App.js
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
import Form from "./src/screens/form";

export default function App() {
  return (
    <View style={{ marginTop: 100 }}>
      <StatusBar />
      <Form />
    </View>
  );
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@6.style-in-reactnative">
Demo
</a>
</div>