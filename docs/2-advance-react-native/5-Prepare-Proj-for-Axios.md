---
sidebar_position: 5
---

# 5. Prepare Project For Axios

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari terkait fatching atau menampilkan dari api json placeholder dengan menggunakan axios.

Kita implementasikan dengan code berikut:

Sebelumnya install terlebih dahulu axios

```bash
npm i axios
```

Selanjutnya import axios yang sudah install

```jsx title="src/screens/listSoc.js" {6}
import React from 'react';
import { View, Text, Button, StyleSheet, FlatList } from 'react-native';
import { ListItem, Avatar } from 'react-native-elements';

// Import Axios
import axios from 'axios';

const Posts = (props) => {
  return (
    <View style={style.container}>
      <View>
        <Text>This Is Post</Text>

        <Button
          title="To Detail Post"
          onPress={() => props.navigation.navigate('DetailPost')}
        />
      </View>
    </View>
  );
};

export default Posts;

const style = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: 'column',
  },
});
```

Selanjutnya buatlah state untuk menampung fetching data api

```jsx title="src/screens/Posts.js" {9-10}
import React from 'react';
import { View, Text, Button, StyleSheet, FlatList } from 'react-native';
import { ListItem, Avatar } from 'react-native-elements';

import axios from 'axios';

const Posts = (props) => {
  //Init State
  const [post, setPost] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  return (
    <View style={style.container}>
      <View>
        <Text>This Is Post</Text>

        <Button
          title="To Detail Post"
          onPress={() => props.navigation.navigate('DetailPost')}
        />
      </View>
    </View>
  );
};

export default Posts;

const style = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: 'column',
  },
});
```

Selanjutnya buatlah function getPost untuk melakukan fetching data dari json placeholder

```jsx title="src/screens/Posts.js" {13-30}
import React from 'react';
import { View, Text, Button, StyleSheet, FlatList } from 'react-native';
import { ListItem, Avatar } from 'react-native-elements';

import axios from 'axios';

const Posts = (props) => {
  //Init State
  const [post, setPost] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  // Create Didmount
  useEffect(() => {
    getPost();
  }, []);

  // Create Function to fetch
  const getPost = () => {
    setIsLoading(true);
    axios
      .get('https://jsonplaceholder.typicode.com/posts')
      .then((res) => {
        setPost(res.data);
        setIsLoading(false);
      })
      .catch(() => {
        alert('Error Fetch Data');
        setIsLoading(false);
      });
  };

  return (
    <View style={style.container}>
      <View>
        <Text>This Is Post</Text>

        <Button
          title="To Detail Post"
          onPress={() => props.navigation.navigate('DetailPost')}
        />
      </View>
    </View>
  );
};

export default Posts;

const style = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: 'column',
  },
});
```

Selanjutnya looping dan tampilkan hasil dari fetching data dari json placeholder

```jsx title="src/screens/Posts.js" {30-50,56-62}
import React from 'react';
import { View, Text, Button, StyleSheet, FlatList } from 'react-native';
import { ListItem, Avatar } from 'react-native-elements';

import axios from 'axios';

const Posts = (props) => {
  const [post, setPost] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  useEffect(() => {
    getPost();
  }, []);

  const getPost = () => {
    setIsLoading(true);
    axios
      .get('https://jsonplaceholder.typicode.com/posts')
      .then((res) => {
        setPost(res.data);
        setIsLoading(false);
      })
      .catch(() => {
        alert('Error Fetch Data');
        setIsLoading(false);
      });
  };

  //   Create Component List
  const _renderItem = ({ item }) => {
    return (
      <ListItem
        onPress={() => props.navigation.navigate('DetailPost', item)}
        key={item.id.toString()}
        bottomDivider
      >
        <Avatar
          rounded
          title={item.title.slice(0, 2)}
          containerStyle={{ backgroundColor: 'black' }}
        />
        <ListItem.Content>
          <ListItem.Title h4 numberOfLines={1}>
            {item.title}
          </ListItem.Title>
          <ListItem.Subtitle numberOfLines={2}>{item.body}</ListItem.Subtitle>
        </ListItem.Content>
      </ListItem>
    );
  };

  return (
    <View style={style.container}>
      <View>
        {/* Render Component List */}
        <FlatList
          data={post}
          renderItem={_renderItem}
          keyExtractor={(item) => item.id.toString()}
          refreshing={isLoading}
          onRefresh={getPost}
        />
      </View>
    </View>
  );
};

export default Posts;

const style = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: 'column',
  },
});
```

Full Code:

```jsx
import React, { useState, useEffect } from 'react';
import { View, Text, Button, StyleSheet, FlatList } from 'react-native';
import { ListItem, Avatar } from 'react-native-elements';

// Import Axios
import axios from 'axios';

const Posts = (props) => {
  //Init State
  const [post, setPost] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  // Create LifeCycle
  useEffect(() => {
    //Function Exception
    getPost();
  }, []);

  // Create Function to fetch
  const getPost = () => {
    setIsLoading(true);
    axios
      .get('https://jsonplaceholder.typicode.com/posts')
      .then((res) => {
        setPost(res.data);
        setIsLoading(false);
      })
      .catch(() => {
        alert('Error Fetch Data');
        setIsLoading(false);
      });
  };

  //   Create Component List
  const _renderItem = ({ item }) => {
    return (
      <ListItem
        onPress={() => props.navigation.navigate('DetailPost', item)}
        key={item.id.toString()}
        bottomDivider
      >
        <Avatar
          rounded
          title={item.title.slice(0, 2)}
          containerStyle={{ backgroundColor: 'black' }}
        />
        <ListItem.Content>
          <ListItem.Title h4 numberOfLines={1}>
            {item.title}
          </ListItem.Title>
          <ListItem.Subtitle numberOfLines={2}>{item.body}</ListItem.Subtitle>
        </ListItem.Content>
      </ListItem>
    );
  };

  return (
    <View style={style.container}>
      <View>
        {/* Render Component List */}
        <FlatList
          data={post}
          renderItem={_renderItem}
          keyExtractor={(item) => item.id.toString()}
          refreshing={isLoading}
          onRefresh={getPost}
        />
      </View>
    </View>
  );
};
```

<div>
  <a class="btn-demo" href="https://snack.expo.dev/@demo.dumbways/github.com-demo-dumbways-advance-react-native@5.prepare-proj-for-axios">
  Full Code & Demo
  </a>
</div>
