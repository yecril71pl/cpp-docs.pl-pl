---
title: Błąd kompilatora C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609758"
---
# <a name="compiler-error-c2975"></a>Błąd kompilatora C2975

> "*argument*": nieprawidłowy argument szablonu dla "*typu*", oczekiwano stałego wyrażenia czasu kompilacji

Argument szablonu jest niezgodna z deklaracją szablonu; wyrażenie stałe powinny być wyświetlane w nawiasach kątowych. Zmienne nie są dozwolone jako rzeczywistych argumentów szablonu. Sprawdź definicję szablonu, aby znaleźć poprawne typy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2975 oraz pokazuje poprawne użycie:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 występuje także w przypadku używania &#95; &#95;wiersza&#95; &#95; jako Stała kompilacji za pomocą [/zi](../../build/reference/z7-zi-zi-debug-information-format.md). Jedno rozwiązanie może polegać na kompilacji z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) zamiast **/zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```