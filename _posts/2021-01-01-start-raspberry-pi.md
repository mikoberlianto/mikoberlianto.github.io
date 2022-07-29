---
layout: post
title: "Mulai Perjalanan Di Raspberry Pi"
subtitle: "Mulai perjalanan mu bersama raspberry pi dengan mudah"
tags: [documentation,setup,raspberry pi]
---

## **Cerita Dibalik Raspberry Pi**
Raspberry Pi (/paɪ/) adalah seri single-board computers (SBCs) terkecil yang dikembangkan di United Kingdom (Inggris) oleh Raspberry Pi Foundation yang berkerjasama dengan Broadcom. Projek Raspberry Pi sebenarnya digunakan untuk keperluan pembelajaran di sekolah dan negara-negara berkembang.

![raspberry-pi](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/0d6033edf45ad2d4185ed05d6cd9a01e2f803034/en/images/pi-plug-in.gif){: .mx-auto.d-block :}

Sampai dengan saat ini Raspberry Pi Foundation atau yang sekarang disebut Raspberry Pi Trading sudah mengeluarkan berbagai jenis tipe Raspbery Pi yang mendukung untuk berbagai macam projek.

| Jenis          | Tipe      | SOC     | Memory  | Release | Arsitektur |
|----------------|-----------|---------|---------|---------|------------|
| Raspberry Pi   | B         | BCM2835 | 256MB | 2012 | ARMv6Z (32-bit) |
|       -        | A         | BCM2835 | 256MB | 2013 | ARMv6Z (32-bit) |
|       -        | B+        | BCM2835 | 512MB | 2014 | ARMv6Z (32-bit) |
|       -        | A+        | BCM2835 | 512MB | 2014 | ARMv6Z (32-bit) |
| Raspberry Pi 2 | B         | BCM2836/7 | 1 GB | 2015 | ARMv7-A (32-bit) |
| Raspberry Pi Zero | Zero   | BCM2835   | 512MB | 2015 | ARMv6Z (32-bit) |
|         -         | W/WH   | BCM2835   | 512MB | 2017 | ARMv6Z (32-bit) |
|         -         | 2W     | BCM2710A1 | 512MB | 2021 | ARMv8-A (64/32-bit) |
| Raspberry Pi 3 | B  | BCM2837A0/B0 | 1GB | 2016 | ARMv8-A (64/32-bit) |
|        -       | A+ | BCM2837B0 | 512MB  | 2018 | ARMv8 (64-bit) |
|        -       | B+ | BCM2837B0 | 1GB    | 2018 | ARMv8-A (64/32-bit) |
| Raspberry Pi 4 | B   | BCM2711 | 1GB,2GB,4GB,8GB | 2019 | ARMv8-A (64/32-bit) |
|       -        | 400 | BCM2711 | 4GB             | 2020 | ARMv8-A (64/32-bit) |
| Raspberry Pi Pico | N/A | RP2040 | 264 KB | 2021 | Armv6-M |

## **Apa yang dibutuhkan**
**1. Raspberry Pi**
<br>Dari berbagai jenis Raspberry Pi diatas, pilih sesuai kebutuhan dan projek mu. Bila membuat sesuatu yang compact bisa memilih jenis Zero.</br>
**2. Power Supply Adaptor**
<br>Adaptor yang dibutuhkan berdaya 5V dengan tegangan min 2.5 Amps ~ 3.0 Amps.</br>
**3. Micro SD Card**
<br>Berkapasitas minimal 8GB.</br>
**4. Keyboard dan Mouse**
**5. Layar TV atau Komputer**
**6. Kabel HDMI**
<br>Bila VGA/DVI gunakan konverter-ke-HDMI.</br>
**8. Casing**
**9. Headphone / Speaker**
**10. Kabel Ethernet**

## **Persiapan SD Card**

