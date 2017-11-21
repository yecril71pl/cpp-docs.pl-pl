---
title: "C2178 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2178
dev_langs: C++
helpviewer_keywords: C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: facb255b0c53a3de0e1d5c9f90de5835b25e3c32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
