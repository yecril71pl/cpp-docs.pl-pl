---
title: Błąd kompilatora C2533 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 528b78e71713725907a9f0e2bd06cec1a8c62e67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045409"
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