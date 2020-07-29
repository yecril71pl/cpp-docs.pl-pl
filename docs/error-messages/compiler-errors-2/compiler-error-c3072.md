---
title: Błąd kompilatora C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: bcf2548fbe1182f7f6c4bd966ca6aa9ef9f10089
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212608"
---
# <a name="compiler-error-c3072"></a>Błąd kompilatora C3072

> nie można zastosować operatora "*operator-Name*" do wystąpienia klasy ref

Użyj operatora jednoargumentowego *operatora nazwy* , aby skonwertować wystąpienie klasy ref do typu dojścia

Typ CLR wymaga operatorów CLR, nienatywnych (lub standardowych).  Aby uzyskać więcej informacji, zobacz [śledzenie operatora odwołania](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3072.

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
