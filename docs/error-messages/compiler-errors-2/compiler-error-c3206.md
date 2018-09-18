---
title: Błąd kompilatora C3206 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3206
dev_langs:
- C++
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa7775f0da26846851677aa267b91438ce84dbf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117962"
---
# <a name="compiler-error-c3206"></a>Błąd kompilatora C3206

'Funkcja': nieprawidłowy typ argumentu dla "param", po której brakuje listy argumentów typu na typ klasy "typename"

Funkcja szablonu jest zdefiniowany jako biorąc argument typu szablonu. Jednak został przekazany argument szablonu szablonu.

Poniższy przykład spowoduje wygenerowanie C3206:

```
// C3206.cpp
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S>();   // C3206
   // try the following line instead
   // f<S<int> >();
}
```

Możliwe rozwiązanie:

```
// C3206b.cpp
// compile with: /c
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S<int> >();
}
```

C3206 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3206c.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS>();   // C3206
}
```

Możliwe rozwiązanie:

```
// C3206d.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS<int> >();
}
```


Szablon klasy nie jest dozwolona jako argument typu szablonu. Poniższy przykład wywołuje C3206:

```
// C3206e.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T<int> t;
}

int main() {
   func<S>();   // C3206 S is not a type.
}
```

Możliwe rozwiązanie:

```
// C3206f.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T t;
}

int main() {
   func<S<int> >();
}
```

Jeśli konieczne jest parametru szablonu, następnie należy zabalit funkcja z klasą szablonu, który przyjmuje parametru szablonu:

```
// C3206g.cpp
template <class T>
struct S {};

template<template<class> class TT>
struct X {
   static void func() {
      TT<int> t1;
      TT<char> t2;
   }
};

int main() {
   X<S>::func();
}
```