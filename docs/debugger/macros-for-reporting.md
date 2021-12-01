---
title: "Macros for Reporting | Microsoft Docs"
description: Learn about the debugging macros _RPTn and _RPTFn provided in CRTDBG.H, and about creating your own debugging macros.
ms.custom: SEO-VS-2020
ms.date: "11/04/2016"
ms.topic: "conceptual"
f1_keywords:
  - "vs.debug.macros"
dev_langs:
  - "CSharp"
  - "VB"
  - "FSharp"
  - "C++"
helpviewer_keywords:
  - "macros, CRT reporting macros"
  - "macros, debugging with"
  - "_RPTFn macro"
  - "CRT, reporting macros"
  - "debugging [CRT], reporting macros"
  - "_RPTn macro"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "multiple"
---
# Macros for Reporting
For debugging, you can use the **_RPTn** and **_RPTFn** macros, defined in CRTDBG.H, to replace the use of `printf` statements. You don't need to inclose them in **#ifdef**s, because they automatically disappear in your release build when **_DEBUG** isn't defined.

|Macro|Description|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Outputs a message string and zero to four arguments. For **_RPT1** through **_RPT4**, the message string serves as a printf-style formatting string for the arguments.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Same as **_RPTn**, but these macros also output the file name and line number where the macro is located.|

 Consider the following example:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 This code outputs the values of `someVar` and `otherVar` to **stdout**. You can use the following call to `_RPTF2` to report these same values and, additionally, the file name and line number:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

You might find that a particular application needs debug reporting that the macros supplied with the C run-time library do not provide. For these cases, you can write a macro designed specifically to fit your own requirements. In one of your header files, for example, you could include code like the following to define a macro called **ALERT_IF2**:

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 One call to **ALERT_IF2** could do all the functions of the **printf** code:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 You can easily change a custom macro to report more or less information to different destinations. This approach is particularly useful as your debugging requirements evolve.

## See also
- [CRT Debugging Techniques](../debugger/crt-debugging-techniques.md)
