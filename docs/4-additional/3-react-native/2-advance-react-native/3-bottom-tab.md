---
sidebar_position: 3
---

# 3. Bottom Tabs Navigator

import useBaseUrl from '@docusaurus/useBaseUrl';

`Bottom Tabs Navigator` berfungsi untuk berpindah screen dengan menempatkan tab menu pada bawah layar aplikasi, ketika menu ditab maka screen akan berpindah.

Sebelum implementasi `Bottom Tabs Navigator`, kita perlu melakukan`instalasi` dengan perintah berikut:

  ```bash
  npm install @react-navigation/bottom-tabs
  ```

Selanjutnya kita implementasikan seperti code berikut:

Sebelumnya import terlebih dulu icon untuk bottom tab
```jsx title="Container.js"
import { Ionicons } from "@expo/vector-icons";
```

Selanjutnya buat variabel Tab untuk membuat bottom tab
```jsx title="Container.js"
const Tab = createBottomTabNavigator();
```

Selanjutnya buatlah function component MyTab seperti berikut:
```jsx title="Container.js"
function MyTab() {
  // Init Theme
  const theme = useTheme();

  return (
    <Tab.Navigator
      initialRouteName="Hello"
      screenOptions={({ route }) => ({
        headerMode: "screen",
        headerTintColor: "white",
        headerStyle: { backgroundColor: theme.colors.primary["300"] },
        tabBarIcon: ({ focused, color, size }) => {
          let iconName;

          if (route.name === "Hello") {
            iconName = focused ? "ios-home" : "ios-home-outline";
          } else if (route.name === "Form") {
            iconName = focused
              ? "ios-information-circle"
              : "ios-information-circle-outline";
          }

          return <Ionicons name={iconName} size={size} color={color} />;
        },
        tabBarActiveTintColor: theme.colors.primary["800"],
        tabBarInactiveTintColor: "gray",
      })}
    >
      <Tab.Screen name="Hello" component={Hello} />
      <Tab.Screen name="Form" component={FormNativeBase} />
    </Tab.Navigator>
  );
}
```

Selanjutnya tambahkan component myTab kedalam component Container
```jsx title="Container.js" {8-11}
export default function Container() {
  const theme = useTheme();

  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen
          name="Main"
          component={MyTab}
          options={{
            headerShown: false,
          }}
        />
        <Stack.Screen
          name="IncDec"
          component={IncDec}
          options={{
            title: "Increment & Decrement",
            headerMode: "screen",
            headerTintColor: "white",
            headerStyle: { backgroundColor: theme.colors.primary["300"] },
          }}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

Contoh full code
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title="Container.js" {4,7,10,13,16,24,27,30-62,71-74}
import * as React from "react";

//Import Navigation Container
import { NavigationContainer } from "@react-navigation/native";

// Import Stack Navigation
import { createStackNavigator } from "@react-navigation/stack";

// Import Bottom Tab Navigation
import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";

//Import Icon
import { Ionicons } from "@expo/vector-icons";

// Import Theme Native Base
import { useTheme } from "native-base";

// Import Screen
import FormNativeBase from "./src/screens/formNativeBase";
import Hello from "./src/screens/hello";
import IncDec from "./src/screens/incDec";

// Create Stack Navigation
const Stack = createStackNavigator();

//Create Bottom Tab Navigation
const Tab = createBottomTabNavigator();

// Create Component Bottom Tab Navigation
function MyTab() {
  // Init Theme
  const theme = useTheme();

  return (
    <Tab.Navigator
      initialRouteName="Hello"
      screenOptions={({ route }) => ({
        headerMode: "screen",
        headerTintColor: "white",
        headerStyle: { backgroundColor: theme.colors.primary["300"] },
        tabBarIcon: ({ focused, color, size }) => {
          let iconName;

          if (route.name === "Hello") {
            iconName = focused ? "ios-home" : "ios-home-outline";
          } else if (route.name === "Form") {
            iconName = focused
              ? "ios-information-circle"
              : "ios-information-circle-outline";
          }

          return <Ionicons name={iconName} size={size} color={color} />;
        },
        tabBarActiveTintColor: theme.colors.primary["800"],
        tabBarInactiveTintColor: "gray",
      })}
    >
      <Tab.Screen name="Hello" component={Hello} />
      <Tab.Screen name="Form" component={FormNativeBase} />
    </Tab.Navigator>
  );
}

export default function Container() {
  const theme = useTheme();

  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen
          name="Main"
          component={MyTab}
          options={{
            headerShown: false,
          }}
        />
        <Stack.Screen
          name="IncDec"
          component={IncDec}
          options={{
            title: "Increment & Decrement",
            headerMode: "screen",
            headerTintColor: "white",
            headerStyle: { backgroundColor: theme.colors.primary["300"] },
          }}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```
<div>
  <a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-advance-react-native@3.bottom-tabs-navigation">
  Demo
  </a>
</div>