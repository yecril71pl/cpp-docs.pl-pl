---
title: Błąd kompilatora C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 3b48e2c65003537102864fdafe7db70b06ade029
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265532"
---
# <a name="compiler-error-c3854"></a>Błąd kompilatora C3854

Wyrażenie po lewej stronie "=" daje w wyniku funkcji. Nie można przypisać do funkcji (funkcja nie jest wartością l)

Nie można ponownie zainicjować odwołanie. Wyłuskanie odwołanie do funkcji daje funkcji, która r-wartości, do którego nie można przypisać. W związku z tym nie można przypisać za pomocą odwołanie do funkcji.

Poniższy przykład spowoduje wygenerowanie C3854:

```
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```