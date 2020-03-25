---
title: Błąd kompilatora C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202309"
---
# <a name="compiler-error-c2712"></a>Błąd kompilatora C2712

> nie można użyć __try w funkcjach, które wymagają odwinięcia obiektu

## <a name="remarks"></a>Uwagi

C2712 błędów może wystąpić, jeśli używasz [/EHsc](../../build/reference/eh-exception-handling-model.md), a funkcja z obsługą wyjątków strukturalnych również ma obiekty, które wymagają odwinięcia (zniszczenia).

Możliwe rozwiązania:

- Przenieś kod wymagający SEH z inną funkcją

- Ponownie Napisz funkcje, które używają SEH, aby uniknąć używania zmiennych lokalnych i parametrów, które mają destruktory. Nie używaj SEH w konstruktorach ani destruktorach

- Kompiluj bez/EHsc

Błąd C2712 może również wystąpić w przypadku wywołania metody zadeklarowanej za pomocą słowa kluczowego [__event](../../cpp/event.md) . Ponieważ zdarzenie może być używane w środowisku wielowątkowym, kompilator generuje kod, który uniemożliwia manipulowanie obiektem zdarzenia bazowego, a następnie umieszcza wygenerowany kod w [instrukcji SEH try-finally](../../cpp/try-finally-statement.md). W związku z tym Błąd C2712 wystąpi, jeśli wywołasz metodę zdarzenia i przejdziesz przez wartość argumentu, którego typ ma destruktor. Jednym z rozwiązań w tym przypadku jest przekazanie argumentu jako odwołania do stałej.

C2712 może również wystąpić, Jeśli kompilujesz z **/CLR: Pure** i deklaruj statyczną tablicę wskaźników do funkcji w bloku `__try`. Statyczny element członkowski wymaga, aby kompilator używał dynamicznej inicjacji z **/CLR: Pure**, co C++ oznacza obsługę wyjątków. Jednak obsługa C++ wyjątków nie jest dozwolona w bloku `__try`.

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2712 i pokazuje, jak rozwiązać ten problem.

```cpp
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
