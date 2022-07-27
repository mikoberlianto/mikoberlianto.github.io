---
layout: post
title: "Belajar ke 2"
subtitle: "Membuat dan menjalankan script Python untuk menscrape post di instagram"
tags: [python,script,windows]
---
# **instagram-scraper** 
## Pengenalan
instagram-scraper adalah aplikasi berbasis command-line di tulis dengan bahasa pemograman Python yang men-scrape dan men-download foto dan video dari user-user di instagram. Gunakan dengan bijak.

Di buat dan dimaintance oleh github user [arc298](https://github.com/arc298) (sebelumnya *rarcega*) dan seluruh kontributor yang sudah men-support dalam project ini. Kamu bisa mempelajari dan mendownload nya di # [arc298/**instagram-scraper**](https://github.com/arc298/instagram-scraper)

## Implementasi
Clone atau download script kedalam directory mu. 
Buat file dengan nama **ig_users.txt** di dalam folder `./instagram-scraper/` sebagai berikut:
```
#nama user ig per baris
user1
user2
user..
```
Buat file dengan nama **cookiejar.txt** kosong di dalam folder `./instagram-scraper/` sebagai berikut:
```
#Disini kosong, tanpa text/komen
```
Buat file dengan nama **timestamps.txt** kosong di dalam folder `./instagram-scraper/` sebagai berikut:
```
#Disini kosong, tanpa text/komen
```

Buat file dengan nama **insta_args.txt** di dalam folder `./instagram-scraper/` sebagai berikut:
```
--maximum=5
--login-user=username_here
--login-pass=password_here
--media-types=image,video
--filename=ig_users.txt
--template={username}-{year}{month}{day}-{h}{m}{s}-{mediatype}-{urlname}
--retain-username
--latest
--profile-metadata
--comments
--retry-forever
--cookiejar=cookiejar.txt
--destination=./data/
--latest-stamps=timestamps.txt
```
Terakhir untuk otomatisasi, kita buat file batch dengan nama file **donlotautoreload.bat** di dalam folder `./instagram-scraper/` sebagai berikut:
```
@echo off

REM start over again
:LOOP

REM Random timeout after do it
SET /A istrht=%RANDOM%*1800/32768+600

REM set Batch file from current location
SET "CURPATH=%~dp0"
rem %CUREPATH:~0,-1%

REM Check file
:cekscraper
IF EXIST "%CURPATH%\insta_args.txt" (
    GOTO mulaiscraper
) ELSE (
    GOTO donlodscraper
)

:donlodscraper
CLS
ECHO  ............................................
ECHO               Scraper not found
ECHO       Download rarcega/Instagram-Scraper
ECHO  https://github.com/rarcega/instagram-scraper
ECHO  ............................................
GOTO LOOP

:mulaiscraper
REM cd /D "%~dp0"
REM ECHO ya benar directory
ECHO Folder sekarang :
CD %CUREPATH%
DIR
pip install instagram-scraper
pip install instagram-scraper --upgrade
python setup.py install
ECHO ............................................
ECHO Nama Module
python setup.py --name
ECHO Versi Module
python setup.py --version
ECHO ............................................
ECHO Memulai scrap user instagram
instagram-scraper @insta_args.txt

REM Back to start again after 2~10 minute
TIMEOUT %istrht%
GOTO LOOP
```
## Opsional file
**timestamps.txt** dan **instagram-scraper.log**

## Maping directory
```
./instagram-scraper
|-instagram_craper
  |-tests
    |-fixtures
      |-response_explore_location.json
      |-response_explore_tags.json
      |-response_first_page.json
      |-response_query_hashtag_first_page.json
      |-response_query_hashtag_second_page.json
      |-response_second_page.json
      |-response_user_metadata.json
      |-response_view_media_video.json
    |-_init_.py
    |-_test_instagram.py
  |-_init_.py
  |-app.py
  |-constants.py
|-setup.cfg
|-setup.py
|-ig_users.txt
|-cookiejar.txt
|-insta_args.txt
|-timestamps.txt
|-instagram-scraper.log


```

> Written with [StackEdit](https://stackedit.io/).