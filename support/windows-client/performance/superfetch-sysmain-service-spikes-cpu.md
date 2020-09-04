---
title: SuperFetch(SysMain) service consumes CPU
description: Works around an issue where the system experiences CPU spike for 1-2 minutes when a 64-bit application runs in the 64-bit version of Windows.
ms.date: 09/04/2020
author: delhan
ms.author: Delead-Han
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-client
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Applications
ms.technology: Performance
---
# SuperFetch(SysMain) service spikes the CPU for 1-2 minute when a 64-bit application is running in Windows Vista or in Windows 7

This article provides a workaround for an issue where the system experiences CPU spike for 1-2 minutes when a 64-bit application runs in the 64-bit version of Windows.

_Original product version:_ &nbsp; Windows 7 Service Pack 1  
_Original KB number:_ &nbsp; 2723033

## Symptoms

When a 64-bit application compiled with `/LARGEADDRESSAWARE:NO` option is running in the 64-bit versions of Windows Vista or in the 64-bit versions of Windows 7, the system may experience CPU spike for 1-2 minutes and this goes on in-definitely. In this situation, the Task Manager shows the svchost.exe process hosting the SysMain(SuperFetch) service is consuming the CPU utilization.

## Cause

Windows creates a single read-only Virtual Address Descriptor (VAD) for the address space above 2 GB while creating the process. SuperFetch while scanning the VAD tree of the running process encounters the VAD and spins with the huge VAD size, causing the CPU to spike.

## Workaround

To work around this issue, avoid option `/LARGEADDRESSAWARE:NO` while compiling the applications.

Note: By default a 64-bit application makes use of the Extended Address Space (8 terabytes per process).
