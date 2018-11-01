---
title: Błąd kompilatora C2617
ms.date: 11/04/2016
f1_keywords:
- C2617
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
ms.openlocfilehash: 21add86e37d32525b69a02e848444919fe2a79f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442812"
---
# <a name="compiler-error-c2617"></a>Błąd kompilatora C2617

'Funkcja': niespójna instrukcja return

Określona funkcja nie ma zadeklarowany typ zwracany i poprzedniej zwracana wartość nie zostały dostarczone przez instrukcję.

Poniższy przykład spowoduje wygenerowanie C2617:

```
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

Możliwe rozwiązanie:

```
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```