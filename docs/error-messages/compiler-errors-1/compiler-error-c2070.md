---
title: Błąd kompilatora C2070 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23daf8a8c25e132aa0717715a742352537010c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044083"
---
# <a name="compiler-error-c2070"></a>Błąd kompilatora C2070

"type": niedozwolony operand sizeof

[Sizeof](../../cpp/sizeof-operator.md) operator wymaga wyrażenie lub wpisz nazwy.

Poniższy przykład spowoduje wygenerowanie C2070:

```
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

Możliwe rozwiązanie:

```
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```