---
title: Błąd kompilatora C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: f000287c5934a39d56342bce0f6c9ca2c69e2297
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212738"
---
# <a name="compiler-error-c2391"></a>Błąd kompilatora C2391

"Identyfikator": "Friend" nie może zostać użyty podczas definicji typu

**`friend`** Deklaracja zawiera kompletną deklarację klasy. **`friend`** Deklaracja może określać funkcję członkowską lub wyrafinowany specyfikator typu, ale nie pełną deklarację klasy.

Poniższy przykład generuje C2326:

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
