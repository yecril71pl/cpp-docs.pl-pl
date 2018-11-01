---
title: Błąd kompilatora C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 00cb13d1999b00dfcaa5a2bc7bfb3b8eb16af5f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661880"
---
# <a name="compiler-error-c2533"></a>Błąd kompilatora C2533

'Identyfikator': konstruktorom niedozwolony typ zwracany

Konstruktor nie może posiadać typu zwracanego (nie jest jeszcze `void` zwracany typ).

Wspólne źródło wystąpienia tego błędu jest Brak średnika między końcem definicji klasy, a pierwszy implementacji konstruktora. Kompilator uznaje klasy definicję typ zwracany dla funkcji konstruktora, a następnie generuje C2533.

Poniższy przykład generuje C2533 i pokazuje, jak go naprawić:

```
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```