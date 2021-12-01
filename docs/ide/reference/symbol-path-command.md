---
title: Symbol Path Command
description: Learn about the Symbol Path command and how it sets the list of directories for the debugger to search for symbols.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
---
# Symbol Path Command
Sets the list of directories for the debugger to search for symbols.

## Syntax

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## Arguments
`pathname`

Optional. A semi-colon delimited list of paths for the debugger to search for symbols.

## Remarks
If no `pathname` is specified, the command lists the current symbol paths.

## Example 1
This example adds two paths to the list of symbol directories.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## Example 2
This example displays a semi-colon delimited list of current symbol paths.

```
Debug.SymbolPath
```

## See also

- [Command Window](../../ide/reference/command-window.md)
- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)
