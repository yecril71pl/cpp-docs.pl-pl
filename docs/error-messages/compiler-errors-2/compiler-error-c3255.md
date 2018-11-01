---
title: Błąd kompilatora C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: a5b483f3aaa82e543d561cb7c550495069a19f7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519941"
---
# <a name="compiler-error-c3255"></a>Błąd kompilatora C3255

"wartość typu": nie można dynamicznie przydzielić tego obiektu typu wartościowego na natywnej stercie

Jedno wystąpienie typu wartości (zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md)) zawierające zarządzanych członków można tworzyć na stosie, ale nie na stosie.

Poniższy przykład spowoduje wygenerowanie C3255:

```
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
