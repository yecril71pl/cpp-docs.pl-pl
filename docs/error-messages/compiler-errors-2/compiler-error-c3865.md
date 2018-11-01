---
title: Błąd kompilatora C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 846657d3598e268d78ff3c39f2bfc901756ad370
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642788"
---
# <a name="compiler-error-c3865"></a>Błąd kompilatora C3865

"calling_convention": należy używać tylko w natywnych funkcjach składowych

Konwencja wywoływania był używany w funkcji, która została każda funkcja globalna lub funkcji składowej zarządzanej. Konwencja wywoływania należy używać tylko w funkcji natywnej (niezarządzane) elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [Konwencje wywoływania](../../cpp/calling-conventions.md).

Poniższy przykład spowoduje wygenerowanie C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```