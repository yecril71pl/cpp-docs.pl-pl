---
title: Kompilator ostrzeżenie (poziom 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455214"
---
# <a name="compiler-warning-level-1-c4286"></a>Kompilator ostrzeżenie (poziom 1) C4286

'Typ1': zostanie przechwycony przez klasę bazową ('Typ2') w wierszu o numerze

Typ określony wyjątek jest obsługiwany przez poprzedniej procedury obsługi. Typ drugiego catch pochodzi z typu pierwszego. Wyjątki dla klasy bazowej, przechwytywać wyjątki dla klasy pochodnej.

## <a name="example"></a>Przykład

```
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```