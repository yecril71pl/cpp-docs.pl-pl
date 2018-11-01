---
title: Błąd kompilatora C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: d82d3272563f7a5af5de399a2f7fff621500e612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490484"
---
# <a name="compiler-error-c3290"></a>Błąd kompilatora C3290

"type": właściwość prosta nie może mieć typu referencyjnego

Właściwość została zadeklarowana niepoprawnie. Zadeklaruj właściwość prosta, kompilator tworzy zmienną, która spowoduje zaktualizowanie właściwości, gdy nie jest możliwe śledzenie odwołania do zmiennej w klasie.

Zobacz [właściwość](../../windows/property-cpp-component-extensions.md) i [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md) Aby uzyskać więcej informacji.

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