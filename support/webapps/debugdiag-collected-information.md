---
title: Information collected by DebugDiag
description: Information on what is collected in DebugDiag Diagnostic.
ms.date: 03/19/2020
ms.prod-support-area-path:
---
# DebugDiag 1.2 Installation and Data Collector

This article describes the information that may be collected from a machine when running the DebugDiag 1.2 Installation and data collector.

_Original product version:_ &nbsp; Windows Server 2008 R2, 2008  
_Original KB number:_ &nbsp; 2700007

## Summary

The DebugDiag 1.2 Installation and Data Collector will install DebugDiag 1.2 to the machine, and allow the user to create a hang dump to upload to Microsoft. It also allows the user to run DebugDiag manually and upload data to Microsoft at a later time.

## Information collected

- Operating System

|Description|
|-|
|Machine Name:|
|OS Name:|
|Last Reboot/Uptime:|
|AntiMalware:|
|User Account Control:|
|Username:|
||

- Computer System

|Description|
|-|
|Computer Model:|
|Processor(s):|
|Machine Domain:|
|Role:|
||

- Hang Dump Files

|Description|File Name|
|--|--|
|Process Dump files|{Computername}\_SDPHangDumps_{Date}_{Time}.zip|
|||

- DebugDiag Data Files

|Description| File Name |
|--|--|
|File Folder specified by user that will contain data they want to upload to Microsoft.|{Computername}\_SDPDebugDiagData_{Date}_{Time}.zip|
|||

- DebugDiag Log Files

|Description| File Name |
|--|--|
|DebugDiag 1.2 Service and Rule Logs|{Computername}_DebugDiag_Logs.zip|
|||

## More information

If the user selects to install DebugDiag 1.2 to the machine, it will launch the DebugDiag 1.2 installer.  After installed, this troubleshooter won't remove DebugDiag 1.2 from the machine. Use Control Panel to uninstall the program if that is desired.

For more information, see [KB2598970 - Information about Microsoft Automated Troubleshooting Services and Support Diagnostic Platform](https://support.microsoft.com/help/2598970).
