---
title: Kompilator ostrzeżenie (poziom 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 287465e9a3f5681f459f0823a4409b0906309a55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280468"
---
# <a name="compiler-warning-level-1-c4096"></a>Kompilator ostrzeżenie (poziom 1) C4096

"": interfejs nie jest interfejsem COM; nie będzie emitowany do IDL

Definicja interfejsu zamierzony może mieć jako interfejs modelu COM nie został zdefiniowany jako interfejs COM i w związku z tym nie będzie emitowany do pliku IDL.

Zobacz [atrybuty interfejsu](../../windows/attributes/interface-attributes.md) atrybuty listy, które wskazują interfejs jest interfejsem COM.

Poniższy przykład spowoduje wygenerowanie C4096:

```
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```