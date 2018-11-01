---
title: Błąd kompilatora C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599844"
---
# <a name="compiler-error-c2395"></a>Błąd kompilatora C2395

"your_type::operator'op": operator CLR lub WinRT nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów: t ", t %", t & ", t ^', t ^ %", t ^ & ", gdzie T ="your_type"

Operator w Windows Runtime lub typ zarządzany nie miał co najmniej jeden parametr, którego typ jest taki sam jak typ wartości zwracanej operatora.

Poniższy przykład generuje C2395 i pokazuje, jak go naprawić:

```
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```