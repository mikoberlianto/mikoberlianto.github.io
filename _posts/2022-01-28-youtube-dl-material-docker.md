---
layout: post
title: "Youtube-DL Material Docker di Raspberry Pi"
subtitle: "Menjalankan Youtube-DL Docker di Perangkat Raspberry Pi"
tags: [script,linux,docker]
---

# Youtube-DL Material
Menjalankan Yotube-DL di Docker Raspberry Pi dengan design Material khas Google.

Coding menggunakan [Angular 11](https://angular.io/) untuk frontend, dan [Node.js](https://nodejs.org/) sebagai backend.

## Build di Raspberry Pi Docker
Klik Stacks-Add Stack
```
version: "2"
services:
###########YTDL_MATERIAL#########
    ytdl_material:
        image: tzahi12345/youtubedl-material:nightly
        container_name: ytdl_material
        restart: always
        volumes:
            - /mnt/extssd/Portainer/Files/AppData/Config/YTDLM:/app/appdata
            - /mnt/extssd/Portainer/Downloads/Youtube/Audio:/app/audio
            - /mnt/extssd/Portainer/Downloads/Youtube/Video:/app/video
            - /mnt/extssd/Portainer/Downloads/Youtube/Subscriptions:/app/subscriptions
            - /mnt/extssd/Portainer/Downloads/Youtube/Users:/app/users
        ports:
            - "1500:17442"
        environment: 
            ALLOW_CONFIG_MUTATIONS: 'true'
            ytdl_mongodb_connection_string: 'mongodb://ytdl-mongo-db:27017'
            ytdl_use_local_db: 'false'
            write_ytdl_config: 'true'
```

## Konfigurasi Custom Args
Konfigurasi video download untuk monitor mobil
Centang **Use Custom Args** dan **Replace Args**
```
-o,,video/%(title)s.mp4,,--write-info-json,,--print-json,,-f,,18/395+140,,--merge-output-format,,mp4,,--no-clean-infojson
```

Konfigurasi video download subtitle
```
--write-sub,,--write-auto-sub,,--sub-format,,srt,,--sub-lang,,EN
```






> Written with [StackEdit](https://stackedit.io/).
