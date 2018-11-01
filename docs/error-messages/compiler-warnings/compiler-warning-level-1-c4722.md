---
title: Kompilator ostrzeżenie (poziom 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 320061c2daf2be042afe45828af637638399beaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469475"
---
# <a name="compiler-warning-level-1-c4722"></a>Kompilator ostrzeżenie (poziom 1) C4722

'Funkcja': destruktor nigdy nie powraca, Potencjalny przeciek pamięci

Przepływ sterowania kończy się destruktora. Wątek lub całego programu spowoduje przerwanie działania i nie można zwolnić przydzielone zasoby.  Ponadto jeśli destruktor zostanie wywołana dla wykonywania operacji odwijania stosu podczas przetwarzania wyjątek, zachowanie plik wykonywalny jest niezdefiniowane.

Aby rozwiązać problem, Usuń wywołanie funkcji, który powoduje, że destruktor nie zwracać.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4722:

```
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```