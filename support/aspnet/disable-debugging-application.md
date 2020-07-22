---
title: Disable debugging for ASP.NET application
description: This article discusses how to disable debugging for ASP.NET applications
ms.date: 03/27/2020
ms.prod-support-area-path: FTP authentication and authorization
ms.topic: how-to
---
# Disable debugging for ASP.NET applications

This article discusses how to disable debugging for ASP.NET applications.

_Original product version:_ &nbsp; ASP.NET  
_Original KB number:_ &nbsp; 815157

## Summary

ASP.NET supports compiling applications in a special debug mode that facilitates developer troubleshooting. Debug mode causes ASP.NET to compile applications with extra information that enables a debugger to closely monitor and control the execution of an application. Applications that are compiled in debug mode execute as expected. However, the performance of the application is affected. To avoid the effect on performance, it's a good idea to enable debugging only when a developer is doing interactive troubleshooting. By default, debugging is disabled, and although debugging is frequently enabled to troubleshoot a problem, it's also frequently not disabled again after the problem is resolved. This article describes how to disable debugging for an ASP.NET application.

To disable debugging, modify the *Web.config* file or the *Machine.config* file, as detailed in the following sections.

## Method 1: Modify the Web.config file

To disable debugging, add the compilation element to the *Web.config* file of the application. The *Web.config* file is located in the application directory. To do this, follow these steps:

1. Open the *Web.config* file in a text editor such as Notepad.exe. Web.config file is typically located in the application directory.
2. In the Web.config file, locate the compilation element. Debugging is enabled when the debug attribute in the compilation element is set to **true**.
3. Modify the debug attribute to **false**, and then save the Web.config file to disable debugging for that application.

    The following code sample shows the compilation element with debug set to **false**:

    ```xml
    <compilation
     debug="false"
    />
    ```

4. Save the Web.config file. The ASP.NET application automatically restarts.

## Method 2: Modify the Machine.config file

You can also disable debugging for all applications on a system by modifying the *Machine.config* file. To confirm that debugging hasn't been enabled in the Machine.config file, follow these steps.

1. Open the Machine.config file in a text editor such as Notepad.exe. The Machine.config file is typically located in the following folder:  

    `%SystemRoot%\Microsoft.NET\Framework\%VersionNumber%\CONFIG\`
2. In the `Machine.config` file, locate the compilation element. Debugging is enabled when the debug attribute in the compilation element is set to **true**.
3. If the debug attribute is **true**, change the debug attribute to **false**.

    The following code sample shows the compilation element with debug set to **false**:

    ```xml
    <compilation
     debug="false"
    />
    ```

4. Save the Machine.config file.
