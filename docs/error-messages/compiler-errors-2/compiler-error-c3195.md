---
title: Błąd kompilatora C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: 4a54a9c629a1abaa4f1c5d15d06448e82cf25561
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538857"
---
# <a name="compiler-error-c3195"></a>Błąd kompilatora C3195

'operator': jest zarezerwowany i nie można użyć jako elementem członkowskim klasy lub wartości typu ref. Operatory środowiska CLR lub WinRT musi być zdefiniowana za pomocą słowa kluczowego 'operator'

Kompilator wykrył definicję operatora, przy użyciu zarządzanych rozszerzeń dla składni języka C++. Dla operatorów, należy użyć składni języka C++.

Poniższy przykład generuje C3195 i pokazuje, jak go naprawić:

```
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```