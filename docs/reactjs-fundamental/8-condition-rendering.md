---
sidebar_position: 8
---

# 8. Conditional Rendering

import useBaseUrl from '@docusaurus/useBaseUrl';

Selanjutnya kita akan mempelajari terkait Conditional Rendering,
Didalam react js kita dapat menetukan sebuah componet atau tag html dirender atau tidak pada kondisi tertentu, itu yang disebut Conditional Rendering. Dalam penggunaan Conditional Rendering terdapat dua cara paling umum yang sering digunakan yaitu ternary operator.

untuk code seperti berikut

```
import React, { useState } from "react";

//Create Component PrivatePage
function PrivatePage(props) {
  return (
    <div>
      <h1>Welcome</h1>
      {/* Parsing using Props */}
      <button onClick={props.logout}>Logout</button>
    </div>
  );
}

//Create Component GuestPage
function GuestPage(props) {
  return (
    <div>
      <h1>Please Sign</h1>
      {/* Parsing using Props */}
      <button onClick={props.login}>Login</button>
    </div>
  );
}

function ConditionRendering() {
  //init State
  const [isLoggedin, setIsLoggedin] = useState(false);
  return (
    <div>
      {/* conditional logic rendering */}
      {isLoggedin ? (
        <PrivatePage logout={() => setIsLoggedin(!isLoggedin)} />
      ) : (
        <GuestPage login={() => setIsLoggedin(!isLoggedin)} />
      )}
    </div>
  );
}

export default ConditionRendering;
```

Pada code diatas, kita membuat state `isLoggedin` yang datanya bernilai `false`, dan kita membuat conditional rendering yang dimana ketika data `isLoggedin` bernilai `true`  akan menampilkan `PrivatePage` dan jika false akan menampilkan `GuestPage`, dan ketika button diklik akan menampilkan yang sebaliknya, yang tadinya true menjadi false, dan yang false menjadi true.