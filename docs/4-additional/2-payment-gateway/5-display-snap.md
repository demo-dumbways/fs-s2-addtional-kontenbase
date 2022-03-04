---
sidebar_position: 5
---

# 5. Displaying Snap Payment

import useBaseUrl from '@docusaurus/useBaseUrl';

Menampilkan snap pada sisi client membutuhkan library `snap.js` yang disediakan oleh midtrans. Maka kita perlu menambahkan dan mengkonfigurasi library snap.js dengan cara mengakses secara langsung pada website midtrans. Selain itu kita juga menyiapkan sebuah variabel yang menampung data `MIDTRANS_CLIENT_KEY`. 

```js title=client/src/pages/DetailProduct.js {3-6}
// continuation code is the same as in the template

useEffect(() => {
  const midtransScriptUrl = "https://app.sandbox.midtrans.com/snap/snap.js";
  const myMidtransClientKey = "Client key here ...";
}, []);

// continuation code is the same as in the template
```

selanjutnya kedua variabel tersebut akan kita jadikan sebuah element beserta atribut - atributnya pada halaman site menggunakan method `createElement`

Referensi : [Link](https://docs.midtrans.com/en/other/faq/technical?id=my-developer-uses-react-js-frontend-framework-and-is-unable-to-use-midtransminjssnapjs-what-should-i-do)

```js title=client/src/pages/DetailProduct.js {5-12}
useEffect(() => {
  const midtransScriptUrl = "https://app.sandbox.midtrans.com/snap/snap.js";
  const myMidtransClientKey = "Client key here ...";

  let scriptTag = document.createElement("script");
  scriptTag.src = midtransScriptUrl;
  scriptTag.setAttribute("data-client-key", myMidtransClientKey);

  document.body.appendChild(scriptTag);
  return () => {
    document.body.removeChild(scriptTag);
  };
}, []);
```

Selanjutnya adalah mengakses API transaction utnuk melakukan proses transkasi pembayaran dan menampung response kedalam sebuah variabel.

```js title=client/src/pages/DetailProduct.js  {3}
// continuation code is the same as in the template

const response = await api.post("/transaction", config);

// continuation code is the same as in the template
```

Setelah mendapatkan response dari `API transaction`, maka kita membutuhkan `token payment` yang dikirimkan response. **Token Payment** dibutuhkan pada proses inisialisasi snap untuk ditampilkan pada halaman site

```js title=client/src/pages/DetailProduct.js  {3-20}
const response = await api.post("/transaction", config);

const token = response.payment.token;

window.snap.pay(token, {
  onSuccess: function (result) {
    console.log(result);
    history.push("/profile");
  },
  onPending: function (result) {
    console.log(result);
    history.push("/profile");
  },
  onError: function (result) {
    console.log(result);
  },
  onClose: function () {
    alert("you closed the popup without finishing the payment");
  },
});
```

Referensi : [Link](https://docs.midtrans.com/en/snap/advanced-feature)