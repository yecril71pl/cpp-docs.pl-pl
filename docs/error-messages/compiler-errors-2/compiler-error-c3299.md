---
title: Błąd kompilatora C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 4ad48ea0bc09e098a41cb9aa969a08e9ead48f73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484841"
---
# <a name="compiler-error-c3299"></a>Błąd kompilatora C3299

"member_function": nie można określić ograniczeń, są one dziedziczone z metody podstawowej

Podczas zastępowania funkcja ogólnej składowej, nie można określić ograniczenia klauzule (powtarzające się ograniczenia oznacza, że ograniczenia nie są dziedziczone).

Klauzule ograniczenia na ogólnych funkcji, które są zastępowanie będą dziedziczone.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3299.

```
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