---
title: Błąd kompilatora C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: f37c8b4e75b530f69c94c2e9e356a05d50397d29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571291"
---
# <a name="compiler-error-c2440"></a>Błąd kompilatora C2440

'conversion': nie można konwertować z 'Typ1' na 'type2'

Kompilator nie może rzutować z `type1` do `type2`.

## <a name="example"></a>Przykład

C2440 może być spowodowany, jeśli użytkownik spróbuje zainicjować wartości innej niż stała `char*` (lub `wchar_t*`) przy użyciu ciągu literału w przypadku kodu C++, gdy opcję zgodności kompilatora [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) jest ustawiona. W języku C typem literału ciągu jest tablica `char`, ale w języku C++ jest Tablica obiektów `const char`. Ten przykład generuje C2440:

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

## <a name="example"></a>Przykład

Jeśli użytkownik spróbuje przekonwertować wskaźnik do elementu void *, może być także spowodowany C2440. Następny przykład generuje C2440:

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

## <a name="example"></a>Przykład

Można również c2440 Jeśli próbowano rzutowania z typu, który jest tylko do przodu jest zadeklarowana, ale nie jest zdefiniowany. Ten przykład generuje C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}

```

## <a name="example"></a>Przykład

Błędy C2440 w wierszach 15 i 16 następnej próbki są kwalifikowane `Incompatible calling conventions for UDT return value` wiadomości. A *UDT* jest typ zdefiniowany przez użytkownika, takie jak klasy, struktury lub Unii. Tego rodzaju błędy niezgodności powstają, gdy konwencja wywołania UDT określona w typie zwracanym przyszłych deklaracji koliduje z rzeczywistą konwencją wywołania UDT, i w przypadku wskaźnika funkcji.

W tym przykładzie najpierw są deklaracje przechodzenia do przodu dla struktury i dla funkcji zwracającej strukturę; kompilator zakłada, że struktura używa konwencji wywoływania języka C++. Następna jest definicja struktury, która domyślnie używa języka C Konwencja wywoływania. Ponieważ kompilator nie zna konwencji wywołania struktury, do momentu zakończenia na całej strukturze konwencją wywołania dla struktur w typie zwracanym `get_c2` również muszą być w języku C++.

Struktura występuje kolejna deklaracja funkcji zwracająca strukturę, ale w tym momencie kompilator wie, że Konwencja wywołania struktury to C++. Podobnie wskaźnik funkcji, która zwraca strukturę, jest zdefiniowany po definicji struktury, tak, aby kompilator wiedział, że struktura używa konwencji wywoływania języka C++.

Aby rozwiązać problem C2440 występujący na skutek niezgodności konwencji wywoływania, Zadeklaruj funkcje wracające do UDT po definicji UDT.

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

## <a name="example"></a>Przykład

C2440 może również wystąpić, jeśli przypiszesz zero do wnętrza wskaźnika:

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

## <a name="example"></a>Przykład

C2440 może również wystąpić dla niepoprawnego użycia konwersji zdefiniowanej przez użytkownika. Na przykład, gdy operator konwersji został zdefiniowany jako `explicit`, kompilator nie można go używać w niejawną konwersję. Aby uzyskać więcej informacji dotyczących konwersji zdefiniowanych przez użytkownika, zobacz [konwersje zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Ten przykład generuje C2440:

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

## <a name="example"></a>Przykład

C2440 może również wystąpić, jeśli zostanie podjęta próba utworzenia instancji tablicy języka Visual C++, którego typem jest <xref:System.Array>.  Aby uzyskać więcej informacji, zobacz [tablic](../../windows/arrays-cpp-component-extensions.md).  Następny przykład generuje C2440:

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

## <a name="example"></a>Przykład

C2440 może również wystąpić z powodu zmian w funkcji atrybutów.  Poniższy przykład generuje C2440.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>Przykład

Kompilator języka Visual C++ nie zezwala już [const_cast Operator](../../cpp/const-cast-operator.md) na spadek, gdy kod, który używa **/CLR** programowania jest kompilowany.

Aby rozwiązać ten C2440, użyj prawidłowego operatora rzutowania. Aby uzyskać więcej informacji, zobacz [operatorów rzutowania](../../cpp/casting-operators.md).

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

## <a name="example"></a>Przykład

C2440 może wystąpić z powodu zmian zgodności kompilatora w programie Visual Studio 2015 Update 3. Wcześniej kompilator niepoprawnie uznaje niektóre wyrażenia distinct tego samego typu przy identyfikowaniu dopasowania szablonu dla `static_cast` operacji. Obecnie kompilator poprawnie rozróżnia typów i kodu, opiera się na poprzednim `static_cast` zachowanie jest uszkodzona. Aby rozwiązać ten problem, należy zmienić argument szablonu, który jest zgodny z typem parametru szablonu lub skorzystania z `reinterpret_cast` lub rzutowania w stylu języka C.

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

## <a name="example"></a>Przykład

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 i nowszym poprawnie zgłaszać błędy kompilatora dotyczące tworzenia obiektów przy użyciu listy inicjatorów, które nie zostały wykryte w Visual Studio 2015 i może prowadzić do awarii lub niezdefiniowane zachowanie środowiska uruchomieniowego. W języku C ++ 17 listy Inicjalizacja kopiowania kompilator jest wymagany do rozważenia jawny Konstruktor przypadku rozpoznawania przeciążenia, ale musi zgłosić błąd, jeśli niejawnej tego przeciążenia.

Poniższy przykład tworzy jedynie w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby poprawić ten błąd, należy użyć inicjalizacji bezpośredniej:

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

## <a name="example"></a>Przykład

### <a name="cv-qualifiers-in-class-construction"></a>Kwalifikatory CV w konstrukcji klasy

W programie Visual Studio 2015 Kompilator ignoruje czasami niepoprawnie Kwalifikator cv podczas generowania obiektu przez wywołanie konstruktora klasy. Może to teoretycznie spowodować awarię lub nieoczekiwane zachowanie. W poniższym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd kompilatora w programie Visual Studio 2017 i nowszych:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby poprawić ten błąd, należy zadeklarować operatora int() jako const.
