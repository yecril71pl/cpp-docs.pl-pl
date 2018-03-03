---
title: "Kompilatora (poziom 4) ostrzeżenie C4456 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e298f092f546c589606be42b6e7b9faed15ddd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
