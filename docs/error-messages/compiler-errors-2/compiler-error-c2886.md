---
title: Błąd kompilatora C2886
ms.date: 11/04/2016
f1_keywords:
- C2886
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
ms.openlocfilehash: 3e445b52c2a0abbfca198c4cb0f4108dd5ba5ffb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233434"
---
# <a name="compiler-error-c2886"></a>Błąd kompilatora C2886

"Class:: identifier": symbol nie może być używany w deklaracji using składowej

**`using`** Deklaracja używa symbolu, takiego jak nazwa przestrzeni nazw. **`using`** Deklaracja służy do deklarowania elementów członkowskich klasy bazowej.

Poniższy przykład generuje C2886:

```cpp
// C2886.cpp
// compile with: /c
namespace Z {
    int i;
}

class B {
protected:
    int i;
};

class D : public B {
    // Error: Z is a namespace
    using Z::i;   // C2886

    // OK: B is a base class
    using B::i;
};
```
