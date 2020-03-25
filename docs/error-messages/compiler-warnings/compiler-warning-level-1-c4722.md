---
title: Ostrzeżenie kompilatora (poziom 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 3fee3296eba4476680f4948b4a1f7fdee03e8840
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175210"
---
# <a name="compiler-warning-level-1-c4722"></a>Ostrzeżenie kompilatora (poziom 1) C4722

"Function": destruktor nigdy nie zwraca, potencjalny przeciek pamięci

Przepływ sterowania kończy się w destruktorze. Wątek lub cały program zakończy pracę, a przydzieloną zasoby mogą nie zostać wydane.  Ponadto, jeśli destruktor zostanie wywołany w celu odwinięcia stosu podczas przetwarzania wyjątku, zachowanie pliku wykonywalnego jest niezdefiniowane.

Aby rozwiązać problem, Usuń wywołanie funkcji, które powoduje, że destruktor nie zwraca.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4722:

```cpp
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
