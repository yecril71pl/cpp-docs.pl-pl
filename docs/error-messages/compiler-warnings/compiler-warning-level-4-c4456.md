---
title: "Kompilatora (poziom 4) ostrzeżenie C4456 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4456
dev_langs: C++
helpviewer_keywords: C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 937475e32ce3c57633f0d0c504ce0ca4b7c627c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4456"></a>Kompilator C4456 ostrzegawcze (poziom 4)
  
> Deklaracja "*identyfikator*" powoduje ukrycie poprzedniej deklaracji lokalnej
  
Deklaracja *identyfikator* w zakresie lokalnej powoduje ukrycie deklaracji poprzedniej deklaracji lokalnej o tej samej nazwie. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w zakresie lokalnym rozpoznać do lokalnie zgłoszonego wersji nie poprzedniej lokalny, który może lub nie jest celem użytkownika. Aby rozwiązać ten problem, zaleca się, że możesz nadać nazwy zmiennych lokalnych, które nie są w konflikcie z innych lokalnych nazw.  
    
## <a name="example"></a>Przykład
  
Poniższy przykład generuje C4456, ponieważ pętli kontrolować zmiennej `int x` i zmienna lokalna `double x` w `member_fn` o takich samych nazwach. Aby rozwiązać ten problem, użyj różnych nazw dla zmiennych lokalnych.  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  
