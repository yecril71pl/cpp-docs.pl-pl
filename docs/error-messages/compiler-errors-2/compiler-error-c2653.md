---
title: Błąd kompilatora C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: d4a3a8a74483317b87e16458f44016f0aeca1379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471152"
---
# <a name="compiler-error-c2653"></a>Błąd kompilatora C2653

> "*identyfikator*": nie jest klasą lub przestrzenią nazw

Składnia języka wymaga klasy, struktury, Unii lub nazwa przestrzeni nazw w tym miejscu.

Ten błąd może wystąpić, gdy używasz nazwę, która nie została zadeklarowana jako klasy, struktury, Unii lub przestrzeni nazw przed operatorem zakresu. Aby rozwiązać ten problem, należy zadeklarować nazwę lub zawierać nagłówek, który deklaruje nazwę, zanim zostaną one użyte.

C2653 jest również możliwe, jeśli zostanie podjęta próba zdefiniować *złożone przestrzeni nazw*, przestrzeń nazw, który zawiera jedną lub więcej nazw zagnieżdżony zakres przestrzeni nazw. Złożone przestrzeni nazw, których definicje nie są dozwolone w języku C++ przed C ++ 17. Złożone przestrzenie nazw są obsługiwane, począwszy od programu Visual Studio 2015 Update 3 po określeniu [/STD: c ++ najnowsze](../../build/reference/std-specify-language-standard-version.md) — opcja kompilatora. Począwszy od programu Visual C++ 2017 w wersji 15.5 definicji przestrzeni nazw złożonego obsługiwanych przez kompilator podczas [/STD: c ++ 17](../../build/reference/std-specify-language-standard-version.md) określono opcję.

## <a name="examples"></a>Przykłady

Ten przykład generuje C2653, ponieważ nazwa zakresu jest używany, ale nie został zadeklarowany. Kompilator oczekuje, że klasy, struktury, Unii lub nazwa przestrzeni nazw przed operatora zakresu (:).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

W kodzie, który nie jest kompilowany dla języka C ++ 17 lub nowszym zagnieżdżone przestrzenie nazw, należy użyć deklaracji jawną przestrzeń nazw na każdym poziomie zagnieżdżania:

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
