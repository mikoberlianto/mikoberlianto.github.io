---
layout: post
title: Static Site Generator, Apa itu?
description: Pengenalan dan contoh dari static site generator
---

Generator situs statis atau Static Site Generator (SSG) adalah alat yang menghasilkan situs web HTML statis penuh berdasarkan data mentah dan satu set templat. Pada dasarnya, generator situs statis mengotomatiskan tugas pengkodean halaman HTML individual dan menyiapkan halaman tersebut untuk disajikan kepada pengguna sebelumnya. Karena halaman HTML ini sudah dibuat sebelumnya, mereka dapat memuat dengan sangat cepat di browser pengguna.

Generator situs statis adalah alternatif untuk sistem manajemen konten (CMS) — jenis alat lain untuk mengelola konten web, membuat halaman web, dan menerapkan templat. (Templat adalah format yang dapat digunakan kembali untuk konten web; pengembang menggunakan templat untuk menghindari penulisan pemformatan yang sama berulang kali.) Generator situs statis biasanya merupakan bagian dari pendekatan pengembangan web [JAMstack](https://www.cloudflare.com/learning/performance/what-is-jamstack/).

## Apa itu situs web statis?
Situs web statis terdiri dari satu atau lebih halaman web HTML yang memuat dengan cara yang sama setiap saat. Situs web statis kontras dengan situs web dinamis, yang memuat secara berbeda berdasarkan sejumlah input data yang berubah, seperti lokasi pengguna, waktu, atau tindakan pengguna. Sementara halaman web statis adalah file HTML sederhana yang dapat dimuat dengan cepat, halaman web dinamis memerlukan eksekusi kode JavaScript di dalam browser untuk merender.

## Apa perbedaan antara generator situs statis dan CMS?
Pada hari-hari awal Internet, situs web disimpan sebagai situs HTML statis, dengan semua halaman web ditata dan dikodekan sebelumnya. Ini tidak efisien karena mengharuskan pengembang untuk mengkodekan setiap halaman web secara manual.

Sistem manajemen konten (CMS) muncul sebagai cara bagi pengembang untuk menghindari semua pengaturan manual itu. Alih-alih mengkodekan halaman sebelumnya, konten disimpan dalam database CMS, dan ketika pengguna meminta halaman, server melakukan hal berikut:

1. Mengkueri database untuk konten yang tepat
2. Mengidentifikasi template yang akan ditampung konten
3. Menghasilkan halaman
4. Menyajikan halaman kepada pengguna

Konten dalam CMS harus sesuai dengan salah satu bidang yang ditawarkan oleh database CMS, tetapi selama itu terjadi, itu akan muncul di tempat yang tepat di situs web setiap saat.

Generator situs statis adalah kompromi antara kedua pendekatan ini. Seperti CMS, ini memungkinkan pengembang untuk menggunakan template dan secara otomatis menghasilkan halaman web — tetapi ia melakukan yang terakhir sebelumnya, alih-alih sebagai tanggapan atas permintaan pengguna. Ini membuat [kinerja situs web](https://www.cloudflare.com/learning/performance/why-site-speed-matters/) lebih cepat, karena halaman web langsung siap untuk dikirim ke pengguna akhir. Ini juga menawarkan penyesuaian yang lebih besar untuk pengembang, karena mereka tidak dibatasi oleh bidang database yang ditawarkan oleh CMS.

## Apa pro dan kontra menggunakan generator situs statis?
### **Pros**
* **Performa**: Karena generator situs statis membuat halaman web terlebih dahulu alih-alih sesuai permintaan (seperti halnya CMS), halaman web dimuat sedikit lebih cepat di browser pengguna.
* **Kustomisasi**: DePengembang dapat membuat template apa pun yang mereka inginkan. Mereka tidak dibatasi oleh bidang yang disediakan oleh CMS, atau oleh template bawaan CMS.
* **Backend yang lebih ringan**: Situs web statis ringan dan tidak memerlukan banyak kode untuk dijalankan di sisi server, sedangkan situs web berbasis CMS terus-menerus meminta konten di sisi server.

### **Cons**
* **Sedikit atau tidak ada templat yang dibuat sebelumnya**: Kelemahan dari penyesuaian tanpa batas adalah perlu waktu lebih lama untuk memulai. Banyak generator situs statis tidak datang dengan template, dan pengembang harus menghabiskan banyak waktu membangunnya dari awal pada awalnya.
* **Tidak ada antarmuka-ramah pengguna**: Lebih sulit bagi pengguna non-pengembang untuk mempublikasikan konten menggunakan generator situs statis. Tidak ada antarmuka CMS, dan bekerja dengan data mentah yang tidak diformat mungkin mengintimidasi pengguna. Selain itu, dukungan pengembang seringkali diperlukan untuk melakukan pembaruan situs web.


## Bagaimana JAMstack berhubungan dengan generator situs statis?
JAMstack (JAM adalah singkatan dari "JavaScript, API, Markup") adalah metodologi untuk secara efisien membuat aplikasi web yang ringan dan berkinerja cepat. Aplikasi JAMstack bersifat statis, dengan API yang digunakan untuk fungsionalitas backend apa pun. Generator situs statis memungkinkan pengembang untuk dengan cepat membangun frontend aplikasi JAMstack.

## Bagaimana kerangka kerja frontend digunakan dengan generator situs statis?
Kerangka kerja frontend adalah kumpulan file dan folder kode bawaan untuk membantu desain dan pemformatan situs web. Kerangka kerja frontend umum termasuk Bootstrap, React, dan Vue.js, meskipun ada banyak lainnya.

Kerangka kerja frontend sangat membantu ketika pengembang awalnya membangun situs web. Namun, kerangka kerja frontend sendiri tidak menghasilkan halaman web HTML, kecuali pengembang menggunakan alat tambahan. Generator situs statis dapat digunakan bersama dengan kerangka kerja bagi pengembang untuk dengan cepat mendapatkan situs web atau aplikasi yang dirancang sepenuhnya siap digunakan. Sebagian besar generator situs statis memungkinkan pengembang untuk menggunakan kerangka kerja apa pun yang mereka inginkan.

### Apa itu Markdown?
Markdown adalah bahasa markup sederhana yang banyak digunakan untuk memformat teks. Banyak pengembang saat ini lebih suka menggunakan Markdown daripada HTML tradisional saat mengkodekan konten, dan banyak generator situs statis mendukung Markdown.

### Apa saja generator situs statis yang umum digunakan?
Banyak generator situs statis tersedia untuk digunakan saat ini. Beberapa yang penting untuk diketahui adalah:

* Jekyll
* Gatsby
* Hugo
* Next.js
* Eleventy

[Cloudflare Pages](https://pages.cloudflare.com/) dihosting di jaringan global Cloudflare, yang berada dalam jarak 100ms dari 99% dunia yang terhubung ke Internet untuk pengiriman konten yang hampir instan ke pengguna akhir. Cloudflare Pages dibangun di atas [Cloudflare Workers fungsi tanpa server](https://workers.cloudflare.com/) dan memungkinkan pengembang untuk membangun aplikasi web yang ringan dan dapat diskalakan.

Pelajari cara deploy [Jekyll site](https://developers.cloudflare.com/pages/how-to/deploy-a-jekyll-site), [Gatsby site](https://developers.cloudflare.com/pages/how-to/deploy-a-gatsby-site), [Hugo site](https://developers.cloudflare.com/pages/how-to/deploy-a-hugo-site), dan lainnya dengan Halaman Cloudflare.


>#### Source
>[cloudflare learning static site generator](https://www.cloudflare.com/learning/performance/static-site-generator/), [jamstack generator](https://jamstack.org/generators/)
