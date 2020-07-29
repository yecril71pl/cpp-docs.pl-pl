---
title: Błąd kompilatora C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 96f2ccc29eed5c1fa4e29f69d18ae6503417f211
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212725"
---
# <a name="compiler-error-c2513"></a>Błąd kompilatora C2513

"Type": Brak deklaracji zmiennej przed "="

Specyfikator typu pojawia się w deklaracji bez identyfikatora zmiennej.

Poniższy przykład generuje C2513:

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Ten błąd może być również wygenerowany jako wynik zgodności kompilatora wykonane dla programu Visual Studio .NET 2003: inicjalizacja typedef nie jest już dozwolona. Inicjalizacja elementu typedef nie jest dozwolona przez Standard i teraz generuje błąd kompilatora.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternatywą byłoby usunięcie **`typedef`** , aby zdefiniować zmienną z listą inicjatora agregacji, ale nie jest to zalecane, ponieważ spowoduje to utworzenie zmiennej o takiej samej nazwie jak typ i ukrycie nazwy typu.
