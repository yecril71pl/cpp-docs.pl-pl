---
title: Compiler Error C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 314b75a9d0ab8cde2886a7466fa0f95b5bbdd8f1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778055"
---
# <a name="compiler-error-c3299"></a>Compiler Error C3299

"member_function": nie można określić ograniczeń, są one dziedziczone z metody podstawowej

Podczas zastępowania funkcja ogólnej składowej, nie można określić ograniczenia klauzule (powtarzające się ograniczenia oznacza, że ograniczenia nie są dziedziczone).

Klauzule ograniczenia na ogólnych funkcji, które są zastępowanie będą dziedziczone.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

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