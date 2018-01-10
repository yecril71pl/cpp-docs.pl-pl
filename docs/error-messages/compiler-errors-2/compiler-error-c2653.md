---
title: "C2653 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2653
dev_langs: C++
helpviewer_keywords: C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f18e3d6210c5d9b9aba4fdfaab296a01d32b6d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2653"></a>C2653 błąd kompilatora

> "*identyfikator*": nie jest nazwą klasy lub przestrzeni nazw

Składnia języka wymaga klasy, struktury, Unią lub tutaj nazwę przestrzeni nazw.

Ten błąd może wystąpić, gdy używasz nazwę, która nie została zadeklarowana jako klasy, struktury, Unii lub przestrzeni nazw przed operatorem zakresu. Aby rozwiązać ten problem, deklaruje nazwę, lub Dołącz nagłówek, który deklaruje nazwę, przed jego użyciem.

C2653 jest także możliwe, jeśli próby zdefiniowania *złożone przestrzeni nazw*, przestrzeni nazw, która zawiera jedną lub więcej nazw zagnieżdżone w zakresie przestrzeni nazw. Złożone przestrzeni nazw, definicje nie są dozwolone w języku C++ przed C ++ 17. Złożone przestrzenie nazw są obsługiwane począwszy od programu Visual Studio 2015 Update 3 po określeniu [/std:c ++ najnowsze](../../build/reference/std-specify-language-standard-version.md) — opcja kompilatora. Począwszy od programu Visual C++ 2017 wersji 15,5 cala kompilator obsługuje definicje złożone przestrzeń nazw podczas [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) określono opcję.

## <a name="examples"></a>Przykłady

W tym przykładzie generuje C2653, ponieważ nazwa zakresu jest używany, ale nie został zadeklarowany. Kompilator oczekuje klasy, struktury, Unii lub przestrzeni nazw nazwa przed operatora zakresu (:).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

W kod, który nie jest skompilowany dla języków C ++ 17 lub nowszym zagnieżdżonych obszarów nazw należy użyć deklaracji jawne przestrzeni nazw w każdym zagnieżdżonym poziomem:

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
