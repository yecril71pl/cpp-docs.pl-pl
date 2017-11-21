---
title: "C3368 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3368
dev_langs: C++
helpviewer_keywords: C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86996ade6501ba83e1895f6ba9b30d62526ff442
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3368"></a>C3368 błąd kompilatora
"deklaracji funkcji": Nieprawidłowa konwencja wywoływania dla języka IDL  
  
 Można używać tylko [__stdcall](../../cpp/stdcall.md) lub [__cdecl](../../cpp/cdecl.md) konwencji wywoływania w pliku .idl.  
  
 Poniższy przykład generuje C3368:  
  
```  
// C3368.cpp  
// processor: x86  
[idl_module(name="Name", dllname="Some.dll")];  
  
[idl_module(name="Name")]  
int __fastcall f1();   // C3368  
```