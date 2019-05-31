---
title: Błąd kompilatora C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: ca70af12ef3223c8c5950f0fa98b1c63a2dd3a4c
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450824"
---
# <a name="compiler-error-c3873"></a>Błąd kompilatora C3873

"char": ten znak nie jest dozwolona jako pierwszy znak identyfikatora

Kompilator języka C++ następuje standard C ++ 11 na znaki są dozwolone w identyfikatorze. Tylko określone zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znak początkowy identyfikatora. Więcej informacji oraz listę dozwolonych znaków i znaki uniwersalne nazwy zakresów, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjna, podczas kompilowania C++sposób niezamierzony kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład spowoduje wygenerowanie C3873:

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```