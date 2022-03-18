---
sidebar_position: 2
---

# 2. Stack Navigator

import useBaseUrl from '@docusaurus/useBaseUrl';

`Stack Navigator` berfungsi untuk berpindah screen dengan menempatkan screen baru diatas tumpukan screen sebelumnya.

Sebelum implementasi `Stack Navigator`, kita perlu melakukan`instalasi` dengan perintah berikut:

```bash
npm install @react-navigation/stack
```

Langkah berikut nya adalah kita perlu menginstall `react-native-gesture-handler` dimana fungsi dari library ini adalah berujuan untuk menggantikan sistem sentuh bawaan pada React Native yang di kita kenal sistem Responde Gesture, Untuk mengintall `react-native-gesture-handler` dapat menggunakan peintah berikut:

```bash
npm install react-native-gesture-handler
```

Langkah berikut nya adalah kita perlu mengimportkan/memasuka library `react-native-gesture-handler` pada file `App.js`, **Notes :** untuk mendeklarasikan `react-native-gesture-handler` silakan sisipkan pada line pertama / baris paling awal

```jsx title="App.js"
//Import React Native Gesture Handler
import "react-native-gesture-handler";
```

Selanjutnya kita implementasikan stack navigator pada file `Container.js` seperti code berikut:

- Import `Navigation Container` dimana navigator container berfungsi untuk mengelola status aplikasi Anda dan menautkan navigator tingkat atas Anda ke lingkungan aplikasi.

  ```jsx title="Container.js"
  import * as React from "react";

  // Import Navigation Container : The NavigationContainer is responsible for managing your app state and linking your top-level navigator to the app environment.
  import { NavigationContainer } from "@react-navigation/native";
  ```

- Import `createStackNavigator` dimana fungsi ini adalah agar kita dapat membuat stack navigation pada aplikasi mobile kita.

  ```jsx title="Container.js"
  // this code continues from the previous code

  // Import Stack Navigation
  import { createStackNavigator } from "@react-navigation/stack";
  ```

- Import `thema dan screen` yang ingin kita navigasikan.

  ```jsx title="Container.js"
  // this code continues from the previous code

  // Import Theme Native Base
  import { useTheme } from "native-base";

  // Import Screen
  import FormNativeBase from "./src/screens/formNativeBase";
  import Hello from "./src/screens/hello";
  import IncDec from "./src/screens/incDec";
  ```

- Deklarasikan kembali `createStackNavigator` yang telah di import pada section di atas dimana agar kita dapat menggunakan stack navigation.

  ```jsx title="Container.js"
  // this code continues from the previous code

  // Create Stack Navigation
  const Stack = createStackNavigator();
  ```

- Tahap terakhir kita akan membuat screen yang sudah kita daftarkan agar dapat bernaviasi satu sama lain dengan stack navigation.

  ```jsx title="Container.js"
  // this code continues from the previous code

  export default function Container() {
    // Init Theme
    const theme = useTheme();

    return (
      <NavigationContainer>
        <Stack.Navigator
          initialRouteName="Home"
          screenOptions={{
            headerMode: "screen",
            headerTintColor: "white",
            headerStyle: { backgroundColor: theme.colors.primary["300"] },
          }}
        >
          <Stack.Screen
            name="Home"
            component={Hello}
            options={{
              title: "Hello Screen",
            }}
          />
          <Stack.Screen
            name="IncDec"
            component={IncDec}
            options={{
              title: "Increment Decrement",
            }}
          />
        </Stack.Navigator>
      </NavigationContainer>
    );
  }
  ```

Full Code:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title="Container.js" {4,7,13-15,18,25-49}
import * as React from "react";

// Import Navigation Container : The NavigationContainer is responsible for managing your app state and linking your top-level navigator to the app environment.
import { NavigationContainer } from "@react-navigation/native";

// Import Stack Navigation
import { createStackNavigator } from "@react-navigation/stack";

// Import Theme Native Base
import { useTheme } from "native-base";

// Import Screen
import FormNativeBase from "./src/screens/formNativeBase";
import Hello from "./src/screens/hello";
import IncDec from "./src/screens/incDec";

// Create Stack Navigation
const Stack = createStackNavigator();

export default function Container() {
  // Init Theme
  const theme = useTheme();

  return (
    <NavigationContainer>
      <Stack.Navigator
        initialRouteName="Home"
        screenOptions={{
          headerMode: "screen",
          headerTintColor: "white",
          headerStyle: { backgroundColor: theme.colors.primary["300"] },
        }}
      >
        <Stack.Screen
          name="Home"
          component={Hello}
          options={{
            title: "Hello Screen",
          }}
        />
        <Stack.Screen
          name="IncDec"
          component={IncDec}
          options={{
            title: "Increment Decrement",
          }}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

Selanjutnya buatlah props `navigation` pada screen `Hello` lalu buat sebuah component `Pressable` yang di dalam nya memiliki sebuah props `onPress` yang berisikan fungsi untuk bernavigasi padas creen `IncDec`.

```jsx {5,19}
import * as React from "react";
import { Text, Box, Pressable } from "native-base";

// Add Props in Hello({navigation})
export default function Hello({ navigation }) {
  return (
    <Box
      bg="primary.400"
      flex={1}
      alignItems="center"
      justifyContent="center"
      p={10}
    >
      <Text fontFamily="body" fontWeight={400} fontStyle="italic" fontSize={30}>
        Life's too short
      </Text>

      <Pressable
        onPress={() => navigation.navigate("IncDec")}
        style={{
          backgroundColor: "#487eb0",
          height: 40,
          width: "100%",
          alignItems: "center",
          justifyContent: "center",
          borderRadius: 10,
          margin: 20,
        }}
      >
        <Text color={{ color: "white" }}>Screen Increment and Decrement</Text>
      </Pressable>
    </Box>
  );
}
```

<div>
  <a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-advance-react-native@2.stack-navigation">
  Demo
  </a>
</div>
