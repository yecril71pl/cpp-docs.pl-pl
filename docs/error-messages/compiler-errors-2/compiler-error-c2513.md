---
title: Błąd kompilatora C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 093a5856fdcfa6311fcef93214672b035c91b4fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746529"
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

Alternatywą jest usunięcie `typedef`, aby zdefiniować zmienną z listą inicjatora agregacji, ale nie jest to zalecane, ponieważ spowoduje to utworzenie zmiennej o takiej samej nazwie jak typ i ukrycie nazwy typu.
