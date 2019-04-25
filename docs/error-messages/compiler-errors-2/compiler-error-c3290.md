---
title: Compiler Error C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: f2a346354d8da7d78c5517b01b4438bfb8af50ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222710"
---
# <a name="compiler-error-c3290"></a>Compiler Error C3290

"type": właściwość prosta nie może mieć typu referencyjnego

Właściwość została zadeklarowana niepoprawnie. Zadeklaruj właściwość prosta, kompilator tworzy zmienną, która spowoduje zaktualizowanie właściwości, gdy nie jest możliwe śledzenie odwołania do zmiennej w klasie.

Zobacz [właściwość](../../extensions/property-cpp-component-extensions.md) i [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3290.

```
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```