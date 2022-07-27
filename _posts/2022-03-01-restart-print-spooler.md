---
layout: post
title: "Belajar ke 3"
subtitle: "Membuat dan menjalankan script batch untuk restart service Print Spooler"
tags: [batch,script,windows]
---
# **Restart Service Print Spooler** 
## Pengenalan
File batch ini untuk merestart service print spooler, dijalankan dengan administrator privilage.

```
@echo off

:: BatchGotAdmin
:-------------------------------------
REM  --> Check for permissions
    IF "%PROCESSOR_ARCHITECTURE%" EQU "amd64" (
>nul 2>&1 "%SYSTEMROOT%\SysWOW64\cacls.exe" "%SYSTEMROOT%\SysWOW64\config\system"
) ELSE (
>nul 2>&1 "%SYSTEMROOT%\system32\cacls.exe" "%SYSTEMROOT%\system32\config\system"
)

REM --> If error flag set, we do not have admin.
if '%errorlevel%' NEQ '0' (
    echo Requesting administrative privileges...
    goto UACPrompt
) else ( goto gotAdmin )

:UACPrompt
    echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
    set params= %*
    echo UAC.ShellExecute "cmd.exe", "/c ""%~s0"" %params:"=""%", "", "runas", 1 >> "%temp%\getadmin.vbs"

    "%temp%\getadmin.vbs"
    del "%temp%\getadmin.vbs"
    exit /B

:gotAdmin
    pushd "%CD%"
    CD /D "%~dp0"
:--------------------------------------    

ECHO Stopping print spooler.
ECHO #*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#
NET stop spooler
ECHO deleting temp files.
ECHO #*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#
DEL %windir%\system32\spool\printers\*.* /q
ECHO Starting print spooler.
ECHO #*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#*#
NET start spooler

PAUSE
```


source: [stackoverflow](https://stackoverflow.com/questions/1894967/how-to-request-administrator-access-inside-a-batch-file) dan [spiceworks](https://community.spiceworks.com/scripts/show/1577-clear-and-reset-print-spooler)
> Written with [StackEdit](https://stackedit.io/).