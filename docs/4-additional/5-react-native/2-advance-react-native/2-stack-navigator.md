---
sidebar_position: 2
---

# 2. Stack Navigator

import useBaseUrl from '@docusaurus/useBaseUrl';

`Stack Navigator` berfungsi untuk berpindah halaman dengan menempatkan screen baru diatas tumpukan screen sebelumnya.

Sebelum implementasi `Stack Navigator`, kita perlu melakukan`instalasi` dengan perintah berikut:

  ```bash
  npm install @react-navigation/stack
  ```

Jika menggunakan expo lakukan perintah instal seperti berikut:
  ```bash
  npm install react-native-gesture-handler
  ```

Selanjutnya kita implementasikan stack navigator seperti code berikut:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title="Container.js" {4,7,10,18,22,25-49}
import * as React from "react";

//Import Navigation Container
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

Selanjutnya buatlah props `navigation` pada screen `Hello` dan buat onPress ketika ditekan akan menampilkan screen IncDec.  
```jsx
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