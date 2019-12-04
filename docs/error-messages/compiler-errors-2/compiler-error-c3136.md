---
title: Błąd kompilatora C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757387"
---
# <a name="compiler-error-c3136"></a>Błąd kompilatora C3136

"Interface": interfejs COM może dziedziczyć tylko po innym interfejsie COM, interfejs nie jest interfejsem COM

Interfejs, do którego zastosowano [atrybut interfejsu](../../windows/attributes/interface-attributes.md) , dziedziczy z interfejsu, który nie jest interfejsem com. Interfejs COM ostatecznie dziedziczy po `IUnknown`. Każdy interfejs poprzedzony atrybutem interfejsu jest interfejsem COM.

Poniższy przykład generuje C3136:

```cpp
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
