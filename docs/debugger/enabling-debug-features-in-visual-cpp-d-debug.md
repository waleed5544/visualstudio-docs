---
title: "Enabling Debug Features in C++ projects (-D_DEBUG) | Microsoft Docs"
description: In Visual C++ you enable debugging features by defining _DEBUG. Learn how to do this, and learn how to link an MFC program in order to debug it.
ms.custom: SEO-VS-2020
ms.date: "11/04/2016"
ms.topic: "conceptual"
f1_keywords:
  - "vs.debug"
dev_langs:
  - "CSharp"
  - "VB"
  - "FSharp"
  - "C++"
helpviewer_keywords:
  - "/D_DEBUG compiler option [C++]"
  - "debugging [C++], enabling debug features"
  - "debugging [MFC], enabling debug features"
  - "assertions, enabling debug features"
  - "D_DEBUG compiler option"
  - "MFC libraries, debug version"
  - "debug builds, MFC"
  - "_DEBUG macro"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "cplusplus"
---
# Enabling Debug Features in C++ projects (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], debugging features such as assertions are enabled when you compile your program with the symbol **_DEBUG** defined. You can define **_DEBUG** in one of two ways:

- Specify **#define _DEBUG** in your source code, or

- Specify the **/D_DEBUG** compiler option. (If you create your project in Visual Studio using wizards, **/D_DEBUG** is defined automatically in the Debug configuration.)

  When **_DEBUG** is defined, the compiler compiles sections of code surrounded by **#ifdef _DEBUG** and `#endif`.

  The Debug configuration of an MFC program must link with a Debug version of the MFC library. The MFC header files determine the correct version of the MFC library to link with based on the symbols you have defined, such as **_DEBUG** and **_UNICODE**. For details, see [MFC Library Versions](/cpp/mfc/mfc-library-versions).

## See also
- [Debugging Native Code](../debugger/debugging-native-code.md)
- [Project Settings for a C++ Debug Configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md)