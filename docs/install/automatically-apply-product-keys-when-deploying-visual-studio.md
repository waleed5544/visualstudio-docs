---
title: Automatically apply product keys
description: Learn how to apply product keys programmatically when you deploy Visual Studio.
ms.date: 09/24/2019
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
---
# Automatically apply product keys when deploying Visual Studio

You can apply your product key programmatically as part of a script that is used to automate the deployment of Visual Studio. You can set a product key on a device programmatically either during an installation of Visual Studio or after an installation completes.

::: moniker range="vs-2017"

## Apply the license after installation

You can activate an installed version of Visual Studio with a product key by using the `StorePID.exe` utility on the target machines, in silent mode. `StorePID.exe` is a utility program that installs with Visual Studio 2017 at the following default location:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Run `StorePID.exe` with elevated privileges, either by using a System Center agent or an elevated command prompt. Follow it with the product key and the Microsoft Product Code (MPC).

>[!IMPORTANT]
> Make sure to include the dashes in the product key.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## Apply the license after installation

You can activate an installed version of Visual Studio with a product key by using the `StorePID.exe` utility on the target machines, in silent mode. `StorePID.exe` is a utility program that installs with Visual Studio 2019 at the following default location:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Run `StorePID.exe` with elevated privileges, either by using a System Center agent or an elevated command prompt. Follow it with the product key and the Microsoft Product Code (MPC).

>[!IMPORTANT]
> Make sure to include the dashes in the product key.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end
:::moniker range="vs-2022"

## Apply the license after installation

You can activate an installed version of Visual Studio with a product key by using the `StorePID.exe` utility on the target machines, in silent mode. `StorePID.exe` is a utility program that installs with Visual Studio 2022 at the following default location:

```shell
C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE
```

 Run `StorePID.exe` with elevated privileges, either by using a System Center agent or an elevated command prompt. Follow it with the product key and the Microsoft Product Code (MPC).

>[!IMPORTANT]
> Make sure to include the dashes in the product key.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

The following example shows a command line for applying the license for Visual Studio 2017 Enterprise, which has an MPC of 08860, a product key of `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, and assumes a default installation location:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2022"

The following example shows a command line for applying the license for Visual Studio 2022 Enterprise, which has an MPC of 09660, a product key of `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, and assumes a default installation location:

```shell
"C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09660
```

::: moniker-end

::: moniker range="vs-2019"

The following example shows a command line for applying the license for Visual Studio 2019 Enterprise, which has an MPC of 09260, a product key of `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, and assumes a default installation location:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 The following table lists the MPC codes for each edition of Visual Studio:

| Visual Studio Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2022"

| Visual Studio Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2022        | 09660 |
| Visual Studio Professional 2022      | 09662 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

If `StorePID.exe` successfully applies the product key, it returns an `%ERRORLEVEL%` of 0. If it encounters errors, it returns one of the following codes, depending on the error condition:

| Error                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> When you run a virtual instance of Visual Studio, make sure that you also virtualize the local AppData folder and the registry. To troubleshoot virtual instances, run `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

::: moniker range="vs-2019"

If `StorePID.exe` successfully applies the product key, it returns an `%ERRORLEVEL%` of 0. If it encounters errors, it returns one of the following codes, depending on the error condition:

| Error                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> When you run a virtual instance of Visual Studio, make sure that you also virtualize the local AppData folder and the registry. To troubleshoot virtual instances, run `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

::: moniker range="vs-2022"

If `StorePID.exe` successfully applies the product key, it returns an `%ERRORLEVEL%` of 0. If it encounters errors, it returns one of the following codes, depending on the error condition:

| Error                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> When you run a virtual instance of Visual Studio, make sure that you also virtualize the local AppData folder and the registry. To troubleshoot virtual instances, run `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## See also

* [Install Visual Studio](../install/install-visual-studio.md)
* [Create an offline installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
