---
title: Błąd kompilatora C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 7efc94cc859bbee6db0ce973135c7501fd79ae1d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206942"
---
# <a name="compiler-error-c2562"></a>Błąd kompilatora C2562

"Identyfikator": funkcja "void" zwraca wartość

Funkcja jest zadeklarowana jako, **`void`** ale zwraca wartość.

Ten błąd może być spowodowany przez nieprawidłowy prototyp funkcji.

Ten błąd może zostać naprawiony w przypadku określenia typu zwracanego w deklaracji funkcji.

Poniższy przykład generuje C2562:

```cpp
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```
