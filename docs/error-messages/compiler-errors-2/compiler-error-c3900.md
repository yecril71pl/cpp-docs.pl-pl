---
title: Błąd kompilatora C3900 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3900
dev_langs:
- C++
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfbec5086cd034b56795f47504c029e975aa36b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039676"
---
# <a name="compiler-error-c3900"></a>Błąd kompilatora C3900

"członek": niedozwolona w bieżącym zakresie

Właściwość bloków może zawierać deklaracje i funkcji tylko definicje funkcji śródwierszowej. Żadne składowe inne niż funkcje są dozwolone w blokach właściwości. Nie definicji typów, Operatorzy lub friend funkcje są dozwolone. Aby uzyskać więcej informacji, zobacz [właściwość](../../windows/property-cpp-component-extensions.md).

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