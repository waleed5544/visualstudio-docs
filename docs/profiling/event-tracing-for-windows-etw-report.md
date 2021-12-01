---
title: "Event Tracing for Windows (ETW) Report | Microsoft Docs"
description: Read about the Event Tracing for Windows (ETW) report, which lists the ETW events that were recorded in a performance session of Visual Studio Profiling Tools.
ms.custom: SEO-VS-2020
ms.date: "11/04/2016"
ms.topic: "conceptual"
helpviewer_keywords:
  - "Event tracing for Windows profiling report"
  - "ETW profiling report"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: 'vs-2017'
ms.workload:
  - "multiple"
---
# Event Tracing for Windows (ETW) report
The Event Tracing for Windows (ETW) report lists the ETW events that were recorded in a performance session of [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools. ETW data is collected in a binary (.*etl*) file.

> [!NOTE]
> You cannot display ETW reports in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface.

- For information about how to collect ETW by using the Profiling Tools from [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface, see [How to: Collect Event Tracing for Windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- For information about how to collect ETW data by using the [VSPerfCmd](../profiling/vsperfcmd.md) command line tools, see [Events](../profiling/events-vsperfcmd.md).

- You generate the ETW report by using the **VSReport/Summary:ETW** command. For more information, see [VSPerfReport](../profiling/vsperfreport.md).

|Column|Description|
|------------|-----------------|
|**Timestamp**|Identifies when the event occurred.|
|**Process ID**|Identifies the process that generated the event.|
|**Thread ID**|Identifies the thread that generated the event.|
|**Description**|Identifies the event provider.|
|**Type**|Identifies the event type.|
|**Properties**|The properties of the event. Each event is a comma-separated, name-value pair that is enclosed in brackets.|
