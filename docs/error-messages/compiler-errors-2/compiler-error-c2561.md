---
title: Błąd kompilatora C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: b4a14be9cd32c752e2ab889417494e80b935e31b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755567"
---
# <a name="compiler-error-c2561"></a>Błąd kompilatora C2561

"Identyfikator": funkcja musi zwracać wartość

Funkcja została zadeklarowana jako zwracająca wartość, ale definicja funkcji nie zawiera instrukcji `return`.

Ten błąd może być spowodowany przez nieprawidłowy prototyp funkcji:

1. Jeśli funkcja nie zwraca wartości, zadeklaruj funkcję z typem zwracanym [void](../../cpp/void-cpp.md).

1. Sprawdź, czy wszystkie możliwe gałęzie funkcji zwracają wartość typu zadeklarowanego w prototypie.

1. C++funkcje zawierające wbudowane procedury asemblera, które przechowują wartość zwracaną w rejestrze `AX` mogą potrzebować instrukcji return. Skopiuj wartość w `AX` do zmiennej tymczasowej i zwróć tę zmienną z funkcji.

Poniższy przykład generuje C2561:

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
