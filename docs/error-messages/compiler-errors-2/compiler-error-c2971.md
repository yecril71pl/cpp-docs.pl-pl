---
title: Błąd kompilatora C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 09f3578bff5806fc32a3b5599dcfa8caa3696974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437301"
---
# <a name="compiler-error-c2971"></a>Błąd kompilatora C2971

"class": parametr szablonu "param": "arg": zmienna lokalna nie może służyć jako argument bez typu

Nie można użyć nazwy lub adresu zmiennej lokalnej, jak argument szablonu.

Poniższy przykład spowoduje wygenerowanie C2971:

```
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```