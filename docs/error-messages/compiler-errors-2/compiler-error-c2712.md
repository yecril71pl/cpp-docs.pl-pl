---
title: Błąd kompilatora C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 19b9c5a54bf405114bd4d596c2a2cc4708aadcc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386794"
---
# <a name="compiler-error-c2712"></a>Błąd kompilatora C2712

> Nie można Użyj __try w funkcjach, które wymagają rozwinięcia obiektu

## <a name="remarks"></a>Uwagi

C2712 błąd może wystąpić, jeśli używasz [/ehsc](../../build/reference/eh-exception-handling-model.md), i funkcji z obsługi wyjątków strukturalnych, również ma obiektów, które wymagają odwijania (niszczenie).

Możliwe rozwiązania:

- Przenieś kod, który wymaga strukturalnej obsługi wyjątków do innej funkcji

- Należy zmodyfikować funkcje, które Użyj strukturalnej obsługi wyjątków, aby uniknąć użycia zmienne lokalne i parametry, które mają destruktory. Nie używaj strukturalnej obsługi wyjątków w konstruktorów i destruktorów

- Skompilować bez/ehsc

Błąd C2712 może również wystąpić, jeśli wywołanie metody zadeklarowanej przy użyciu [__event](../../cpp/event.md) — słowo kluczowe. Ponieważ zdarzenia mogą być używane w środowisku wielowątkowym, kompilator generuje kod, który uniemożliwia manipulowania obiektu bazowego event, a następnie umieszcza wygenerowany kod w SEH [try-finally — instrukcja](../../cpp/try-finally-statement.md). W związku z tym C2712 wystąpi błąd Jeśli wywołanie metody zdarzeń i przekazać wartość argumentu o typie ma destruktor. Jedno rozwiązanie w tym przypadku jest przekazanie argumentu jako stałe odwołanie.

C2712 może również wystąpić, jeśli kompilujesz z opcją **/CLR: pure** i Zadeklaruj statyczne tablicę wskaźników do funkcji w `__try` bloku. Statyczny element członkowski wymaga kompilator korzystać dynamiczna Inicjalizacja w obszarze **/CLR: pure**, co oznacza obsługi wyjątków C++. Jednak obsługa wyjątków języka C++ nie jest dozwolona w `__try` bloku.

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2712 i pokazuje, jak go naprawić.

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