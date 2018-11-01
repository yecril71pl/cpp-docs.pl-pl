---
title: Błąd kompilatora C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: f7327b7d2b0cc9fa4b617a9a6033116c43db6258
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528678"
---
# <a name="compiler-error-c2990"></a>Błąd kompilatora C2990

"class": typ klasy korporacyjnej jako już został zadeklarowany jako typ klasy

Inne niż ogólne lub klasą szablonu redefiniuje generyczny lub szablonu klasy. Sprawdź pliki nagłówkowe dla konfliktów.

Poniższy przykład spowoduje wygenerowanie C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 może również wystąpić z powodu istotnej zmiany w kompilatorze języka Visual C++ dla Visual C++ 2005; Kompilator teraz wymaga wielu deklaracji dla tego samego typu identyczne w odniesieniu do specyfikacji szablonu.

Poniższy przykład spowoduje wygenerowanie C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```