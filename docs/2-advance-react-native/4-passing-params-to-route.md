---
sidebar_position: 4
---

# 4. Passing Params to Route

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari bagaimana mempassing sebuah data melalui parameter melalui route, yang dimana berfungsi untuk mengkomunikasikan sebuah data dari satu screen ke screen lain.

Langkah pertama ada kita perlu membuat satu buah screen dimana screen tersebut memiliki sebuah `data dummy` yang berisikan list Platform Video Player, Silakan kalian ketikan code berikut dan berikan nama `listSoc.js`

```jsx title="src/screens/listSoc.js" {6}
import * as React from 'react';
import { Text, Box, FlatList, Pressable } from 'native-base';

export default function Hello({ navigation }) {
  // Set Dummy Data with Array
  const socialMedia = ['Netflix', 'YouTube', 'Instagram'];

  return (
    <Box
      safeArea
      bg="primary.400"
      flex={1}
      alignItems="center"
      justifyContent="center"
      p={10}
    ></Box>
  );
}
```

Langkah berikut nya kita akan membuat sebuah function yang bernama `handlePress` dimana fungsi ini bertugas untuk mengirimkan data ke screen yang nantinya akan kita tuju yaitu `Detail Social`.

```jsx title="src/screens/listSoc.js" {8-10}
import * as React from 'react';
import { Text, Box, FlatList, Pressable } from 'native-base';

export default function Hello({ navigation }) {
  // Set Dummy Data with Array
  const socialMedia = ['Netflix', 'YouTube', 'Instagram'];

  const handlePress = (value) => {
    navigation.navigate('Detail Social', { value });
  };

  return (
    <Box
      safeArea
      bg="primary.400"
      flex={1}
      alignItems="center"
      justifyContent="center"
      p={10}
    ></Box>
  );
}
```

Selanjutnya looping data dummy menggunakan flatlist

```jsx title="src/screens/listSoc.js" {21-37}
import * as React from 'react';
import { Text, Box, FlatList, Pressable } from 'native-base';

export default function Hello({ navigation }) {
  // Set Dummy Data with Array
  const socialMedia = ['Netflix', 'YouTube', 'Instagram'];

  const handlePress = (value) => {
    navigation.navigate('Detail Social', { value });
  };

  return (
    <Box
      safeArea
      bg="primary.400"
      flex={1}
      alignItems="center"
      justifyContent="center"
      p={10}
    >
      <FlatList
        data={socialMedia}
        renderItem={({ item }) => (
          <Pressable onPress={() => handlePress(item)}>
            <Text
              fontFamily="body"
              fontWeight={400}
              fontStyle="italic"
              fontSize={30}
              margin={5}
            >
              {item}
            </Text>
          </Pressable>
        )}
        keyExtractor={(item) => item}
      />
    </Box>
  );
}
```

Full Code:

```jsx title="src/screens/listSoc.js" {7,10-12,24-40}
import * as React from 'react';
import { Text, Box, FlatList, Pressable } from 'native-base';

// Add Props in Hello({navigation})
export default function ListSoc({ navigation }) {
  // Set Dummy Data with Array
  const socialMedia = ['Netflix', 'YouTube', 'Instagram'];

  // Make Function handle press to get value per list
  const handlePress = (value) => {
    navigation.navigate('Detail Social', { value });
  };

  return (
    <Box
      safeArea
      bg="primary.400"
      flex={1}
      alignItems="center"
      justifyContent="center"
      p={10}
    >
      {/* Render Array With Flatlist */}
      <FlatList
        data={socialMedia}
        renderItem={({ item }) => (
          <Pressable onPress={() => handlePress(item)}>
            <Text
              fontFamily="body"
              fontWeight={400}
              fontStyle="italic"
              fontSize={30}
              margin={5}
            >
              {item}
            </Text>
          </Pressable>
        )}
        keyExtractor={(item) => item}
      />
    </Box>
  );
}
```

<div>
  <a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-advance-react-native@4.passing-params-to-route">
  Full Code & Demo
  </a>
</div>
