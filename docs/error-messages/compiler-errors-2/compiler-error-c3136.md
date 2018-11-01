---
title: Błąd kompilatora C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501096"
---
# <a name="compiler-error-c3136"></a>Błąd kompilatora C3136

"interface": interfejs COM może dziedziczyć tylko z innego interfejsu COM, "interface" nie jest interfejsem COM

Interfejs, do której zastosowano [atrybut interfejsu](../../windows/attributes/interface-attributes.md) dziedziczy interfejs, który nie jest interfejsem COM. Interfejs COM, ale ostatecznie dziedziczy `IUnknown`. Dowolny interfejs poprzedzony przez atrybut interfejsu jest interfejsem COM.

Poniższy przykład generuje C3136:

```
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```