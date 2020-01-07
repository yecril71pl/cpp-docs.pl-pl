---
title: using — Deklaracja
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: a158094141307acb507d5f3e873c600e89135ad7
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301278"
---
# <a name="using-declaration"></a>using — Deklaracja

Deklaracja **using** wprowadza nazwę w regionie deklaratywnym, w którym występuje deklaracja using.

## <a name="syntax"></a>Składnia

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>Parametry

*zagnieżdżony specyfikator Name* Sekwencja nazw, klas lub nazw wyliczenia oraz operatory rozpoznawania zakresu (::), zakończone przez operator rozpoznawania zakresu. Aby wprowadzić nazwę z globalnej przestrzeni nazw, można użyć operatora rozpoznawania pojedynczego zakresu. Słowo kluczowe **TypeName** jest opcjonalne i może służyć do rozpoznawania nazw zależnych w przypadku wprowadzenia ich do szablonu klasy z klasy bazowej.

*niekwalifikowana-ID* Niekwalifikowane wyrażenie identyfikatora, które może być identyfikatorem, nazwą operatora przeciążonego, zdefiniowanym przez użytkownika operatorem literału lub nazwą funkcji konwersji, nazwą destruktora klasy lub nazwą szablonu i listą argumentów.

*deklarator — lista* Rozdzielana przecinkami lista wartości typu [**TypeName**] *zagnieżdżonej nazwy specyfikatora* *deklaratory,* która jest zastosowana opcjonalnie przez wielokropek.

## <a name="remarks"></a>Uwagi

