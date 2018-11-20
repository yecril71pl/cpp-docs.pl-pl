---
title: Operator dynamic_cast
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176968"
---
# <a name="dynamiccast-operator"></a>Operator dynamic_cast

Konwertuje argument `expression` do obiektu typu `type-id`.

## <a name="syntax"></a>Składnia

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Uwagi

`type-id` Musi być wskaźnikiem lub odwołanie do typu klasy uprzednio zdefiniowany albo "wskaźnika do typu void". Typ `expression` musi być wskaźnikiem, jeśli `type-id` jest wskaźnikiem lub l wartością, jeśli `type-id` to odwołanie.

Zobacz [static_cast](../cpp/static-cast-operator.md) objaśnienia dotyczące różnicę między rzutowaniami statycznych i dynamicznych oraz moment jest właściwy używać ich.

Istnieją dwie przełomowe zmiany w zachowaniu **dynamic_cast** w zarządzanym kodzie:

- **dynamic_cast** na wskaźnik do podstawowym typem wyliczenia spakowany zakończy się niepowodzeniem w czasie wykonywania, zwracając 0 zamiast przekonwertowanego wskaźnika.

- **dynamic_cast** nie będzie już zgłaszać wyjątku po `type-id` jest posługiwanie się nimi wskaźnik do typu wartości z rzutowania kończy się niepowodzeniem w czasie wykonywania.  Rzutowanie teraz zwróci wartość 0 wskaźnika, zamiast zgłaszać.

Jeśli `type-id` jest wskaźnikiem do jednoznacznej dostępny bezpośredniej lub pośredniej klasy bazowej `expression`, wskaźnikiem do podobiektów unikatowy typ `type-id` jest wynikiem. Na przykład:

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

Ten typ konwersja nazywa "rozszerzające", ponieważ powoduje przeniesienie wskaźnika w górę hierarchii klas z klasy pochodnej do klasy, która jest pochodną. Rozszerzające to niejawna konwersja.

Jeśli `type-id` jest void * środowiska wykonawczego dokonuje do określenia rzeczywistego typu `expression`. Wynik jest wskaźnikiem do kompletnego obiektu wskazywanego przez `expression`. Na przykład:

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

Jeśli `type-id` nie jest void *, aby zobaczyć, jeśli obiekt wskazywany przez jest wykonywane sprawdzenie czasu wykonywania `expression` można przekonwertować na typ wskazywanego przez `type-id`.

Jeśli typ `expression` jest klasą bazową typu `type-id`, aby sprawdzić, czy jest wykonywane sprawdzenie czasu wykonywania `expression` faktycznie wskazuje na obiekt kompletny typu `type-id`. Jeśli to PRAWDA, wynik jest wskaźnikiem do kompletnym obiektem typu `type-id`. Na przykład:

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

Ten typ konwersja nazywa "downcast", ponieważ powoduje przeniesienie wskaźnika w dół hierarchii klas, od danej klasy do klasy bazującej na tym obiekcie.

W przypadku wielokrotnego dziedziczenia możliwości niejednoznaczności zostały wprowadzone. Rozważmy hierarchię klas pokazaną na poniższym rysunku.

Na typy CLR **dynamic_cast** skutkuje pusta, jeśli konwersja może zostać wykonana niejawnie lub MSIL `isinst` instrukcji, która przeprowadza sprawdzanie dynamicznych i zwraca **nullptr** Jeśli Konwersja nie powiedzie się.

Następujące przykładowe używa **dynamic_cast** do ustalenia, czy klasa jest wystąpienie określonego typu:

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

![Klasy hierarchii, który pokazuje wielokrotne dziedziczenie](../cpp/media/vc39011.gif "klasy hierarchii, który pokazuje dziedziczenie wielokrotne") <br/>
Hierarchia klas, który pokazuje dziedziczenie wielokrotne

Wskaźnik do obiektu typu `D` może być bezpiecznie rzutowany `B` lub `C`. Jednak jeśli `D` jest rzutowany na wskaż `A` obiektu, którego wystąpienia `A` spowodowałoby? Spowoduje to błąd rzutowania niejednoznaczne. Aby obejść ten problem, można wykonać dwa rzutowania jednoznaczne. Na przykład:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   D* pd = new D;
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Mogą zostać wprowadzone dalsze niejasności, korzystając z wirtualnej klasy bazowej. Rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Klasa hierarchii, która zawiera wirtualne klasy bazowe](../cpp/media/vc39012.gif "klasy hierarchii, która zawiera wirtualne klasy bazowe") <br/>
Hierarchia klas, który pokazuje wirtualne klasy bazowe

W tej hierarchii `A` jest wirtualnej klasy bazowej. Biorąc pod uwagę wystąpienie klasy `E` i wskaźnik `A` podobiektu, **dynamic_cast** na wskaźnik do `B` zakończy się niepowodzeniem z powodu niejednoznaczności. Najpierw należy rzutować na pełną `E` obiektu, a następnie sposobu pracy użytkownika Utwórz kopię zapasową hierarchii jednoznacznie, aby dotrzeć do prawidłowego `B` obiektu.

Rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Klasa hierarchii, która zawiera zduplikowane klas bazowych](../cpp/media/vc39013.gif "klasy hierarchii, która zawiera zduplikowane klas bazowych") <br/>
Hierarchii klas, która zawiera zduplikowane klas bazowych

Danego obiektu typu `E` i wskaźnik `D` podobiektu przejść z `D` podobiektu się najdalej po lewej stronie `A` podobiektów, można wprowadzić trzy konwersje. Można wykonać **dynamic_cast** konwersja `D` wskaźnik do `E` wskaźnika, a następnie konwersji (albo **dynamic_cast** lub niejawną konwersję) z `E`do `B`, a na koniec niejawna konwersja z `B` do `A`. Na przykład:

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

**Dynamic_cast** operator może również służyć do wykonywania "rzutowania między". Korzystając z tej samej hierarchii klas, możliwe jest rzutowanie wskaźnika, na przykład z `B` podobiektu do `D` podobiektu, tak długo, jak obiekt kompletny jest typu `E`.

Biorąc pod uwagę krzyżowe rzutowania, jest faktycznie można zrobić konwersja ze wskaźnika do `D` na wskaźnik do skrajnej lewej `A` podobiektu w dwóch krokach. Można wykonać krzyżowych rzutowanie z elementu `D` do `B`, następnie niejawna konwersja z `B` do `A`. Na przykład:

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

Wartość wskaźnika o wartości null jest konwertowany na wartość pustego wskaźnika typu miejsca docelowego przez **dynamic_cast**.

Kiedy używasz `dynamic_cast < type-id > ( expression )`, jeśli `expression` nie może być bezpiecznie konwertowany na typ `type-id`, sprawdzanie w czasie wykonania powoduje, że cast nie powiedzie się. Na przykład:

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

Wartość nie powiodło się Rzutowanie na typ wskaźnika jest pustym wskaźnikiem. Nie powiodło się rzutowania do odwołania typu zgłasza [bad_cast, wyjątek](../cpp/bad-cast-exception.md).   Jeśli `expression` nie wskazują lub odwoływać się do prawidłowego obiektu, `__non_rtti_object` wyjątku.

Zobacz [typeid](../cpp/typeid-operator.md) objaśnienia dotyczące `__non_rtti_object` wyjątku.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wskaźnik klasy bazowej (Konstrukcja struct A), do obiektu (struktura C).  To, a także fakt, że funkcje wirtualne, polimorfizmu środowiska uruchomieniowego.

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