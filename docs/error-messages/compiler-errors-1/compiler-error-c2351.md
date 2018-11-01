---
title: Błąd kompilatora C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 2d93902ee0008a54da1b2ecf165e0a829362511f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665494"
---
# <a name="compiler-error-c2351"></a>Błąd kompilatora C2351

przestarzała Inicjalizacja składni konstruktora C++

Na liście inicjowania nowego stylu dla konstruktora jawnie nazwę każdego bezpośrednią klasą bazową, nawet jeśli jest on tylko podstawowej klasy.

Poniższy przykład spowoduje wygenerowanie C2351:

```
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```