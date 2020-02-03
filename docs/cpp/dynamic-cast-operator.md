---
title: Operator dynamic_cast
description: Omówienie operatora dynamic_cast C++ języka.
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 0073aaa886bba33a0ec6c07fb89d6eee032765c8
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972221"
---
# <a name="dynamic_cast-operator"></a>Operator dynamic_cast

Konwertuje operand `expression` na obiekt typu `type-id`.

## <a name="syntax"></a>Składnia

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Uwagi

`type-id` musi być wskaźnikiem lub odwołaniem do wcześniej zdefiniowanego typu klasy lub "wskaźnikiem do wartości void". Typ `expression` musi być wskaźnikiem, jeśli `type-id` jest wskaźnikiem lub l-wartością, jeśli `type-id` jest odwołaniem.

Zobacz [static_cast](../cpp/static-cast-operator.md) , aby uzyskać wyjaśnienie różnic między konwersjami statycznymi a dynamicznymi, i kiedy jest on właściwy do użycia.

Istnieją dwie zmiany w zachowaniu **dynamic_cast** w kodzie zarządzanym:

- **dynamic_cast** wskaźnikiem do bazowego typu wyliczenia w ramce będzie kończyć się niepowodzeniem w czasie wykonywania, zwracając 0 zamiast przekonwertowanego wskaźnika.

- **dynamic_cast** nie będzie już zgłaszać wyjątku, gdy `type-id` jest wskaźnikiem wewnętrznym do typu wartości, a rzutowanie kończy się niepowodzeniem w czasie wykonywania.  Rzutowanie będzie teraz zwracało 0 wartość wskaźnika zamiast zgłaszania.

Jeśli `type-id` jest wskaźnikiem do nieniejednoznacznej dostępnej bezpośredniej lub pośredniej klasy podstawowej `expression`, wynik jest wskaźnikiem do unikatowego podobiektu typu `type-id`. Na przykład:

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

Ten typ konwersji nazywa się "przerzutem", ponieważ przenosi wskaźnik do hierarchii klas z klasy pochodnej do klasy, z której pochodzi. Rzutowanie jest niejawną konwersją.

Jeśli `type-id` jest void *, jest przeprowadzane sprawdzenie w czasie wykonywania w celu określenia rzeczywistego typu `expression`. Wynik jest wskaźnikiem do kompletnego obiektu wskazywanym przez `expression`. Na przykład:

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

Jeśli `type-id` nie jest typu void *, jest przeprowadzane sprawdzenie w czasie wykonywania, aby sprawdzić, czy obiekt wskazany przez `expression` można skonwertować na typ wskazywany przez `type-id`.

Jeśli typ `expression` jest klasą bazową typu `type-id`, zostanie wykonane sprawdzenie w czasie wykonywania, aby zobaczyć, czy `expression` rzeczywiście wskazuje na kompletny obiekt typu `type-id`. Jeśli wartość jest równa true, wynik jest wskaźnikiem do kompletnego obiektu typu `type-id`. Na przykład:

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

Ten typ konwersji nosi nazwę "downcast", ponieważ przesuwa wskaźnik w dół hierarchii klas, z danej klasy do klasy pochodnej.

W przypadku wielokrotnego dziedziczenia są wprowadzane możliwości niejednoznaczności. Rozważmy hierarchię klas pokazaną na poniższym rysunku.

W przypadku typów CLR **dynamic_cast** powoduje, że konwersja może zostać wykonana niejawnie lub instrukcji `isinst` MSIL, która wykonuje dynamiczne sprawdzanie i zwraca **nullptr** , jeśli konwersja nie powiedzie się.

Poniższy przykład używa **dynamic_cast** , aby określić, czy Klasa jest wystąpieniem określonego typu:

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![Hierarchia klas, która pokazuje wielokrotne dziedziczenie](../cpp/media/vc39011.gif "Hierarchia klas, która pokazuje wielokrotne dziedziczenie") <br/>
Hierarchia klas, która pokazuje wielokrotne dziedziczenie

