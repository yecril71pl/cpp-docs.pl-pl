---
title: __restrict | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __restrict_cpp
dev_langs: C++
helpviewer_keywords: __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e854c87355831980f768fd0027f8ac70d9001a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="restrict"></a>__restrict
Podobnie jak **__declspec ( [ograniczyć](../cpp/restrict.md) )** , modyfikator `__restrict` — słowo kluczowe wskazuje, czy symbol nie jest używane z aliasem w bieżącym zakresie. `__restrict` — Słowo kluczowe różni się od `__declspec ( restrict )` modyfikator w następujący sposób:  
  
-   `__restrict` — Słowo kluczowe jest prawidłowa tylko dla zmiennych i `__declspec ( restrict )` jest prawidłowy tylko w deklaracji i definicji funkcji.  
  
-   `__restrict`przypomina `restrict` od specyfikacji C99, ale `__restrict` mogą być używane w C++ lub C programów.  
  
-   Gdy `__restrict` jest używana, kompilator nie zostaną przeniesione właściwości aliasu nie zmiennej. Oznacza to po przypisaniu `__restrict` zmiennej niż`__restrict` zmiennej, kompilator zezwala nie __restrict zmienną jako alias. Ta lokalizacja jest inna od zachowania `restrict` — słowo kluczowe ze specyfikacji C99.  
  
 Ogólnie rzecz biorąc, jeśli mają wpływ na zachowanie całej funkcji, lepiej jest użyć `__declspec ( restrict )` niż słowo kluczowe.  
  
 W programie Visual Studio 2015 lub nowszego oraz `__restrict` może być używany z odwołania C++.  
  
> [!NOTE]
>  Jeśli używany w zmiennej, która ma również [volatile](../cpp/volatile-cpp.md) — słowo kluczowe, `volatile` mają wyższy priorytet.  
  
## <a name="example"></a>Przykład  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)