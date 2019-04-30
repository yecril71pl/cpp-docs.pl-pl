---
title: Błąd kompilatora C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: eb2a6935073c3b4a2b9eb3d9b099b372cfa34303
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385644"
---
# <a name="compiler-error-c3873"></a>Błąd kompilatora C3873

"char": ten znak nie jest dozwolona jako pierwszy znak identyfikatora

Kompilator języka C++ następuje standard C ++ 11 na znaki są dozwolone w identyfikatorze. Tylko określone zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znak początkowy identyfikatora. Więcej informacji oraz listę dozwolonych znaków i znaki uniwersalne nazwy zakresów, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjna, podczas kompilowania C++sposób niezamierzony kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład spowoduje wygenerowanie C3873:

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```