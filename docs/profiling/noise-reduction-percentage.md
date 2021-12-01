---
title: "Noise Reduction Percentage | Microsoft Docs"
description: Learn about the Noise Reduction Percentage setting and how you can control the number of entries that are displayed in the call tree.
ms.date: "11/04/2016"
ms.topic: "conceptual"
f1_keywords:
  - "vs.cv.threads.filter"
helpviewer_keywords:
  - "Concurrency Visualizer, Noise Reduction Percentage"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "multiple"
---
# Noise Reduction Percentage
By default, the value of the Noise Reduction Percentage setting is 2. Only entries that have a percentage of inclusive time greater than or equal to this setting are shown in the call tree. By changing the setting, you can control the number of entries that are displayed in the call tree. For example, changing the value to 10 will show only call tree entries that have an inclusive time greater than or equal to 10%. By increasing the value of the setting, you can focus on entries that have larger impacts on the performance of your process.