Wskaźnik do obiektu typu `D` można bezpiecznie rzutować do `B` lub `C`. Jeśli jednak `D` jest rzutowane w celu wskazywania `A` obiektu, którego wystąpienie może być wynikiem `A`? Spowoduje to niejednoznaczny błąd rzutowania. Aby obejść ten problem, można wykonać dwa niejednoznaczne rzuty. Na przykład:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Dalsze niejasności można wprowadzać w przypadku używania wirtualnych klas bazowych. Rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Hierarchia klas, która pokazuje wirtualne klasy bazowe](../cpp/media/vc39012.gif "Hierarchia klas, która pokazuje wirtualne klasy bazowe") <br/>
Hierarchia klas, która pokazuje wirtualne klasy bazowe

W tej hierarchii `A` jest wirtualną klasą bazową. Jeśli wystąpienie klasy `E` i wskaźnik do podobiektu `A`, **dynamic_cast** do wskaźnika do `B` zakończy się niepowodzeniem z powodu niejednoznaczności. Najpierw należy wykonać rzutowanie do kompletnego obiektu `E`, a następnie wykonać kopię zapasową hierarchii w sposób niejednoznaczny, aby dotrzeć do poprawnego obiektu `B`.

Rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Hierarchia klas, która pokazuje zduplikowane klasy bazowe](../cpp/media/vc39013.gif "Hierarchia klas, która pokazuje zduplikowane klasy bazowe") <br/>
Hierarchia klas, która pokazuje zduplikowane klasy bazowe

W przypadku obiektu typu `E` i wskaźnika do `D` podobiektu, aby przejść z podobiektu `D` do `A` podobiektu z lewej strony, można wykonać trzy konwersje. Można wykonać konwersję **dynamic_cast** ze wskaźnika `D` do wskaźnika `E`, a następnie konwersji ( **dynamic_cast** lub niejawnej konwersji) od `E` do `B`, a na koniec niejawnej konwersji z `B` na `A`. Na przykład:

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

Operatora **dynamic_cast** można również użyć do przeprowadzenia "krzyżowego rzutowania". Korzystając z tej samej hierarchii klas, możliwe jest rzutowanie wskaźnika, na przykład, z podobiektu `B` do `D` podobiektu, o ile kompletny obiekt jest typu `E`.

Biorąc pod uwagę rzuty krzyżowe, można w rzeczywistości wykonać konwersję ze wskaźnika, aby `D` do wskaźnika do największej `A` podobiektu w zaledwie dwóch krokach. Można wykonać rzutowanie krzyżowe z `D` na `B`, a następnie niejawną konwersję z `B` do `A`. Na przykład:

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Wartość wskaźnika o wartości null jest konwertowana na wartość wskaźnika o wartości null typu docelowego przez **dynamic_cast**.

Jeśli używasz `dynamic_cast < type-id > ( expression )`, jeśli nie można bezpiecznie skonwertować `expression` do typu `type-id`, sprawdzenie w czasie wykonywania powoduje niepowodzenie rzutowania. Na przykład:

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

Wartość nieudanego rzutowania na typ wskaźnika jest wskaźnikiem o wartości null. Rzutowanie na typ referencyjny nie powiodło się, zgłasza [wyjątek bad_cast](../cpp/bad-cast-exception.md).   Jeśli `expression` nie wskazuje lub nie odwołuje się do prawidłowego obiektu, zostanie zgłoszony wyjątek `__non_rtti_object`.

Zobacz [typeid](../cpp/typeid-operator.md) , aby uzyskać wyjaśnienie wyjątku `__non_rtti_object`.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wskaźnik klasy bazowej (struct A) do obiektu (struktura C).  Jest to również funkcja wirtualna, która umożliwia korzystanie z polimorfizmu w czasie wykonywania.

Przykład wywołuje również funkcję niewirtualną w hierarchii.

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>Zobacz także

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)