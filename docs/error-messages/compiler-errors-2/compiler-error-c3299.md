---
title: Błąd kompilatora C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 148433f0d959985eb5a874f588f8cbf9d377e8b7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735960"
---
# <a name="compiler-error-c3299"></a>Błąd kompilatora C3299

"member_function": nie można określić ograniczeń, są one dziedziczone z metody podstawowej

Podczas zastępowania ogólnej funkcji składowej nie można określać klauzul ograniczenia (powtarzające się ograniczenia wynikają z tego, że ograniczenia nie są dziedziczone).

Klauzule ograniczenia dotyczące funkcji ogólnej, która jest zastępowana, zostaną Odziedziczone.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnegoC++(/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3299.

```cpp
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```
