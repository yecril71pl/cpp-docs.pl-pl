---
title: Błąd kompilatora C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: 5cadb8165b5b63b2f7ac2d4cc31e2623b0f6bce9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243014"
---
# <a name="compiler-error-c3872"></a>Błąd kompilatora C3872

"char": ten znak nie jest dozwolony w identyfikatorze

Kompilator języka C++ następuje standard C ++ 11 na znaki są dozwolone w identyfikatorze. Tylko określone zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znak początkowy identyfikatora. Więcej informacji oraz listę dozwolonych znaków i znaki uniwersalne nazwy zakresów, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjna, podczas kompilowania C++sposób niezamierzony kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład spowoduje wygenerowanie C3872:

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```