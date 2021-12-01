---
title: -Diff (devenv.exe)
description: Learn how to use the Diff devenv command-line switch to compare two files.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
---
# /Diff (devenv.exe)

Compares two files. The differences are displayed in a special Visual Studio window.

## Syntax

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## Arguments

- *SourceFile*

  Required. The full path and name of the first file to be compared.

- *TargetFile*

  Required. The full path and name of the second file to be compared.

- *SourceDisplayName*

  Optional. The display name of the first file.

- *TargetDisplayName*

  Optional. The display name of the second file.

## Remarks

If an instance of the IDE is already open, the file comparison appears in a tab in the current IDE.

## Example

The first example compares two files without changing their display names. The second example compares the files while changing both of their display names. The third and fourth examples compare two files but apply an alias to only the first file or the second file.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## See also

- [Devenv command-line switches](../../ide/reference/devenv-command-line-switches.md)
