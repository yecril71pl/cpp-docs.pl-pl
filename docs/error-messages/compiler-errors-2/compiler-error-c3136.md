---
title: Błąd kompilatora C3136 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082a89b69092a8320f6bb4b930d01a7fd2de10c8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788386"
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