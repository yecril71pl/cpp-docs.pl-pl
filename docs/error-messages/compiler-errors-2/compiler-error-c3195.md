---
title: Błąd kompilatora C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760429"
---
# <a name="compiler-error-c3195"></a>Błąd kompilatora C3195

"operator": jest zarezerwowany i nie może być używany jako element członkowski klasy referencyjnej lub typu wartości. Operatory CLR lub WinRT muszą być zdefiniowane za pomocą słowa kluczowego "operator"

Kompilator wykrył definicję operatora przy użyciu rozszerzeń zarządzanych do C++ składni. Należy użyć C++ składni dla operatorów.

Poniższy przykład generuje C3195 i pokazuje, jak to naprawić:

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
