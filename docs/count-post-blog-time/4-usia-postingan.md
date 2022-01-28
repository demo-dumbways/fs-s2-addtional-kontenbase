---
sidebar_position: 4
---

# 4. Menghitung Waktu/Usia Postingan

Kita sudah mendapatkan waktu konten blog di posting pada function sebelumnya, sekarang untuk melakukan perhitungan usia postingan maka kita perlu mencari selisih waktu sekarang dengan waktu posting.

Sama seperti mengubah format waktu, kita juga akan melakukan proses mencari selisih waktu kedalam sebuah function. Proses pertama diawali dengan mengubah kedalam format hari, karna nantinya kita menginginkan waktu/usia postingan bisa berdasarkan hari, jam, ataupun menit.

```js
function getDistanceTime(time) {
    const distance = new Date() - new Date(time);
  
    const miliseconds = 1000;
    const secondsInMinute = 3600; 
    const hoursInDay = 23;
    const dayDistance = distance / (miliseconds * secondsInMinute * hoursInDay);
  }
```

setelah mendapat selisih waktu berdasarkan hari, selanjutnya kita akan menggunakan percabangan untuk mengubah selisih waktu berdasarkan jam dan menit.

```js {9-21}
function getDistanceTime(time) {
    const distance = new Date() - new Date(time);
  
    const miliseconds = 1000;
    const secondsInMinute = 3600; 
    const hoursInDay = 23;
    const dayDistance = distance / (miliseconds * secondsInMinute * hoursInDay);

    if (dayDistance >= 1) {
        return Math.floor(dayDistance) + ' day ago';
    } else {
        // Convert to hour
        const hourDistance = Math.floor(distance / (1000 * 60 * 60));
        if (hourDistance > 0) {
            return hourDistance + ' hour ago';
        } else {
            // Convert to minute
            const minuteDistance = Math.floor(distance / (1000 * 60));
            return minuteDistance + ' minute ago';
        }
    }
  }
``` 