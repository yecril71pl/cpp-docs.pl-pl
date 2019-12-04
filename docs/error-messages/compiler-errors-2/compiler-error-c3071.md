---
title: Błąd kompilatora C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 26a95b18970aef450c6fdf718910aa3f816fd778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759415"
---
# <a name="compiler-error-c3071"></a>Błąd kompilatora C3071

operator "operator" może być stosowany tylko do wystąpienia klasy ref lub typu wartościowego

Nie można użyć operatora CLR w typie natywnym. Operatora można używać w klasie ref lub ref struct (typu wartości), ale nie typu natywnego, takiego jak int czy alias dla typu natywnego, takiego jak system:: Int32. Te typy nie mogą być opakowane z C++ kodu w sposób, który odwołuje się do zmiennej macierzystej, dlatego nie można użyć operatora.

Aby uzyskać więcej informacji, zobacz [śledzenie operatora odwołania](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3071.

```cpp
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```
