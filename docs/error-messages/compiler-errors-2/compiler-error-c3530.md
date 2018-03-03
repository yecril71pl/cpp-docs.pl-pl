---
title: "C3530 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a71820e6303c67e3d247c7da6dddc184e5cb41a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3530"></a>C3530 błąd kompilatora
"auto" nie można łączyć z jakimkolwiek innym specyfikatorem typu  
  
 Specyfikator typu jest używana z `auto` — słowo kluczowe.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Nie należy używać specyfikatora typu w deklaracji zmiennej, która używa `auto` — słowo kluczowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3530, ponieważ zmienna `x` zadeklarowano zarówno `auto` — słowo kluczowe i typ `int`, i dlatego przykładzie jest skompilowana przy użyciu **/Zc: Auto**.  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto, słowo kluczowe](../../cpp/auto-keyword.md)