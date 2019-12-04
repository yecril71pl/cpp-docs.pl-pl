---
title: Błąd kompilatora C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737195"
---
# <a name="compiler-error-c2178"></a>Błąd kompilatora C2178

nie można zadeklarować*identyfikatora "identifier*" ze specyfikatorem "*specyfikatorer*"

W deklaracji użyto specyfikatora `mutable`, ale specyfikator jest niedozwolony w tym kontekście.

Specyfikator `mutable` może być stosowany tylko do nazw składowych danych klasy i nie można go stosować do nazw zadeklarowanych `const` lub `static`i nie można go stosować do elementów członkowskich odwołania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak C2178 może wystąpić i jak rozwiązać ten problem.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
