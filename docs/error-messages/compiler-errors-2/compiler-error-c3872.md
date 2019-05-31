---
title: Błąd kompilatora C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: bd056a63ab60cd5a2504c6a0bc19e388f71b068b
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450054"
---
# <a name="compiler-error-c3872"></a>Błąd kompilatora C3872

"char": ten znak nie jest dozwolony w identyfikatorze

Kompilator języka C++ następuje standard C ++ 11 na znaki są dozwolone w identyfikatorze. Tylko określone zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znak początkowy identyfikatora. Więcej informacji oraz listę dozwolonych znaków i znaki uniwersalne nazwy zakresów, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjna, podczas kompilowania C++sposób niezamierzony kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład spowoduje wygenerowanie C3872:

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```