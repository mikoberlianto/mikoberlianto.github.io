---
layout: post
title: Scrcpy
subtitle: Mirroring display and control Android devices
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [script,windows]
comments: false
---

# **scrcpy**
Dibaca "screen copy"

Aplikasi ini menyediakan tampilan dan kontrol perangkat Android yang terhubung pada USB (atau melalui TCP/IP). Ini tidak membutuhkan akses root apa pun. Ini bekerja pada GNU/Linux, Windows and macOS.

Ini berfokus pada:
-sangat ringan; (native, hanya menampilkan layar perangkat)
-peforma (30~60fps, tergantung perangkat)
-kualitas (1920×1080 atau lebih)
-latensi rendah (35~70ms)
-waktu startup rendah (~1 detik untuk menampilkan gambar pertama)
-tidak mengganggu (tidak ada sisa aplikasi yang terpasang di perangkat Android)
-manfaat user; tidak ada akun, tidak ada iklan, tidak membutuhkan internet
-kebebasan; gratis dan open source software

fitur yang termasuk:
-perekaman
-mirroring dengan perangkat device layar mati
-copy-paste di kedua arah
-kualitas yang dapat dikonfigurasi
-perangkat Android sebagai webcam (V4L2) (hanya-linux)
-simulasi keyboard fisik (HID)
-simulasi mouse fisik (HID)
-mode OTG
-dan masih banyak lagi


## Persyaratan
Perangkat Android membutuhkan setidaknya API 21 (Android 5.0).

Pastikan Anda mengaktifkan [**debugging adb**](https://developer.android.com/studio/command-line/adb.html#Enabling) pada perangkat Anda.

Di beberapa perangkat, Anda juga perlu mengaktifkan [opsi tambahan](https://github.com/Genymobile/scrcpy/issues/70#issuecomment-373286323) untuk mengontrolnya menggunakan keyboard dan mouse.

## Menjalankan
1. Pasang perangkat Android ke komputermu melalui port USB atau dapat koneksi dalam jaringan WiFi.

2. Enable **adb debugging** di perangkat mu.
### Melalui USB
Di Android 4.2 dan diatasnya, tampilan **Developer options** disembunyikan secara default. Untuk menampilkannya, pergi ke **Settings** > **About phone** dan tap **Build number** sebanyak 7 kali. Kembali ke tampilan sebelumnya untuk menemukan **Developer options** di bawah.

Di beberapa perangkat, tampilan Developer options mungkin berbeda lokasi dan namanya.
```
Catatan: Saat kamu menghubungkan perangkat yang menjalankan Android 4.2.2 atau diatasnya, sistem akan menampilkan dialog menanyakan apakah menerima RSA key yang mengijinkan debugging melalui komputer ini.
```
### Melalui WiFi
-Hubungkan perangkat ke komputer host menggunakan kabel USB.
-Atur perangkat target untuk listen koneksi TCP/IP di port 5555.
```
adb tcpip 5555
```
-Lepaskan hubungan kabel USB dari perangkat target.
-Cari IP address dari perangkat Android. Sebagai contoh, di perangkat Nexus, kamu dapat menemukan IP address di **Settings** > **About tablet** (atau **About phone**) > **Status** > **IP address**. Atau, di perangkat Wear OS, kamu dapat menemukan IP address di **Settings** > **Wi-Fi Settings** > **Advanced** > **IP address**.
-Menghubungkan ke perangkat dengan IP Address tersebut.
```
adb connect device_ip_address:5555
```
konfirmasi komputer host mu sudah terhubung ke perangkat target:
```
$ adb devices
List of devices attached
device_ip_address:5555 device
```




3. Mulai mirroring dengan perintah berikut

```
scrcpy
```
Ini menerima argumen baris perintah, didaftarkan dengan:
```
scrcpy --help
```
==============
```
Microsoft Windows [Version 10.0.22000.708]
(c) Microsoft Corporation. All rights reserved.

C:\Users\YourUserPC>scrcpy --tcpip=192.168.1.2
scrcpy 1.23 <https://github.com/Genymobile/scrcpy>
* daemon not running; starting now at tcp:5037
* daemon started successfully
INFO: Connecting to 192.168.1.2:5555...
cannot connect to 192.168.1.2:5555: No connection could be made because the target machine actively refused it. (10061)
ERROR: Could not connect to 192.168.1.2:5555
ERROR: Server connection failed

C:\Users\YourUserPC>ping 192.168.1.2

Pinging 192.168.1.2 with 32 bytes of data:
Reply from 192.168.1.2: bytes=32 time=16ms TTL=64
Reply from 192.168.1.2: bytes=32 time=14ms TTL=64
Reply from 192.168.1.2: bytes=32 time=5ms TTL=64
Reply from 192.168.1.2: bytes=32 time=5ms TTL=64

Ping statistics for 192.168.1.2:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 5ms, Maximum = 16ms, Average = 10ms

C:\Users\YourUserPC>adb tcpip 5555
restarting in TCP mode port: 5555

C:\Users\YourUserPC>adb connect 192.168.1.2:5555
connected to 192.168.1.2:5555

C:\Users\YourUserPC>scrcpy --tcpip=192.168.1.2
scrcpy 1.23 <https://github.com/Genymobile/scrcpy>
INFO: Connecting to 192.168.1.2:5555...
INFO: Connected to 192.168.1.2:5555
C:\ProgramData\chocolatey\lib\scrcpy\tools\scrcpy-server: 1 file pushed, 0 skipped. 10.2 MB/s (41123 bytes in 0.004s)
[server] INFO: Device: Xiaomi M2012K11AG (Android 12)
INFO: Renderer: direct3d
INFO: Initial texture: 1080x2400
WARN: Killing the server...
```

source:
NOT WORKING ON ANDROID 12 https://github.com/Genymobile/scrcpy/issues/3255


scrcpy --tcpip=192.168.1.47:40329 --bit-rate 10M --max-size 1024 --always-on-top --window-title "POCO F3-MIKO BERLIANTO" --turn-screen-off --power-off-on-close
scrcpy -d --bit-rate 10M --max-size 1024 --always-on-top --window-title "POCO F3-MIKO BERLIANTO"
