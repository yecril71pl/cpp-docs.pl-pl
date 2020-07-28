---
title: Błąd kompilatora C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d6014aa44dd1c2a5f1b0418a7171b239a754ec33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220200"
---
# <a name="compiler-error-c2884"></a>Błąd kompilatora C2884

"name": wprowadzono za pomocą deklaracji using powoduje konflikt z funkcją lokalną "Function"

Podjęto próbę zdefiniowania funkcji więcej niż jeden raz. Pierwsza definicja jest definicją lokalną. Sekunda pochodzi z przestrzeni nazw z **`using`** deklaracją.

Poniższy przykład generuje C2884:

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
