---
title: "Kompilatora (poziom 4) ostrzeżenie C4457 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4457
dev_langs: C++
helpviewer_keywords: C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a8ede4500e579436d5d6b9db581a06c14a6aca43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4457"></a>Kompilator C4457 ostrzegawcze (poziom 4)
  
> Deklaracja "*identyfikator*" powoduje ukrycie parametru funkcji
  
Deklaracja *identyfikator* w zakresie lokalnej powoduje ukrycie deklaracji parametru funkcji takiej samej nazwie. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w zakresie lokalnym rozpoznać do lokalnie zgłoszonego wersji nie parametr, który może lub nie jest celem użytkownika. Aby rozwiązać ten problem, zaleca się, że możesz nadać nazwy zmiennych lokalnych, które nie są w konflikcie z nazwy parametru.  
    
## <a name="example"></a>Przykład
  
Poniższy przykład generuje C4457, ponieważ parametr `x` i zmienna lokalna `x` w `member_fn` o takich samych nazwach. Aby rozwiązać ten problem, użyj różnych nazw parametrów i zmiennych lokalnych.  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