Deklaracja using wprowadza niekwalifikowaną nazwę jako synonim dla jednostki zadeklarowanej w innym miejscu. Umożliwia ona użycie pojedynczej nazwy z określonej przestrzeni nazw bez jawnej kwalifikacji w regionie deklaracji, w którym występuje. Jest to w przeciwieństwie do [dyrektywy using](../cpp/namespaces-cpp.md#using_directives), która umożliwia używanie *wszystkich* nazw w przestrzeni nazw bez kwalifikacji. Słowo kluczowe **using** jest również używane dla [aliasów typów](../cpp/aliases-and-typedefs-cpp.md).

## <a name="example"></a>Przykład

Deklaracja using może być używana w definicji klasy.

```cpp
// using_declaration1.cpp
#include <stdio.h>
class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class D : B {
public:
   using B::f;    // B::f(char) is now visible as D::f(char)
   using B::g;    // B::g(char) is now visible as D::g(char)
   void f(int) {
      printf_s("In D::f()\n");
      f('c');     // Invokes B::f(char) instead of recursing
   }

   void g(int) {
      printf_s("In D::g()\n");
      g('c');     // Invokes B::g(char) instead of recursing
   }
};

int main() {
   D myD;
   myD.f(1);
   myD.g('a');
}
```

```Output
In D::f()
In B::f()
In B::g()
```

## <a name="example"></a>Przykład

Gdy jest używany do deklarowania elementu członkowskiego, deklaracja using musi odwoływać się do elementu członkowskiego klasy bazowej.

```cpp
// using_declaration2.cpp
#include <stdio.h>

class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class C {
public:
   int g();
};

class D2 : public B {
public:
   using B::f;   // ok: B is a base of D2
   // using C::g;   // error: C isn't a base of D2
};

int main() {
   D2 MyD2;
   MyD2.f('a');
}
```

```Output
In B::f()
```

## <a name="example"></a>Przykład

Składowe zadeklarowane za pomocą deklaracji using mogą być przywoływane przy użyciu jawnej kwalifikacji. Prefiks `::` odwołuje się do globalnej przestrzeni nazw.

```cpp
// using_declaration3.cpp
#include <stdio.h>

void f() {
   printf_s("In f\n");
}

namespace A {
   void g() {
      printf_s("In A::g\n");
   }
}

namespace X {
   using ::f;   // global f is also visible as X::f
   using A::g;   // A's g is now visible as X::g
}

void h() {
   printf_s("In h\n");
   X::f();   // calls ::f
   X::g();   // calls A::g
}

int main() {
   h();
}
```

```Output
In h
In f
In A::g
```

## <a name="example"></a>Przykład

W przypadku złożenia deklaracji using, synonim utworzony przez deklarację odwołuje się tylko do definicji, które są prawidłowe w punkcie deklaracji using. Definicje dodane do przestrzeni nazw po deklaracji using nie są prawidłowymi synonimami.

Nazwa zdefiniowana za pomocą deklaracji **using** jest aliasem oryginalnej nazwy. Nie ma to wpływu na typ, połączenie ani inne atrybuty oryginalnej deklaracji.

```cpp
// post_declaration_namespace_additions.cpp
// compile with: /c
namespace A {
   void f(int) {}
}

using A::f;   // f is a synonym for A::f(int) only

namespace A {
   void f(char) {}
}

void f() {
   f('a');   // refers to A::f(int), even though A::f(char) exists
}

void b() {
   using A::f;   // refers to A::f(int) AND A::f(char)
   f('a');   // calls A::f(char);
}
```

## <a name="example"></a>Przykład

W odniesieniu do funkcji w przestrzeniach nazw, jeśli zestaw lokalnych deklaracji i użycie deklaracji dla pojedynczej nazwy są określone w regionie deklaratywnym, muszą one odwoływać się do tej samej jednostki lub muszą odwoływać się do funkcji.

```cpp
// functions_in_namespaces1.cpp
// C2874 expected
namespace B {
    int i;
    void f(int);
    void f(double);
}

void g() {
    int i;
    using B::i;   // error: i declared twice
    void f(char);
    using B::f;   // ok: each f is a function
}
```

W powyższym przykładzie instrukcja `using B::i` powoduje, że druga `int i` być zadeklarowana w funkcji `g()`. Instrukcja `using B::f` nie powoduje konfliktu z funkcją `f(char)`, ponieważ nazwy funkcji wprowadzone przez `B::f` mają różne typy parametrów.

## <a name="example"></a>Przykład

Deklaracja funkcji lokalnej nie może mieć takiej samej nazwy i typu jak funkcja wprowadzona przy użyciu deklaracji. Na przykład:

```cpp
// functions_in_namespaces2.cpp
// C2668 expected
namespace B {
    void f(int);
    void f(double);
}

namespace C {
    void f(int);
    void f(double);
    void f(char);
}

void h() {
    using B::f;          // introduces B::f(int) and B::f(double)
    using C::f;          // C::f(int), C::f(double), and C::f(char)
    f('h');              // calls C::f(char)
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)
}
```

## <a name="example"></a>Przykład

W odniesieniu do dziedziczenia, gdy deklaracja using wprowadza nazwę z klasy bazowej do zakresu klasy pochodnej, funkcje składowe w klasie pochodnej przesłaniają wirtualne funkcje Członkowskie o tej samej nazwie i typach argumentów w klasie bazowej.

```cpp
// using_declaration_inheritance1.cpp
#include <stdio.h>
struct B {
   virtual void f(int) {
      printf_s("In B::f(int)\n");
   }

   virtual void f(char) {
      printf_s("In B::f(char)\n");
   }

   void g(int) {
      printf_s("In B::g\n");
   }

   void h(int);
};

struct D : B {
   using B::f;
   void f(int) {   // ok: D::f(int) overrides B::f(int)
      printf_s("In D::f(int)\n");
   }

   using B::g;
   void g(char) {   // ok: there is no B::g(char)
      printf_s("In D::g(char)\n");
   }

   using B::h;
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)
};

void f(D* pd) {
   pd->f(1);     // calls D::f(int)
   pd->f('a');   // calls B::f(char)
   pd->g(1);     // calls B::g(int)
   pd->g('a');   // calls D::g(char)
}

int main() {
   D * myd = new D();
   f(myd);
}
```

```Output
In D::f(int)
In B::f(char)
In B::g
In D::g(char)
```

## <a name="example"></a>Przykład

Wszystkie wystąpienia nazwy wymienionej w deklaracji using muszą być dostępne. W szczególności, jeśli Klasa pochodna używa deklaracji using w celu uzyskania dostępu do składowej klasy bazowej, nazwa elementu członkowskiego musi być dostępna. Jeśli nazwa jest funkcją przeciążonej funkcji członkowskiej, wszystkie funkcje o nazwie muszą być dostępne.

Aby uzyskać więcej informacji na temat ułatwienia dostępu dla członków, zobacz [member-Access Control](../cpp/member-access-control-cpp.md).

```cpp
// using_declaration_inheritance2.cpp
// C2876 expected
class A {
private:
   void f(char);
public:
   void f(int);
protected:
   void g();
};

class B : public A {
   using A::f;   // C2876: A::f(char) is inaccessible
public:
   using A::g;   // B::g is a public synonym for A::g
};
```

## <a name="see-also"></a>Zobacz także

[Przestrzenie nazw](../cpp/namespaces-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)