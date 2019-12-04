---
title: Błąd kompilatora C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: e30ed7016ca3a4d4948a08c5c09268e52c9a407d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761676"
---
# <a name="compiler-error-c3181"></a>Błąd kompilatora C3181

"Type": nieprawidłowy operand dla operatora

Do operatora [typeid](../../extensions/typeid-cpp-component-extensions.md) przekazano nieprawidłowy parametr. Parametr musi być typem zarządzanym.

Należy zauważyć, że kompilator używa aliasów dla typów natywnych, które są mapowane na typy w środowisku uruchomieniowym języka wspólnego.

Poniższy przykład generuje C3181:

```cpp
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
