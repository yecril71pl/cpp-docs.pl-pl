---
title: Błąd kompilatora C3913
ms.date: 11/04/2016
f1_keywords:
- C3913
helpviewer_keywords:
- C3913
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
ms.openlocfilehash: 3a38f7bffd56f025510e092ad37b5f810cb11a9b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776521"
---
# <a name="compiler-error-c3913"></a>Błąd kompilatora C3913

Domyślna właściwość musi być indeksowana

Domyślna właściwość został niepoprawnie zdefiniowany.

Aby uzyskać więcej informacji, zobacz [właściwość](../../extensions/property-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3913:

```
// C3913.cpp
// compile with: /clr /c
ref struct X {
   property int default {   // C3913
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```