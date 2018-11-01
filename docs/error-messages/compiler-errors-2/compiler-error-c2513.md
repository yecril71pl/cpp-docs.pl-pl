---
title: Błąd kompilatora C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 13840246a5dc6a1c1bdbcb55dc47f212ee353d81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561206"
---
# <a name="compiler-error-c2513"></a>Błąd kompilatora C2513

"type": Brak deklaracji zmiennej przed "="

Specyfikator typu pojawia się w deklaracji z nie zmiennej identyfikatora.

Poniższy przykład spowoduje wygenerowanie C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Ten błąd może być też wygenerowany w wyniku pracy zgodność kompilatora Visual Studio .NET 2003: inicjowanie typedef nie są już dozwolone. Inicjowanie typedef nie jest dozwolona przez standardowe i generuje błąd kompilatora.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternatywą jest nieusuwanie `typedef` do definiujemy zmienną z listy inicjatorów agregacji, ale nie jest zalecane, ponieważ spowoduje to utworzenie zmiennej o nazwie identycznej z nazwą typu i ukryć nazwę typu.