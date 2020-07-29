---
title: Błąd kompilatora C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: f723fcc0a3d9626f01f2059a3d9363801221bca0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216053"
---
# <a name="compiler-error-c2723"></a>Błąd kompilatora C2723

"Function": specyfikator "specyfikator" jest niedozwolony w definicji funkcji

Specyfikator nie może występować z definicją funkcji poza deklaracją klasy. **`virtual`** Specyfikator może być określony tylko w deklaracji funkcji składowej w deklaracji klasy.

Poniższy przykład generuje C2723 i pokazuje, jak to naprawić:

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
