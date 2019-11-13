---
title: Ostrzeżenie kompilatora (poziom 1) C4925
ms.date: 11/04/2016
f1_keywords:
- C4925
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
ms.openlocfilehash: 88eb09bdde1fa8dc50fa601cf7ae200d2851ac03
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052291"
---
# <a name="compiler-warning-level-1-c4925"></a>Ostrzeżenie kompilatora (poziom 1) C4925

"Method": nie można wywołać metody dispinterface z poziomu skryptu

W językach skryptów nie można utworzyć VT_BYREF parametru "in". można utworzyć tylko parametry VT_BYREF out.

Innym sposobem na rozwiązanie tego ostrzeżenia jest to, że parametr (w definicji i implementacji) nie jest typem wskaźnika.

Poniższy przykład generuje C4925:

```cpp
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