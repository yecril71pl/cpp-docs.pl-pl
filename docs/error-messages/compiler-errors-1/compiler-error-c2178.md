---
title: Błąd kompilatora C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386008"
---
# <a name="compiler-error-c2178"></a>Błąd kompilatora C2178

"*identyfikator*"nie może być zadeklarowana z"*specyfikator*" Specyfikator

A `mutable` specyfikator został użyty w deklaracji, ale specyfikator jest niedozwolony w tym kontekście.

`mutable` Specyfikator mogą być stosowane tylko do nazwy elementów członkowskich danych klasy i nie można zastosować do nazwy zadeklarowane `const` lub `static`i nie można zastosować do odwoływać się do elementów członkowskich.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak może wystąpić C2178 i jak go naprawić.

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
