---
title: "Compiler Error C2673 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-tools"]
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: ["C2673"]
dev_langs: ["C++"]
helpviewer_keywords: ["C2673"]
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2673
'function' : global functions do not have 'this' pointers  
  
 A global function tried to access `this`.  
  
 The following sample generates C2673:  
  
```  
// C2673.cpp  
int main() {  
   this = 0;   // C2673  
}  
```