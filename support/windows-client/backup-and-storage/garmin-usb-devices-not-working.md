---
title: Garmin is not compatible with Windows 10
description: Fixes an issue that prevents Garmin wearable devices from working after you've upgraded your computer or device to Windows 10.
ms.date: 07/27/2020
author: delhan
ms.author: Deland-Han
manager: dscontentpm
audience: ITPro
ms.topic: troubleshooting
ms.prod: windows-client
localization_priority: medium
ms.reviewer: kaushika, tiquinn, scottmca
ms.prod-support-area-path: Storage hardware
ms.technology: BackupStorage
---
# Garmin USB devices don't work with Windows 10

This article provides information on how to fix the problem that Garmin wearable devices aren't recognized on Windows 10.

_Original product version:_ &nbsp; Windows 10, version 1709  
_Original KB number:_ &nbsp; 3183365

## Symptoms

After you upgrade a computer or device to Windows 10, certain Garmin wearable devices may not work as expected when they're connected to a USB port.

Although the Garmin device shows up in Device Manager and is displayed as a connected drive in File Explorer, it is not accessible. Attempts to access the drive trigger errors such as the following:

> Please insert a disk.

> The directory name is invalid.

## Cause

This problem occurs because Garmin devices that are formatted with FAT12, FAT16, or FAT32 file systems are not recognized as mass storage devices by a computer or device that's running Windows 10.

## Resolution

To resolve the issue, download and install the latest version of Garmin Express software. The Garmin Express tool recognizes the connected device and updates its boot code to make it compatible with Windows 10.

This issue is documented by Garmin at [Device is not detected in Windows 10 after updating to the Anniversary update](https://static.garmin.com/com.garmin.static-pages/cf-maintenance-500.html?site=forums).

To download the latest Garmin Express tool, go to [Garmin Express](https://software.garmin.com/express.html).

[!INCLUDE [Third-party disclaimer](../../includes/third-party-disclaimer.md)]

## Applies to

- Windows 10, version 1709
- Windows 10, version 1607
