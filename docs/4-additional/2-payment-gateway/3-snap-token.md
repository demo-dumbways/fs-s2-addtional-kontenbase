---
sidebar_position: 3
---

# 3. Snap Token (Backend)

import useBaseUrl from '@docusaurus/useBaseUrl';

**SNAP** adalah portal pembayaran yang memungkinkan merchant untuk menampilkan halaman pembayaran Midtrans langsung di website. Permintaan API harus dilakukan dari `backend merchant (aplikasi kita)` untuk memperoleh token transaksi Snap dengan memberikan informasi pembayaran dan `Server Key`. Setidaknya ada tiga komponen yang diperlukan untuk mendapatkan token Snap `(server_key, order_id, gross_amount)`