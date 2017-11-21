---
title: "C2128 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: c2128
dev_langs: C++
helpviewer_keywords: C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0739af6c84b2dc1a7f86c5cb4843ce66e85bf85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2128"></a>C2128 błąd kompilatora
"Funkcja": alloc_text/same_seg dotyczy tylko funkcji z powiązaniem C  
  
 `pragma``alloc_text` można używać tylko z funkcjami zadeklarowana, aby mieć powiązanie C.  
  
 Poniższy przykład generuje C2128:  
  
```  
// C2128.cpp  
// compile with: /c  
  
// Delete the following line to resolve.  
void func();  
// #pragma alloc_text("my segment", func)   // C2128  
  
extern "C" {  
void func();  
}  
  
#pragma alloc_text("my segment", func)  
void func() {}  
```