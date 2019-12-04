---
title: Błąd kompilatora C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749103"
---
# <a name="compiler-error-c3900"></a>Błąd kompilatora C3900

"member": niedozwolone w bieżącym zakresie

Bloki właściwości mogą zawierać deklaracje funkcji i tylko wbudowane definicje funkcji. Elementy członkowskie inne niż funkcje są dozwolone w blokach właściwości. Nie można używać typów typedef, operatorów ani zaprzyjaźnionych funkcji. Aby uzyskać więcej informacji, zobacz [Właściwość](../../extensions/property-cpp-component-extensions.md).

Definicje zdarzeń mogą zawierać tylko metody dostępu i funkcje.

Poniższy przykład generuje C3900:

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

Poniższy przykład generuje C3900:

```cpp
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
