---
title: Błąd kompilatora C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 74c5032338b3f4cf30bdb75bdf070cee7b67ce58
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742115"
---
# <a name="compiler-error-c2440"></a>Błąd kompilatora C2440

"Konwersja": nie można konwertować z "type1" na "type2"

Kompilator nie może rzutować z `type1` na `type2` .

C2440 może być spowodowany próbą zainicjowania niestałej **`char*`** (lub) przy `wchar_t*` użyciu literału ciągu w kodzie C++, gdy opcja zgodności kompilatora [/Zc: strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) jest ustawiona. W C, typ literału ciągu jest tablicą **`char`** , ale w języku C++ jest tablicą `const char` .

## <a name="examples"></a>Przykłady

Ten przykład generuje C2440:

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

C2440 może również być spowodowany próbą przekonwertowania wskaźnika do elementu członkowskiego na typ void *. Następny przykład generuje C2440:

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

C2440 może również być spowodowany próbą rzutowania z typu, który jest tylko zadeklarowany do przodu, ale nie jest zdefiniowany. Ten przykład generuje C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

Błędy C2440 w wierszach 15 i 16 z kolejnego przykładu są kwalifikowane do `Incompatible calling conventions for UDT return value` wiadomości. *UDT* to typ zdefiniowany przez użytkownika, taki jak Klasa, struktura lub Unia. Te rodzaje błędów niezgodności są spowodowane tym, gdy Konwencja wywoływania UDT określona w zwracanym typie deklaracji do przodu powoduje konflikt z rzeczywistą konwencją wywoływania UDT i kiedy jest używana wskaźnik funkcji.

W przykładzie najpierw istnieją deklaracje dalej dla struktury i dla funkcji, która zwraca strukturę; kompilator zakłada, że struktura używa konwencji wywoływania języka C++. Następnie jest definicją struktury, która domyślnie używa konwencji wywoływania języka C. Ponieważ kompilator nie zna konwencji wywoływania struktury, dopóki nie zakończy się odczytywanie całej struktury, przyjęto również konwencję wywoływania dla struktury w typie zwracanym jako `get_c2` C++.

Następuje struktura jest kolejną deklaracją funkcji, która zwraca strukturę, ale w tym momencie kompilator wie, że konwencją wywoływania struktury jest C++. Podobnie, wskaźnik funkcji, która zwraca strukturę, jest zdefiniowany po definicji struktury, tak aby kompilator wie, że struktura używa konwencji wywoływania języka C++.

Aby rozwiązać C2440 występujący ze względu na niezgodne konwencje wywoływania, należy zadeklarować funkcje, które zwracają UDT po definicji UDT.

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

C2440 może również wystąpić, Jeśli przypiszesz zero do wewnętrznego wskaźnika:

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

C2440 może również wystąpić w przypadku nieprawidłowego użycia konwersji zdefiniowanej przez użytkownika. Na przykład, gdy operator konwersji został zdefiniowany jako **`explicit`** , kompilator nie może użyć go w niejawnej konwersji. Aby uzyskać więcej informacji dotyczących konwersji zdefiniowanych przez użytkownika, zobacz [konwersje zdefiniowane przez użytkownika (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Ten przykład generuje C2440:

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

C2440 może również wystąpić, jeśli spróbujesz utworzyć wystąpienie tablicy Visual C++, której typem jest <xref:System.Array> .  Aby uzyskać więcej informacji, zobacz [tablice](../../extensions/arrays-cpp-component-extensions.md).  Następny przykład generuje C2440:

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

C2440 może również wystąpić ze względu na zmiany w funkcji atrybutów.  Poniższy przykład generuje C2440.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

Kompilator języka Microsoft C++ nie zezwala już [operatorowi const_cast](../../cpp/const-cast-operator.md) na rzutowanie, gdy jest kompilowany kod źródłowy korzystający z programowania **/CLR** .

Aby rozwiązać ten C2440, użyj poprawnego operatora rzutowania. Aby uzyskać więcej informacji, zobacz [Operatory rzutowania](../../cpp/casting-operators.md).

Ten przykład generuje C2440:

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

C2440 może wystąpić ze względu na zgodność ze zmianami kompilatora w programie Visual Studio 2015 Update 3. Wcześniej kompilator nieprawidłowo traktował określone wyrażenie DISTINCT jako ten sam typ podczas identyfikowania dopasowania szablonu dla **`static_cast`** operacji. Teraz kompilator rozróżnia typy prawidłowo, a kod, który opierał się na poprzednim **`static_cast`** zachowaniu, jest przerwany. Aby rozwiązać ten problem, Zmień argument szablonu tak, aby pasował do typu parametru szablonu lub użyć **`reinterpret_cast`** rzutowania w stylu języka C.

Ten przykład generuje C2440:

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

### <a name="copy-list-initialization"></a>Inicjalizacja kopiowania listy

Program Visual Studio 2017 lub nowszy prawidłowo podnosi błędy kompilatora związane z tworzeniem obiektów przy użyciu list inicjatorów, które nie zostały przechwycone w programie Visual Studio 2015 i mogą prowadzić do awarii lub niezdefiniowanego zachowania środowiska uruchomieniowego. W przypadku inicjalizacji listy kopii w języku C++ 17, kompilator jest wymagany do uwzględnienia jawnego konstruktora w celu rozpoznania przeciążenia, ale musi zgłosić błąd, jeśli to przeciążenie jest rzeczywiście wybrane.

Poniższy przykład kompiluje w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

Aby poprawić błąd, użyj bezpośredniej inicjalizacji:

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

### <a name="cv-qualifiers-in-class-construction"></a>kwalifikatory CV w konstrukcji klasy

W programie Visual Studio 2015 kompilator czasami niepoprawnie ignoruje kwalifikator CV podczas generowania obiektu klasy za pośrednictwem wywołania konstruktora. Może to spowodować awarię lub nieoczekiwane zachowanie środowiska uruchomieniowego. Poniższy przykład kompiluje w programie Visual Studio 2015, ale wywołuje błąd kompilatora w programie Visual Studio 2017 lub nowszym:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby poprawić błąd, zadeklaruj operator int () jako const.
