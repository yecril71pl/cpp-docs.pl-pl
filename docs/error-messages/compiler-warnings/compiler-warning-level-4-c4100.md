---
title: Kompilator ostrzeżenie (poziom 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: ccb438cf7c80edb1403683ac4817617ffccc690d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447730"
---
# <a name="compiler-warning-level-4-c4100"></a>Kompilator ostrzeżenie (poziom 4) C4100

'Identyfikator': parametr formalny nieużywanych

Brak odwołania do parametru formalnego w treści funkcji. Nieużywany parametr jest ignorowany.

C4100 również mogą być wydawane, gdy kod wywołuje destruktora w parametrze typu pierwotnego.  Jest to ograniczenie Microsoft C++ kompilatora.

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