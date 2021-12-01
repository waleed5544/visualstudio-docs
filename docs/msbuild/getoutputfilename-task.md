---
title: GetOutputFileName Task | Microsoft Docs
description: Use the MSBuild GetOutputFileName helper task to specify output file name options for cl.exe and other tools.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
---
# GetOutputFileName task

Helper task to get output file name for cl and other tools, which allow specifying only output directory or full file name or nothing.

## Parameters

The following table describes the parameters of the **GetOutputFileName** task.

|Parameter|Description|
|---------------|-----------------|
|**OutputExtension**|Required **string** parameter.|
|**OutputFile**|Optional **string** output parameter.|
|**OutputPath**|Optional **string** parameter.|
|**SourceFile**|Required **string** parameter.|

## See also

[Task reference](../msbuild/msbuild-task-reference.md)
