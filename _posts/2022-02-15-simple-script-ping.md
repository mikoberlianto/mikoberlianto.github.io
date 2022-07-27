---
layout: post
title: "Simple script ping service"
subtitle: "Make a simple bat file to execute ping service on Windows OS"
tags: [script,windows]
---
# **Simple Script Bat File to Execute PING service**

## Make file START PING

Open your favorite text-editor such as Notepad or Notepad++ and make new file named it `PINGSTART.bat` copy paste below script to that file
``` bat
@echo off
setlocal

set "iplist=iplist.txt"

if not exist "%iplist%" (
    echo Missing IPLIST file "%iplist.txt"
    exit /b
)

for /f "usebackq tokens=*" %%i in ("%iplist%") do (
    start pingloop.bat %%~i
)
```
## Make file PING LOOP
Make another file name `PINGLOOP.bat` and copy paste below script to that file

```bat
@echo off
setlocal

set colorUp=2F
set colorDown=4F

if "%~1" EQU "" (
    exit /b
)

title IP:%~1 - Status:

:Loop
    echo %DATE% %TIME%
    ping -n 1 -l 0 %~1 | find "TTL=" && (
        color %colorUp%
        title IP:%~1 - Status:UP
    ) || (
        color %colorDown%
        title IP:%~1 - Status:DOWN
    )
    goto :Loop
```
## Make file IP LIST
Final file make named `IPLIST.txt` and type ip address you wanna monitored by ping such as
```
8.8.8.8
192.168.0.1
google.com
```

## Start Script
To running script just double click file named `PINGSTART.bat` there will be opened new command line windows as many as your IP LIST monitored. If green mean UP and red DOWN.

> Written with [StackEdit](https://stackedit.io/).