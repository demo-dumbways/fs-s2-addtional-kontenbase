---
sidebar_position: 3
---

# 3. Bottom Tabs Navigator

import useBaseUrl from '@docusaurus/useBaseUrl';

`Bottom Tabs Navigator` berfungsi untuk berpindah screen dengan menempatkan tab menu pada bawah layar aplikasi, ketika kita menyentuh pada tab menu maka screen akan berpindah.

langkah awal sebelum kita mengimplementasi `Bottom Tabs Navigator`, kita perlu melakukan`instalasi` dengan perintah berikut:

```bash
npm install @react-navigation/bottom-tabs
```

Langkah selanjut nya adalah kita akan mencoba menginstall `Expo Icon` agar tampilan pada `Bottom Tabs Navigator` kita dapat di tambahkan sebuah Icon

```bash
npm install expo-vector-icons
```

Selanjut nya kita akan mencoba mengimplementasikan `Bottom Tabs Navigator` pada file `Container.js` yang dimana akan kita coba kombinasikan dengan `Stack Navigator` yang telah kita buat pada di Sesi sebelum nya.

- Langkah Pertama Import `createBottomTabNavigator` dimana fungsi ini adalah agar kita dapat membuat stack navigation pada aplikasi mobile kita.

  ```jsx title="Container.js"{4-5}
  // Import Stack Navigation
  import { createStackNavigator } from '@react-navigation/stack';

  // Import Bottom Tab Navigation
  import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
  ```

- Langkah Berikutnya kita perlu mengImport `Icon` yang nantinya akan kita tambahkan pada `Bottom Tabs Navigator`.

  ```jsx title="Container.js"
  // this code continues from the previous code

  import { Ionicons } from '@expo/vector-icons';
  ```

- Langkah Berikutnya kita perlu mendeklarasikan kembali `createBottomTabNavigator` yang telah di import pada section di atas dimana agar kita dapat menggunakan Buttom navigation.

  ```jsx title="Container.js" {6-7}
  // this code continues from the previous code

  // Create Stack Navigation
  const Stack = createStackNavigator();

  //Create Bottom Tab Navigation
  const Tab = createBottomTabNavigator();
  ```

- Dikarenakan kita ingin menggunakan 2 navigation dalam 1 apps yaitu `Stack` dan `Bottom` maka kita perlu membuat satu buah component yang dimana isi dari component tersebut adalah sebuah navigation yang menjadi main menu dari apps kita, pada aplikasi mobile sendiri biasanya `Bottom Tabs Navigator` biasa gunakan sebagai main menu dari Apps, silakan buat code berikut :

  ```jsx title="Container.js"
  // this code continues from the previous code

  function MyTab() {
    // Init Theme
    const theme = useTheme();

    return (
      <Tab.Navigator
        initialRouteName="Hello"
        screenOptions={({ route }) => ({
          headerMode: 'screen',
          headerTintColor: 'white',
          headerStyle: { backgroundColor: theme.colors.primary['300'] },
          tabBarIcon: ({ focused, color, size }) => {
            let iconName;

            if (route.name === 'Hello') {
              iconName = focused ? 'ios-home' : 'ios-home-outline';
            } else if (route.name === 'Form') {
              iconName = focused
                ? 'ios-information-circle'
                : 'ios-information-circle-outline';
            }

            return <Ionicons name={iconName} size={size} color={color} />;
          },
          tabBarActiveTintColor: theme.colors.primary['800'],
          tabBarInactiveTintColor: 'gray',
        })}
      >
        <Tab.Screen name="Hello" component={Hello} />
        <Tab.Screen name="Form" component={FormNativeBase} />
      </Tab.Navigator>
    );
  }
  ```

- Langkah Berikut nya adalah kita perlu merefactor code pada component `Container.js` Menjadi seperti berikut :

  **Notes :** Disini kita merubah Main Navigation Menjadi Component `MyTabs` yang dimana component tersebut berisikan `Bottom Tabs Navigator`

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
              title: 'Increment & Decrement',
              headerMode: 'screen',
              headerTintColor: 'white',
              headerStyle: { backgroundColor: theme.colors.primary['300'] },
            }}
          />
        </Stack.Navigator>
      </NavigationContainer>
    );
  }
  ```

Full code :

```jsx title="Container.js" {10,13,27,30-62,71-74}
import * as React from 'react';

//Import Navigation Container
import { NavigationContainer } from '@react-navigation/native';

// Import Stack Navigation
import { createStackNavigator } from '@react-navigation/stack';

// Import Bottom Tab Navigation
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

//Import Icon
import { Ionicons } from '@expo/vector-icons';

// Import Theme Native Base
import { useTheme } from 'native-base';

// Import Screen
import FormNativeBase from './src/screens/formNativeBase';
import Hello from './src/screens/hello';
import IncDec from './src/screens/incDec';

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
        headerMode: 'screen',
        headerTintColor: 'white',
        headerStyle: { backgroundColor: theme.colors.primary['300'] },
        tabBarIcon: ({ focused, color, size }) => {
          let iconName;

          if (route.name === 'Hello') {
            iconName = focused ? 'ios-home' : 'ios-home-outline';
          } else if (route.name === 'Form') {
            iconName = focused
              ? 'ios-information-circle'
              : 'ios-information-circle-outline';
          }

          return <Ionicons name={iconName} size={size} color={color} />;
        },
        tabBarActiveTintColor: theme.colors.primary['800'],
        tabBarInactiveTintColor: 'gray',
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
            title: 'Increment & Decrement',
            headerMode: 'screen',
            headerTintColor: 'white',
            headerStyle: { backgroundColor: theme.colors.primary['300'] },
          }}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

<div>
  <a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-advance-react-native@3.bottom-tabs-navigation">
  Full code & Demo
  </a>
</div>
