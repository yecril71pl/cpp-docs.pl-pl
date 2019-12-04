---
title: Błąd kompilatora C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d0e283c7cd6116655a56f8df67ab4eecf9923b68
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760944"
---
# <a name="compiler-error-c2884"></a>Błąd kompilatora C2884

"name": wprowadzono za pomocą deklaracji using powoduje konflikt z funkcją lokalną "Function"

Podjęto próbę zdefiniowania funkcji więcej niż jeden raz. Pierwsza definicja jest definicją lokalną. Sekunda pochodzi z przestrzeni nazw z deklaracją `using`.

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
