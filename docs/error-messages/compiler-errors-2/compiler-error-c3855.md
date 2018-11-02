---
title: Błąd kompilatora C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: 12ee1c6aa5f414a9cf3084831c956514593102c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478133"
---
# <a name="compiler-error-c3855"></a>Błąd kompilatora C3855

"class": parametr typu "param" jest niezgodny z deklaracją

Kompilator odnaleźć szablonu nontype lub parametrów ogólnych o różnych nazwach. Taka sytuacja może wystąpić, gdy parametr szablonu określonego w definicji specjalizacja szablonu jest niezgodna z jego deklaracji.

Poniższy przykład spowoduje wygenerowanie C3855:

```
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

Możliwe rozwiązanie:

```
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

C3855 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

Możliwe rozwiązanie:

```
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```