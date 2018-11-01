---
title: Błąd kompilatora C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435312"
---
# <a name="compiler-error-c2562"></a>Błąd kompilatora C2562

'Identyfikator': funkcja "void" zwraca wartość

Funkcja jest zadeklarowana jako `void` , ale zwraca wartość.

Ten błąd może być spowodowany przez prototypu Niepoprawna funkcja.

Ten błąd może być ustalony, jeśli określony typ zwracany w deklaracji funkcji.

Poniższy przykład spowoduje wygenerowanie C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```