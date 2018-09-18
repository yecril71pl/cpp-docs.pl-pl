---
title: Błąd kompilatora C3854 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3854
dev_langs:
- C++
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d94d2462662fd5f99e80ba205b8e2df41d7c716b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099554"
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