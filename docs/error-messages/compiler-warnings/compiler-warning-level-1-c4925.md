---
title: Kompilator ostrzeżenie (poziom 1) C4925
ms.date: 11/04/2016
f1_keywords:
- C4925
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
ms.openlocfilehash: cb7b416fe15380dc914bd57152e8a0ce3618ee85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393509"
---
# <a name="compiler-warning-level-1-c4925"></a>Kompilator ostrzeżenie (poziom 1) C4925

"method": metoda interfejsu dispinterface nie może być wywoływana ze skryptu

Języki skryptów nie można utworzyć VT_BYREF parametru "in", można tylko utworzyć VT_BYREF parametrów "out".

Innym sposobem rozwiązania tego ostrzeżenia jest nie parametrze (w definicję i implementację) typ wskaźnika.

Poniższy przykład spowoduje wygenerowanie C4925:

```
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```