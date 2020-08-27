---
title: Błąd kompilatora C2712
description: Opis błędu kompilatora Microsoft C/C++ C2712.
ms.date: 08/25/2020
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 2f0b883607241473a429919e06de9e975fa2e3c1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898697"
---
# <a name="compiler-error-c2712"></a>Błąd kompilatora C2712

> nie można użyć `__try` w funkcjach, które wymagają odwinięcia obiektu

## <a name="remarks"></a>Uwagi

C2712 błędów może wystąpić, jeśli używasz [`/EHsc`](../../build/reference/eh-exception-handling-model.md) , a funkcja z obsługą wyjątków strukturalnych również ma obiekty, które wymagają odwinięcia (zniszczenia).

Możliwe rozwiązania:

- Przenieś kod wymagający SEH z inną funkcją

- Ponownie Napisz funkcje, które używają SEH, aby uniknąć używania zmiennych lokalnych i parametrów, które mają destruktory. Nie używaj SEH w konstruktorach ani destruktorach

- Kompiluj bez/EHsc

Błąd C2712 może również wystąpić w przypadku wywołania metody zadeklarowanej za pomocą [`__event`](../../cpp/event.md) słowa kluczowego. Ze względu na to, że zdarzenie może być używane w środowisku wielowątkowym, kompilator generuje kod, który uniemożliwia manipulowanie obiektem zdarzenia bazowego, a następnie umieszcza wygenerowany kod w [ `try-finally` instrukcji](../../cpp/try-finally-statement.md)SEH. W związku z tym Błąd C2712 wystąpi, jeśli wywołasz metodę zdarzenia i przejdziesz przez wartość argumentu, którego typ ma destruktor. Jednym z rozwiązań w tym przypadku jest przekazanie argumentu jako odwołania do stałej.

C2712 może również wystąpić, Jeśli kompilujesz z **`/clr:pure`** i deklarujesz tablicę statyczną wskaźników do funkcji w **`__try`** bloku. Statyczny element członkowski wymaga, aby kompilator używał inicjowania dynamicznego w **`/clr:pure`** , co oznacza obsługę wyjątków C++. Jednak obsługa wyjątków C++ nie jest dozwolona w **`__try`** bloku.

**`/clr:pure`** **`/clr:safe`** Opcje kompilatora i są przestarzałe w programie visual Studio 2015 i nie są obsługiwane w programie visual Studio 2017.

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
