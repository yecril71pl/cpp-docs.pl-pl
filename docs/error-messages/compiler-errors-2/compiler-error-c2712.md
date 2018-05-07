---
title: C2712 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26c5d7a24c022cacf4c20687b2d8c58f7e9e342
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2712"></a>C2712 błąd kompilatora
Nie można użyć __try w funkcjach, które wymagają rozwinięcia obiektu  
  
 C2712 błąd może wystąpić, jeśli używasz [/ehsc](../../build/reference/eh-exception-handling-model.md), i funkcji z obsługi wyjątków strukturalnych również zawiera obiekty, które wymagają odwijaniem (zniszczenie).  
  
 Możliwe rozwiązania:  
  
-   Przenieś kod, który wymaga SEH na inną funkcję  
  
-   Należy zmodyfikować funkcje, które umożliwiają Unikaj używania zmiennych lokalnych i parametrów, które mają destruktory SEH. Nie używaj SEH w konstruktorów ani destruktorów  
  
-   Kompiluj bez/ehsc  
  
 C2712 błąd może wystąpić, gdy wywołanie metody zadeklarowanej przy użyciu [__event](../../cpp/event.md) — słowo kluczowe. Ponieważ zdarzenia mogą być używane w środowisku wielowątkowym, kompilator generuje kod, który uniemożliwia manipulowania obiektu podstawowego zdarzeń i następnie dodaje wygenerowany kod SEH [try-finally — instrukcja](../../cpp/try-finally-statement.md). W rezultacie C2712 wystąpi błąd wywołania metody zdarzeń i przekazanie przez wartość argumentu, którego typ ma destruktor. Jedno rozwiązanie w tym przypadku jest przekazanie argument jako odwołanie stałej.  
  
## <a name="example"></a>Przykład  
 C2712 może również wystąpić w przypadku kompilacji z **/CLR: pure** ani deklarować statycznych tablicy wskaźników do funkcji w `__try` bloku. Statyczny element członkowski wymaga kompilator, aby używał dynamiczna Inicjalizacja w obszarze **/CLR: pure**, co oznacza C++, obsługa wyjątków. Jednak C++, obsługa wyjątków nie jest dozwolona w `__try` bloku.  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Poniższy przykład generuje C2712 i pokazuje, jak go naprawić.  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```