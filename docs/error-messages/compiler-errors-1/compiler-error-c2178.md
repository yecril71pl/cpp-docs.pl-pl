---
title: C2178 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3727a66554b2e128061820df160c02a1370ebb74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171299"
---
# <a name="compiler-error-c2178"></a>C2178 błąd kompilatora  
  
"*identyfikator*"nie mogą być zadeklarowane z"*specyfikator*" Specyfikator  
  
A `mutable` specyfikator został użyty w deklaracji, ale specyfikator jest niedozwolony w tym kontekście.  
  
`mutable` Specyfikator mogą być stosowane tylko do nazwy elementów członkowskich danych klasy i nie można zastosować do nazwy zadeklarowany `const` lub `static`i nie można zastosować do odwołań do elementów członkowskich.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład przedstawia sposób C2178 może wystąpić i sposobu jego usunięcia.  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  
