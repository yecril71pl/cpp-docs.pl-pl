---
title: Błąd kompilatora C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: ab1f83e2075128441cbffd2d939e3b99b45be4c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596435"
---
# <a name="compiler-error-c2247"></a>Błąd kompilatora C2247

'Identyfikator' nie jest dostępna, ponieważ "class" użyto "specyfikatora" dziedziczy po "class"

`identifier` jest dziedziczona z klasy zadeklarowane za pomocą dostępu do prywatnych lub chronionych.

Poniższy przykład spowoduje wygenerowanie C2247:

```
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: dostęp do kontrolki z chronionych elementów członkowskich. Chroniony element członkowski (n) jest możliwy tylko za pośrednictwem funkcji składowej klasy (B), która dziedziczy z klasy (A), w której (n) jest członkiem.

Kod, który jest prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET, Visual c++ należy zadeklarować element członkowski może być zaprzyjaźniona z typu. Można również użyć publiczne dziedziczenie.

```
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

C2247 mogą być też generowane w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: podstawowy prywatny klasy teraz niedostępny. Jest prywatny klasą bazową do typu klasy (A) nie (B) powinny być dostępne do typu (C), który używa B jako klasę bazową.

Kod, który jest prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET, Visual c++ użyj operatora zakresu.

```
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```