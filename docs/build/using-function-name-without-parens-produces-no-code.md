---
title: Korzystanie z nazwy funkcji bez () nie tworzy kodu
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314601"
---
# <a name="using-function-name-without--produces-no-code"></a>Korzystanie z nazwy funkcji bez () nie tworzy kodu

Gdy nazwa funkcji zadeklarowana w programie jest używana bez nawiasów, kompilator nie tworzy kodu. Dzieje się tak niezależnie od tego, czy funkcja przyjmuje parametry, ponieważ kompilator oblicza adres funkcji; Jednak ze względu na to, że operator wywołania funkcji "()" nie istnieje, wywołanie nie zostało wykonane. Ten wynik jest podobny do następującego:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

W Visual C++, nawet przy użyciu poziomu ostrzeżeń 4 nie generuje danych wyjściowych. Nie wydano ostrzeżenia; nie jest tworzony żaden kod.

Przykładowy kod poniżej kompiluje (z ostrzeżeniem) i łączy się prawidłowo bez błędów, ale nie tworzy kodu w odwołaniu do `funcn( )`. Aby to działanie działało prawidłowo, Dodaj operator wywołania funkcji "()".

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>Zobacz też

[Optymalizacja kodu](optimizing-your-code.md)
