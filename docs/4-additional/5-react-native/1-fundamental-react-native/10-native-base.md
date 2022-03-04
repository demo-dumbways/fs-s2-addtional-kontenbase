---
sidebar_position: 10
---

# 10. Native Base

import useBaseUrl from '@docusaurus/useBaseUrl';

**NativeBase** NativeBase adalah komponen user interface untuk React Native  yang dapat digunakan pada platform Android maupun iOS.

Berikut code implementasi `NativeBase`:

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=src/screens/formNativeBase.js
import * as React from "react";
import { MaterialCommunityIcons } from "@expo/vector-icons";
import {
  Box,
  Text,
  Heading,
  VStack,
  FormControl,
  Input,
  Link,
  Button,
  Icon,
  IconButton,
  HStack,
  Divider,
} from "native-base";

export default function FormNativeBase() {
  return (
    <Box
      safeArea
      bg="primary.100"
      flex={1}
      p={10}
      w="100%"
      mx="auto"
      justifyContent="center"
    >
      <Heading size="lg" color="primary.500">
        Welcome
      </Heading>
      <Heading color="muted.400" size="xs">
        Sign in to continue!
      </Heading>

      <VStack space={2} mt={5}>
        <FormControl>
          <FormControl.Label
            _text={{ color: "muted.700", fontSize: "sm", fontWeight: 600 }}
          >
            Email ID
          </FormControl.Label>
          <Input />
        </FormControl>
        <FormControl mb={5}>
          <FormControl.Label
            _text={{ color: "muted.700", fontSize: "sm", fontWeight: 600 }}
          >
            Password
          </FormControl.Label>
          <Input type="password" />
          <Link
            _text={{ fontSize: "xs", fontWeight: "700", color: "cyan.500" }}
            alignSelf="flex-end"
            mt={1}
          >
            Forget Password?
          </Link>
        </FormControl>
        <VStack space={2}>
          <Button colorScheme="cyan" _text={{ color: "white" }}>
            Login
          </Button>

          <HStack justifyContent="center" alignItem="center">
            <IconButton
              variant="unstyled"
              startIcon={
                <Icon
                  as={<MaterialCommunityIcons name="facebook" />}
                  color="muted.700"
                  size="sm"
                />
              }
            />
            <IconButton
              variant="unstyled"
              startIcon={
                <Icon
                  as={<MaterialCommunityIcons name="google" />}
                  color="muted.700"
                  size="sm"
                />
              }
            />
            <IconButton
              variant="unstyled"
              startIcon={
                <Icon
                  as={<MaterialCommunityIcons name="github" />}
                  color="muted.700"
                  size="sm"
                />
              }
            />
          </HStack>
        </VStack>
        <HStack justifyContent="center">
          <Text fontSize="sm" color="muted.700" fontWeight={400}>
            I'm a new user.{" "}
          </Text>
          <Link
            _text={{ color: "cyan.500", bold: true, fontSize: "sm" }}
            href="#"
          >
            Sign Up
          </Link>
        </HStack>
      </VStack>
    </Box>
  );
}
```

Selanjutnya kita import component `Container` pada App.js
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```js title=Container.js
import * as React from "react";
import { Text, Box } from "native-base";

// Import Screen
import FormNativeBase from "./src/screens/formNativeBase";
import Hello from "./src/screens/hello";

export default function Container() {
  return <FormNativeBase />;
}
```

Selanjutnya kita import component `Container` pada App.js
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-results-stage-2/tree/3-frontend-react-js-fundamental/src">
Contoh code
</a>

<br />
<br />

```jsx title=App.js
import * as React from "react";
// Import 'NativeBaseProvider' component
import { NativeBaseProvider, extendTheme } from "native-base";

// Import font with Expo
import AppLoading from "expo-app-loading";
import {
  useFonts,
  BalsamiqSans_400Regular,
  BalsamiqSans_400Regular_Italic,
} from "@expo-google-fonts/balsamiq-sans";

// Import Container
import Container from "./Container";

export default function App() {
  // Load Font with Expo
  let [fontsLoaded] = useFonts({
    BalsamiqSans_400Regular,
    BalsamiqSans_400Regular_Italic,
  });

  // Setup Font
  const fontConfig = {
    BalsamiqSans: {
      400: {
        normal: "BalsamiqSans_400Regular",
        italic: "BalsamiqSans_400Regular_Italic",
      },
    },
  };

  // Setup Custome Theme
  const customeColor = {
    primary: {
      50: "#E3F2F9",
      100: "#C5E4F3",
      200: "#A2D4EC",
      300: "#7AC1E4",
      400: "#47A9DA",
      500: "#0088CC",
      600: "#007AB8",
      700: "#006BA1",
      800: "#005885",
      900: "#003F5E",
    },
    amber: {
      400: "#d97706",
    },
  };

  // Configuration Native Base Custom Theme
  const theme = extendTheme({
    colors: customeColor,
    fontConfig,
    fonts: {
      heading: "BalsamiqSans",
      body: "BalsamiqSans",
      mono: "BalsamiqSans",
    },
    config: { initialColorMode: "dark" },
  });

  if (!fontsLoaded) {
    return <AppLoading />;
  } else {
    return (
      <NativeBaseProvider theme={theme}>
        <Container />
      </NativeBaseProvider>
    );
  }
}
```

<div>
<a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-fundamental-react-native@7.list-of-map">
Demo
</a>
</div>