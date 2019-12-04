---
title: Błąd kompilatora C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: a8fe0802a7529551fce1c0b7242c867db52d8842
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756763"
---
# <a name="compiler-error-c3072"></a>Błąd kompilatora C3072

nie można zastosować operatora "operator" do wystąpienia klasy ref

Użyj jednoargumentowego operatora "`operator`", aby skonwertować wystąpienie klasy ref do typu dojścia

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
