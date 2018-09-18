---
title: Kompilator ostrzeżenie (poziom 1) C4722 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4722
dev_langs:
- C++
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f450120ff05c7e13888bf4b4ce4425405525b4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112502"
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