### **Enable SSH on First Boot**
1. Gambar flash ke Kartu Micro SD Anda, keluarkan dan colok-in lagi ke PC.
2. Membuka direktori `boot` dan membuat file `SSH` non-extention.
3. Keluarkan dan pasang Micro SD ke raspberry pi lalu nyalakan perangkat.
4. Pindai Alamat IP Raspberry Pi menggunakan [AngryIpScanner](https://angryip.org/download/#windows) atau [Wireless Network Watcher](https://www.nirsoft.net/utils/wireless_network_watcher.html).
5. Sambungkan menggunakan SSH Client (seperti [Putty](https://www.putty.org/)) atau Anda dapat mengarahkan di Terminal Windows ```ssh pi@<ip_address_raspi>```
6. Selamat, Anda dapat masuk menggunakan kredensial default `user/password` `pi/raspberry`.

PEMBARUAN: Atau, Anda dapat mengaturnya pada versi terbaru Raspberry Pi Imager kemudian menekan `Ctrl+Shift+X` dan mengaktifkan ssh melalui aplikasi sebelum flash.  
###### Sumber: [PiMyLifeup](https://pimylifeup.com/raspberry-pi-enable-ssh-boot/)
  



### **Fixing (some) USB Adapter Problems Using Quirks**
Some of the very common adapters can be made to work by using USB quirks to disable UAS mode on the drive. This lowers performance, but it's still much faster than a SD card and your adapter won't go to waste.

To find out the quirks we need to find the device ID string for your adapter and then add an entry to cmdline.txt telling the kernel to apply them on boot.
#### **Find Your Adapter**
To apply the quirks we first need to get the adapter id. We will use the sudo lsusb command:
``` shell
pi@raspberrypi:~ $ sudo dmesg -C
pi@raspberrypi:~ $ sudo dmesg | grep usb
pi@raspberrypi:~ $ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pi@raspberrypi:~ $ 
pi@raspberrypi:~ $ 
pi@raspberrypi:~ $ lsusb
Bus 002 Device 003: ID 174c:0825 ASMedia Technology Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
On line 1 second exect command *lsusb* we can see my ASMedia Technology Inc. adapter (it's the known working Geekworm X825 SATA to USB adapter Raspberry Pi*). You will see something very similar to mine when you run the command and it shouldn't be too hard to figure out which device it is. If you need more information add a *-v* switch to make the command *sudo lsusb -v*. This can sometimes add some additional details to make it easier to figure out which one is your adapter.
If you're still not sure, we have another command that between the two that can narrow things down. Type / paste the following:
``` shell
pi@raspberrypi:~ $ sudo dmesg | grep usb
[138842.160139] usb 2-2: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd
[138842.191348] usb 2-2: New USB device found, idVendor=174c, idProduct=0825, bcdDevice= 0.20
[138842.191368] usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[138842.191389] usb 2-2: Product: X825
[138842.191403] usb 2-2: Manufacturer: SupTronics
[138842.191416] usb 2-2: SerialNumber: 20210300006B
pi@raspberrypi:~ $ 
```
This is the *dmesg* log showing the hardware detection as hardware is activated on the Pi. If your log is really long you can generate fresh entries by just unplugging a device and plugging it back in and running the command again. Here we can clearly see that the X825 is what our Geekworm adapter is being detected as.

Now we can go back to our first lsusb command and we want the 8 characters from the ID field that comes right after the Device:
``` shell
Bus 002 Device 003: ID 174c:0825 ASMedia Technology Inc.
```
#### **Applying Quirks**
To apply the quirks to our USB adapter we are going to edit */boot/cmdline.txt*. Type:
`sudo nano /boot/cmdline.txt`
We are going to add the following entry into the very front of cmdline.txt:
`usb-storage.quirks=XXXX:XXXX:u`
In place of the X's above you will put in your adapter?s ID that we got before. With the example commands I gave above mine would look like this: *usb-storage.quirks=174c:0825:u*. After this my *cmdline.txt* looks like this (everything should be one continuous line, no line breaks!):
`usb-storage.quirks=174c:0825:u console=serial0,115200 console=tty1 root=PARTUUID=d34db33f-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait`
Now reboot the Pi. If the Pi fails to boot you can plug the SD card into the computer and go to */boot/cmdline.txt* and undo the change we did so you can boot back in with your SD card.

#### **Verifying Quirks**
Once you have rebooted after changing *cmdline.txt* we can verify the quirks have been applied by doing another `dmesg | grep usb` command:
```shell
sudo dmesg | grep usb
 [    1.332924] usb 2-1: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
 [    1.332957] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
 [    1.332983] usb 2-1: Product: ASM105x
 [    1.333006] usb 2-1: Manufacturer: ASMT
 [    1.333028] usb 2-1: SerialNumber: 123456789B79F
 [    1.335967] usb 2-1: UAS is blacklisted for this device, using usb-storage instead
 [    1.336071] usb 2-1: UAS is blacklisted for this device, using usb-storage instead
 [    1.336103] usb-storage 2-1:1.0: USB Mass Storage device detected
 [    1.336479] usb-storage 2-1:1.0: Quirks match for vid 174c pid 55aa: c00000
 [    1.336611] scsi host0: usb-storage 2-1:1.0
 ```

This time we can see in dmesg that UAS was blacklisted for the device and it has loaded with the usb-storage driver instead. This driver tends to be more compatible with the 'problematic adapters' but the performance is usually significantly lower. It's definitely worth a try though as some adapters do better with the quirks performance-wise. The only way to know for sure is to run a benchmark.
###### Source: [jamesachambers](https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/)
