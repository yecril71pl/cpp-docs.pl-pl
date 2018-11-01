---
title: Kompilator ostrzeżenie (poziom 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: 03ea8328351a594e04988e3544686d8c5dc1144a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638766"
---
# <a name="compiler-warning-level-3-c4646"></a>Kompilator ostrzeżenie (poziom 3) C4646

Funkcja zadeklarowana ze __declspec(noreturn) ma typ zwracany niż void

Funkcja oznaczone [noreturn](../../cpp/noreturn.md) `__declspec` powinny mieć modyfikator [void](../../cpp/void-cpp.md) typ zwracany.

Poniższy przykład spowoduje wygenerowanie C4646:

```
// C4646.cpp
// compile with: /W3 /WX
int __declspec(noreturn) TestFunction()
{   // C4646  make return type void
}
```