---
title: Błąd kompilatora C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777418"
---
# <a name="compiler-error-c3900"></a>Błąd kompilatora C3900

"członek": niedozwolona w bieżącym zakresie

Właściwość bloków może zawierać deklaracje i funkcji tylko definicje funkcji śródwierszowej. Żadne składowe inne niż funkcje są dozwolone w blokach właściwości. Nie definicji typów, Operatorzy lub friend funkcje są dozwolone. Aby uzyskać więcej informacji, zobacz [właściwość](../../extensions/property-cpp-component-extensions.md).

Definicje zdarzeń może zawierać tylko metody dostępu i funkcje.

Poniższy przykład spowoduje wygenerowanie C3900:

```
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

Poniższy przykład spowoduje wygenerowanie C3900:

```
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```