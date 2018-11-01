---
title: Kompilator ostrzeżenie (poziom 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 84a0b27203cd43e8a8992c4ba599f1400c6909ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634866"
---
# <a name="compiler-warning-level-4-c4100"></a>Kompilator ostrzeżenie (poziom 4) C4100

'Identyfikator': parametr formalny nieużywanych

Brak odwołania do parametru formalnego w treści funkcji. Nieużywany parametr jest ignorowany.

C4100 również mogą być wydawane, gdy kod wywołuje destruktora w parametrze typu pierwotnego.  Jest to ograniczenie kompilatora Visual C++.

Poniższy przykład generuje C4100:

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```