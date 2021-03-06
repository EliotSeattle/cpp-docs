---
title: "LoadLibrary and AfxLoadLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-tools"]
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: ["LoadLibrary"]
dev_langs: ["C++"]
helpviewer_keywords: ["DLLs [C++], AfxLoadLibrary", "DLLs [C++], LoadLibrary", "AfxLoadLibrary method", "LoadLibrary method", "explicit linking [C++]"]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LoadLibrary and AfxLoadLibrary
Processes call [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) (or [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) to explicitly link to a DLL. If the function succeeds, it maps the specified DLL into the address space of the calling process and returns a handle to the DLL that can be used with other functions in explicit linking—for example, `GetProcAddress` and `FreeLibrary`.  
  
 `LoadLibrary` attempts to locate the DLL by using the same search sequence that is used for implicit linking. If the system cannot find the DLL or if the entry-point function returns FALSE, `LoadLibrary` returns NULL. If the call to `LoadLibrary` specifies a DLL module that is already mapped into the address space of the calling process, the function returns a handle of the DLL and increments the reference count of the module.  
  
 If the DLL has an entry-point function, the operating system calls the function in the context of the thread that called `LoadLibrary`. The entry-point function is not called if the DLL is already attached to the process because of a previous call to `LoadLibrary` that has no corresponding call to the `FreeLibrary` function.  
  
 For MFC applications that load MFC extension DLLs, we recommend that you use `AfxLoadLibrary` instead of `LoadLibrary`. `AfxLoadLibrary` handles thread synchronization before you call `LoadLibrary`. The interface (function prototype) to `AfxLoadLibrary` is the same as `LoadLibrary`.  
  
 If Windows cannot load the DLL, the process can attempt to recover from the error. For example, the process could notify the user of the error and ask the user to specify another path to the DLL.  
  
> [!IMPORTANT]
>  If the code is to run under Windows NT 4, Windows 2000, or Windows XP (prior to SP1), make sure to specify the full path of any DLLs. On these operating systems, the current directory is searched first when files are loaded. If you do not qualify the path of the file, a file that is not the intended one might be loaded.  
  
## What do you want to do?  
  
-   [How to link implicitly to a DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Determine which linking method to use](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## What do you want to know more about?  
  
-   [The search path that is used by Windows to locate a DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary and AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## See Also  
 [DLLs in Visual C++](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)