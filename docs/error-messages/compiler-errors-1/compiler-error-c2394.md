---
title: Błąd kompilatora C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: a18b09bcb5e6f4e743a8b1668cd0057b02a60a8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303700"
---
# <a name="compiler-error-c2394"></a>Błąd kompilatora C2394

"your_type::operator'op" ": CLR lub WinRToperator nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów: T ^', t ^ % ", t ^ &", gdzie T = "your_type"

Operator w Windows Runtime lub typ zarządzany nie miał co najmniej jeden parametr, którego typ jest taki sam jak typ wartości zwracanej operatora.

Poniższy przykład spowoduje wygenerowanie C2394:

```
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```