---
title: Błąd kompilatora C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: 1d08c53aad50d2cbc10c8c0e398fe3a18de3849d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606495"
---
# <a name="compiler-error-c3360"></a>Błąd kompilatora C3360

"string": nie można utworzyć nazwy

Wartość, która została przekazana do [uuid](../../windows/uuid-cpp-attributes.md) atrybut nie jest prawidłowa.

Poniższy przykład spowoduje wygenerowanie C3360:

```
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```