---
title: Błąd kompilatora C3872 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec6450dca0faa86f3cf27452eff6df9851742d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018837"
---
# <a name="compiler-error-c3872"></a>Błąd kompilatora C3872

"char": ten znak nie jest dozwolony w identyfikatorze

Kompilator języka C++ następuje standard C ++ 11 na znaki są dozwolone w identyfikatorze. Tylko określone zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znak początkowy identyfikatora. Więcej informacji oraz listę dozwolonych znaków i znaki uniwersalne nazwy zakresów, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjny gdy kompilacja C + +/ kodu interfejsu wiersza polecenia. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład spowoduje wygenerowanie C3872:

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```