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
### **Pro**
* **Performa**: Karena generator situs statis membuat halaman web terlebih dahulu alih-alih sesuai permintaan (seperti halnya CMS), halaman web dimuat sedikit lebih cepat di browser pengguna.
* **Customization**: Developers can create any template they want. They are not limited by the fields provided by a CMS, nor by a CMS's built-in templates.
* **Lighter backend**: Static websites are lightweight and do not require as much code to run on the server side, whereas CMS-based websites constantly query the server side for content.

### **Cons**
* **Few or no pre-built templates**: The downside of unlimited customization is that it can take longer to get started. Many static site generators do not come with templates, and developers will have to spend a lot of time building them from scratch at first.
* **No user-friendly interface**: It is harder for non-developer users to publish content using a static site generator. There is no CMS interface, and working with raw unformatted data may be intimidating for users. In addition, developer support is often necessary for making website updates.


## How does JAMstack relate to static site generators?
JAMstack (JAM stands for "JavaScript, APIs, Markup") is a methodology for efficiently creating lightweight, fast-performing web applications. JAMstack applications are static, with APIs used for any backend functionality. Static site generators enable developers to quickly build a JAMstack application frontend.

## How are frontend frameworks used with static site generators?
A frontend framework is a collection of files and folders of prebuilt code to help with the design and formatting of a website. Common frontend frameworks include Bootstrap, React, and Vue.js, though there are many others.

Frontend frameworks are extremely helpful when developers are initially building a website. However, frontend frameworks on their own do not generate HTML webpages, unless a developer uses additional tools. A static site generator can be used along with a framework for a developer to rapidly get a fully designed website or application ready for use. Most static site generators allow developers to use any framework they want.

### What is Markdown?
Markdown is a widely used, simple markup language for formatting text. Many developers today prefer using Markdown to traditional HTML when coding content, and many static site generators support Markdown.

### What are some commonly used static site generators?
Many static site generators are available for use today. Some important ones to know are:

* Jekyll
* Gatsby
* Hugo
* Next.js
* Eleventy

[Cloudflare Pages](https://pages.cloudflare.com/) is hosted on the Cloudflare global network, which is within 100ms of 99% of the Internet-connected world for near-instant content delivery to end users. Cloudflare Pages is built on [Cloudflare Workers serverless functions](https://workers.cloudflare.com/) and enables developers to build lightweight, scalable web applications.

Learn how to deploy a [Jekyll site](https://developers.cloudflare.com/pages/how-to/deploy-a-jekyll-site), a [Gatsby site](https://developers.cloudflare.com/pages/how-to/deploy-a-gatsby-site), a [Hugo site](https://developers.cloudflare.com/pages/how-to/deploy-a-hugo-site), and more with Cloudflare Pages.


>#### Source
>[cloudflare learning static site generator](https://www.cloudflare.com/learning/performance/static-site-generator/), [jamstack generator](https://jamstack.org/generators/)
