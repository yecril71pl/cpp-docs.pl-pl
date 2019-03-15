---
title: Korzystanie z nazwy funkcji bez () nie tworzy kodu
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823895"
---
# <a name="using-function-name-without--produces-no-code"></a>Korzystanie z nazwy funkcji bez () nie tworzy kodu

Jeśli nazwy funkcji zadeklarowanych w programie jest używana bez nawiasów, kompilator nie generuje kodu. Dzieje się tak niezależnie od tego, czy funkcja przyjmuje parametry, ponieważ kompilator oblicza adresu funkcji; Jednak ponieważ operator wywołania funkcji (")" nie jest obecny, nie wykonano wywołanie. Ten wynik jest podobny do następującego:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

W programie Visual C++ nawet przy użyciu poziom ostrzeżeń 4 generuje żadne diagnostyczne dane wyjściowe. Nie ostrzeżenie; żaden kod jest generowany.

Poniższy przykładowy kod kompiluje (z ostrzeżeniem) i poprawnie łącza bez błędów, ale nie tworzy kodu reference do `funcn( )`. Aby to działało poprawnie Dodaj operator wywołania funkcji (")".

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

## <a name="see-also"></a>Zobacz także

[Optymalizacja kodu](optimizing-your-code.md)
