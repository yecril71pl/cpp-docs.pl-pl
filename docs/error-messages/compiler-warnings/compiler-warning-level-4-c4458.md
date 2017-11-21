---
title: "Kompilatora (poziom 4) ostrzeżenie C4458 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4458
dev_langs: C++
helpviewer_keywords: C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 455b7173221e05b0da0f73a5c1401d1114297b14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4458"></a>Kompilator C4458 ostrzegawcze (poziom 4)
  
> Deklaracja "*identyfikator*" powoduje ukrycie elementu członkowskiego klasy
  
Deklaracja *identyfikator* w zakresie lokalnej powoduje ukrycie deklaracji o takiej samej nazwie *identyfikator* w zakresie klasy. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w tym zakresie rozwiązania do lokalnie zgłoszonego wersji, a nie wersji elementu członkowskiego klasy, która może lub nie jest celem użytkownika. Aby rozwiązać ten problem, zaleca się, że możesz nadać nazwy zmiennych lokalnych, które nie są w konflikcie z nazwą elementu członkowskiego klasy.  
    
## <a name="example"></a>Przykład
  
Poniższy przykład generuje C4458, ponieważ parametr `x` i zmienna lokalna `y` w `member_fn` mają takie same nazwy jako elementy członkowskie danych w klasie. Aby rozwiązać ten problem, użyj różnych nazw parametrów i zmiennych lokalnych.  
  
```cpp  
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;  
        // To fix this issue, change the parameter name x
        // and local name y to something that does not 
        // conflict with the data member names.
    }
} s;
```  
