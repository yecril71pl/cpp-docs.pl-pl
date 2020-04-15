---
title: 'Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5bec92ce2bd97f11723cdf59c58b7331b39565f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370183"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)

W tym artykule pokazano, jak zdefiniować i używać zdefiniowanych przez użytkownika typów odwołań i typów wartości w języku C++/CLI.

## <a name="contents"></a><a name="BKMK_Contents"></a>Zawartość

[Tworzenie wystąpienia obiektu](#BKMK_Object_instantiation)

[Klasy abstrakcyjne niejawnie](#BKMK_Implicitly_abstract_classes)

[Widoczność typu](#BKMK_Type_visibility)

[Widoczność członków](#BKMK_Member_visibility)

[Publiczne i prywatne klasy macierzyste](#BKMK_Public_and_private_native_classes)

[Konstruktory statyczne](#BKMK_Static_constructors)

[Semantyka tego wskaźnika](#BKMK_Semantics_of_the_this_pointer)

[Funkcje ukrywania według podpisu](#BKMK_Hide_by_signature_functions)

[Konstruktory kopiowania](#BKMK_Copy_constructors)

[Destruktory i finalizatory](#BKMK_Destructors_and_finalizers)

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a>Tworzenie wystąpienia obiektu

Odwołania (ref) typy mogą być tworzone tylko na zarządzanym stosie, a nie na stosie lub na macierzystej sterty. Typy wartości można utworzyć wystąpienia na stosie lub sterty zarządzanej.

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a>Klasy abstrakcyjne niejawnie

*Niejawnie abstrakcyjna klasa* nie może zostać szesnastkona. Klasa jest niejawnie abstrakcyjne, jeśli typ podstawowy klasy jest interfejsem i klasa nie implementuje wszystkie funkcje członkowskie interfejsu.

Jeśli nie można skonstruować obiektów z klasy, która pochodzi z interfejsu, przyczyną może być, że klasa jest niejawnie abstrakcyjne. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [streszczenie](../extensions/abstract-cpp-component-extensions.md).

Poniższy przykład kodu pokazuje, że `MyClass` nie można `MyClass::func2` utworzyć wystąpienia klasy, ponieważ funkcja nie jest implementowana. Aby włączyć przykład do kompilacji, `MyClass::func2`uncomment .

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a>Widoczność typu

Można kontrolować widoczność typów środowiska uruchomieniowego języka wspólnego (CLR), tak aby, jeśli odwołuje się do zestawu, typy w zestawie mogą być widoczne lub nie widoczne poza zestawem.

`public`wskazuje, że typ jest widoczny dla dowolnego `#using` pliku źródłowego, który zawiera dyrektywę dla zestawu, który zawiera typ.  `private`wskazuje, że typ nie jest widoczny dla `#using` plików źródłowych, które zawierają dyrektywę dla zestawu, który zawiera typ. Jednak typy prywatne są widoczne w ramach tego samego zestawu. Domyślnie widoczność dla klasy `private`to .

Domyślnie przed Visual Studio 2005 typy macierzyste miały dostępność publiczną poza zestawem. Włącz [ostrzeżenie kompilatora (poziom 1) C4692,](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) aby ułatwić wyświetlanie, gdzie prywatne typy macierzyste są używane niepoprawnie. Użyj [pragmy make_public,](../preprocessor/make-public.md) aby zapewnić publiczny dostęp do typu macierzystego w pliku kodu źródłowego, którego nie można modyfikować.

Aby uzyskać więcej informacji, zobacz [#using dyrektywy](../preprocessor/hash-using-directive-cpp.md).

W poniższym przykładzie pokazano, jak zadeklarować typy i określić ich dostępność, a następnie uzyskać dostęp do tych typów wewnątrz zestawu. Oczywiście jeśli zestaw, który ma typy prywatne `#using`odwołuje się przy użyciu , tylko typy publiczne w zestawie są widoczne.

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**Dane wyjściowe**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

Teraz przepiszmy poprzedni przykład, tak aby został zbudowany jako biblioteka DLL.

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

Następny przykład pokazuje, jak uzyskać dostęp do typów poza zestawem. W tym przykładzie klient zużywa składnik, który jest zbudowany w poprzednim przykładzie.

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**Dane wyjściowe**

```Output
in Public_Class
```

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a>Widoczność członków

Dostęp do członka klasy publicznej z tego samego zestawu można uzyskać inaczej niż dostęp do niego spoza `public` `protected`zestawu przy użyciu par specyfikatorów dostępu , i`private`

W tej tabeli podsumowano wpływ różnych specyfikatorów dostępu:

|Specyfikator|Efekt|
|---------------|------------|
|public|Element członkowski jest dostępny wewnątrz i na zewnątrz zestawu.  Zobacz [publiczne,](../cpp/public-cpp.md) aby uzyskać więcej informacji.|
|private|Element członkowski nie jest dostępny ani wewnątrz, ani na zewnątrz zestawu.  Zobacz [prywatne,](../cpp/private-cpp.md) aby uzyskać więcej informacji.|
|protected|Element członkowski jest dostępny wewnątrz i na zewnątrz zestawu, ale tylko do typów pochodnych.  Zobacz [chronione, aby](../cpp/protected-cpp.md) uzyskać więcej informacji.|
|internal|Element członkowski jest publiczny wewnątrz zestawu, ale prywatny poza zestawem.  `internal`jest słowem kluczowym kontekstowym.  Aby uzyskać więcej informacji, zobacz [Słowa kluczowe kontekstowe](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|chronionej lub chronionej przez społeczeństwo|Element członkowski jest publiczny wewnątrz zestawu, ale chroniony poza zestawem.|
|prywatne chronione lub chronione prywatne|Element członkowski jest chroniony wewnątrz zestawu, ale prywatny poza zestawem.|

W poniższym przykładzie pokazano typ publiczny, który ma członków, które są zadeklarowane z różnych możliwości dostępu, a następnie pokazuje dostęp do tych elementów członkowskich z wewnątrz zestawu.

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**Dane wyjściowe**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

Teraz skompilujmy poprzedni przykład jako bibliotekę DLL.

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

Poniższy przykład zużywa składnik, który jest tworzony w poprzednim przykładzie, a tym samym pokazuje, jak uzyskać dostęp do elementów członkowskich spoza zestawu.

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**Dane wyjściowe**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a>Publiczne i prywatne klasy macierzyste

Do typu macierzystego można odwoływać się z typu zarządzanego.  Na przykład funkcja w typie zarządzanym może przyjmować parametr, którego typ jest strukturą macierzystą.  Jeśli typ zarządzany i funkcja są publiczne w zestawie, typ macierzysty musi być również publiczny.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Następnie utwórz plik kodu źródłowego, który zużywa typ macierzysty:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Teraz skompiluj klienta:

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a>Konstruktory statyczne

Typ CLR — na przykład klasa lub struktura — może mieć statyczny konstruktor, który może służyć do inicjowania statycznych elementów członkowskich danych.  Konstruktor statyczny jest wywoływana co najwyżej raz i jest wywoływana przed każdy statyczny element członkowski typu jest dostępny po raz pierwszy.

Konstruktor wystąpienia zawsze działa po konstruktorze statycznym.

Kompilator nie może wbudowane wywołanie konstruktora, jeśli klasa ma konstruktora statycznego.  Kompilator nie może wbudowane wywołanie dowolnej funkcji elementu członkowskiego, jeśli klasa jest typem wartości, ma konstruktor statyczny i nie ma konstruktora wystąpienia.  CLR może wbudowane wywołanie, ale kompilator nie może.

Zdefiniuj konstruktora statycznego jako funkcję prywatnego elementu członkowskiego, ponieważ ma być wywoływana tylko przez CLR.

Aby uzyskać więcej informacji na temat konstruktorów statycznych, zobacz [Jak: Definiowanie konstruktora statycznego interfejsu (C++/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**Dane wyjściowe**

```Output
in static constructor
10
11
```

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>Semantyka tego wskaźnika

Podczas definiowania typów za pomocą programu `this` Visual C++ wskaźnik w typie odwołania jest typu "dojście". Wskaźnik `this` w typie wartości jest typu "wskaźnik wewnętrzny".

Te różne semantyki `this` wskaźnika może spowodować nieoczekiwane zachowanie, gdy wywoływany jest domyślny indeksator. W następnym przykładzie pokazano prawidłowy sposób dostępu do domyślnego indeksatora zarówno w typie ref i typie wartości.

Aby uzyskać więcej informacji, zobacz

- [Operator uchwytu do obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**Dane wyjściowe**

```Output
10.89
10.89
```

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a>Funkcje ukrywania według podpisu

W standardzie C++ funkcja w klasie podstawowej jest ukryta przez funkcję, która ma taką samą nazwę w klasie pochodnej, nawet jeśli funkcja klasy pochodnej nie ma tej samej liczby lub rodzaju parametrów. Jest to określane jako semantyka *hide-by-name.* W typie odwołania funkcja w klasie podstawowej może być ukryta tylko przez funkcję w klasie pochodnej, jeśli zarówno nazwa, jak i lista parametrów są takie same. Jest to znane jako semantyka *hide-by-signature.*

Klasa jest uważana za klasę hide-by-signature, gdy wszystkie jej `hidebysig`funkcje są oznaczone w metadanych jako . Domyślnie wszystkie klasy, które są tworzone `hidebysig` w **obszarze /clr** mają funkcje. Gdy klasa `hidebysig` ma funkcje, kompilator nie ukrywa funkcji według nazwy w żadnych bezpośrednich klas podstawowych, ale jeśli kompilator napotka klasę hide-by-name w łańcuchu dziedziczenia, kontynuuje to zachowanie hide-by-name.

W obszarze semantyka hide-by-signature, gdy funkcja jest wywoływana na obiekcie, kompilator identyfikuje najbardziej pochodną klasę, która zawiera funkcję, która może spełnić wywołanie funkcji. Jeśli istnieje tylko jedna funkcja w klasie, która może spełnić wywołanie, kompilator wywołuje tę funkcję. Jeśli istnieje więcej niż jedna funkcja w klasie, która może spełnić wywołanie, kompilator używa reguł rozpoznawania przeciążenia, aby określić, która funkcja do wywołania. Aby uzyskać więcej informacji na temat reguł przeciążenia, zobacz [Przeciążanie funkcji](../cpp/function-overloading.md).

Dla danego wywołania funkcji funkcja w klasie podstawowej może mieć podpis, który sprawia, że nieco lepiej niż funkcja w klasie pochodnej. Jednak jeśli funkcja została jawnie wywołana na obiekt klasy pochodnej, funkcja w klasie pochodnej jest wywoływana.

Ponieważ zwracana wartość nie jest uważana za część podpisu funkcji, funkcja klasy podstawowej jest ukryta, jeśli ma taką samą nazwę i przyjmuje taką samą liczbę i rodzaj argumentów jak funkcja klasy pochodnej, nawet jeśli różni się typem wartości zwracanej.

Poniższy przykład pokazuje, że funkcja w klasie podstawowej nie jest ukryta przez funkcję w klasie pochodnej.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**Dane wyjściowe**

```Output
Base::Test
```

Następny przykład pokazuje, że kompilator Microsoft C++ wywołuje funkcję w klasie najbardziej pochodnej — nawet jeśli konwersja jest wymagana do dopasowania jednego lub więcej parametrów — a nie wywołać funkcję w klasie podstawowej, która jest lepiej dopasowana do wywołania funkcji.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**Dane wyjściowe**

```Output
Derived::Test2
```

Poniższy przykład pokazuje, że można ukryć funkcję, nawet jeśli klasa podstawowa ma taką samą sygnaturę jak klasa pochodna.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**Dane wyjściowe**

```Output
Derived::Test4
97
```

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a>Konstruktory kopiowania

Standard C++ mówi, że konstruktor kopii jest wywoływana, gdy obiekt jest przenoszony, tak, że obiekt jest tworzony i niszczony pod tym samym adresem.

Jednak gdy **/clr** jest używany do kompilowania i funkcja, która jest kompilowana do MSIL wywołuje funkcję macierzystą, gdzie klasa macierzysta — lub więcej niż jeden — jest przekazywana przez wartość i gdzie klasa macierzysta ma konstruktora kopii i/lub destruktora, nie wywoływany jest konstruktor kopiowania, a obiekt jest niszczony pod innym adresem niż tam, gdzie został utworzony. Może to spowodować problemy, jeśli klasa ma wskaźnik do siebie lub jeśli kod jest śledzenie obiektów według adresu.

Aby uzyskać więcej informacji, zobacz [/clr (Kompilacja środowiska wykonawczego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

Poniższy przykład pokazuje, gdy konstruktor kopii nie jest generowany.

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**Dane wyjściowe**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a>Destruktory i finalizatory

Destruktory w typie odwołania wykonują deterministyczne oczyszczanie zasobów. Finalizatory oczyścić niezarządzanych zasobów i mogą być wywoływane deterministically przez destruktora lub niedeterministycznie przez moduł zbierający elementy bezużyteczne. Aby uzyskać informacje na temat destruktorów w standardowym języku C++, zobacz [Destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Zachowanie destruktorów w zarządzanej klasie Visual C++ różni się od rozszerzeń zarządzanych dla języka C++. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [Zmiany w semantyki destruktora](../dotnet/changes-in-destructor-semantics.md).

Moduł zbierający elementy bezużyteczne CLR usuwa nieużywane obiekty zarządzane i zwalnia ich pamięci, gdy nie są już wymagane. Jednak typ może używać zasobów, które moduł odśmiecania elementów bezużytecznych nie wie, jak zwolnić. Zasoby te są nazywane zasobami niezarządzanymi (na przykład dojścia do plików natywnych). Zaleca się zwolnienie wszystkich zasobów niezarządzanych w finalizatorze. Ponieważ zasoby zarządzane są zwalniane niedeterministycznie przez moduł zbierający elementy bezużyteczne, nie jest bezpieczne odwoływanie się do zasobów zarządzanych w finalizatorze, ponieważ jest możliwe, że moduł zbierający elementy bezużyteczne już oczyścił ten zarządzany zasób.

Visual C++ finalizatora nie jest <xref:System.Object.Finalize%2A> taka sama jak metoda. (Dokumentacja CLR używa finalizatora <xref:System.Object.Finalize%2A> i metody synonimicznie). Metoda <xref:System.Object.Finalize%2A> jest wywoływana przez moduł zbierający elementy bezużyteczne, który wywołuje każdy finalizator w łańcuchu dziedziczenia klasy. W przeciwieństwie do destruktorów Visual C++ wywołanie finalizatora klasy pochodnej nie powoduje, że kompilator wywołać finalizatora we wszystkich klasach podstawowych.

Ponieważ kompilator Microsoft C++ obsługuje deterministycznej wersji zasobów, <xref:System.IDisposable.Dispose%2A> <xref:System.Object.Finalize%2A> nie próbuj zaimplementować lub metody. Jednak jeśli znasz te metody, oto jak Visual C++ finalizatora i destruktora, który <xref:System.IDisposable.Dispose%2A> wywołuje mapę finalizatora do wzorca:

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

Typ zarządzany może również używać zasobów zarządzanych, które wolełyby zwolnić deterministycznie i nie pozostawić modułowi zbierającemu elementy bezużyteczne do wydania niedeterministycznie w pewnym momencie po obiekt nie jest już wymagane. Deterministyczne uwalnianie zasobów może znacznie poprawić wydajność.

Kompilator Microsoft C++ umożliwia definicję destruktora do deterministycznie oczyścić obiekty. Użyj destruktora, aby zwolnić wszystkie zasoby, które mają być deterministycznie zwolnić.  Jeśli finalizator jest obecny, wywołać go z destruktora, aby uniknąć duplikacji kodu.

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

Jeśli kod, który zużywa typ nie wywoła destruktora, moduł zbierający elementy bezużyteczne ostatecznie zwalnia wszystkie zasoby zarządzane.

Obecność destruktora nie oznacza obecności finalizatora. Jednak obecność finalizatora oznacza, że należy zdefiniować destruktora i wywołać finalizatora z tego destruktora. Zapewnia to deterministyczne wydanie zasobów niezarządzanych.

Wywołanie destruktora pomija <xref:System.GC.SuppressFinalize%2A>— za pomocą — finalizacji obiektu. Jeśli destruktor nie jest wywoływana, finalizatora typu ostatecznie zostanie wywołana przez moduł zbierający elementy bezużyteczne.

Deterministically czyszczenie zasobów obiektu przez wywołanie destruktora może zwiększyć wydajność w porównaniu z najmu CLR niedeterministycznie sfinalizować obiekt.

Kod, który jest napisany w języku Visual C++ i skompilowany przy użyciu **/clr** uruchamia destruktora typu, jeśli:

- Obiekt, który jest tworzony przy użyciu semantyki stosu wykracza poza zakres. Aby uzyskać więcej informacji, zobacz [Semantyka stosu języka C++ dla typów odwołań](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Wyjątek jest zgłaszany podczas budowy obiektu.

- Obiekt jest elementem członkowskim w obiekcie, którego destruktor jest uruchomiony.

- Operator [usuwania](../cpp/delete-operator-cpp.md) jest wywoływany na dojście[(Dojem do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Jawnie wywołać destruktora.

Jeśli typ jest zużywany przez klienta, który jest napisany w innym języku, destruktor jest wywoływana w następujący sposób:

- Na wezwanie <xref:System.IDisposable.Dispose%2A>do .

- Na wywołanie `Dispose(void)` typu.

- Jeśli typ wykracza poza zakres w `using` instrukcji C#.

Jeśli tworzysz obiekt typu odwołania na zarządzanym stosie (nie używasz semantyki stosu dla typów odwołań), użyj składni [try-finally,](../cpp/try-finally-statement.md) aby upewnić się, że wyjątek nie uniemożliwia uruchamiania destruktora.

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

Jeśli typ ma destruktora, kompilator `Dispose` generuje metodę, która implementuje <xref:System.IDisposable>. Jeśli typ, który jest napisany w języku Visual C++ i ma destruktora, który jest zużywany z innego języka, wywołanie `IDisposable::Dispose` tego typu powoduje, że destruktor typu ma zostać wywołany. Gdy typ jest zużywany z klienta języka Visual C++, `Dispose`nie można bezpośrednio wywołać; zamiast tego wywołać destruktora `delete` za pomocą operatora.

Jeśli typ ma finalizator, kompilator `Finalize(void)` generuje metodę, <xref:System.Object.Finalize%2A>która zastępuje .

Jeśli typ ma finalizatora lub destruktora, kompilator `Dispose(bool)` generuje metodę, zgodnie z wzorcem projektu. (Aby uzyskać więcej informacji, zobacz [Usuwanie wzoru).](/dotnet/standard/design-guidelines/dispose-pattern) Nie można jawnie `Dispose(bool)` autor lub wywołać w języku Visual C++.

Jeśli typ ma klasę podstawową, która jest zgodna ze wzorcem projektu, destruktory dla wszystkich klas podstawowych są wywoływane, gdy wywoływany jest destruktor dla klasy pochodnej. (Jeśli typ jest napisany w języku Visual C++, kompilator zapewnia, że typy implementują ten wzorzec.) Innymi słowy destruktor sieci klas odniesienia do jego baz i elementów członkowskich, zgodnie z określonymi przez standard C++ — najpierw uruchamiany jest destruktor klasy, następnie destruktory dla jego elementów członkowskich w odwrotnej kolejności, w jakiej zostały zbudowane, a na koniec destruktory dla jego klas podstawowych w odwrotnej kolejności, w jakiej zostały zbudowane.

Destruktory i finalizatory nie są dozwolone wewnątrz typów wartości lub interfejsów.

Finalizator można zdefiniować lub zadeklarować tylko w typie odwołania. Podobnie jak konstruktor i destruktor, finalizator nie ma typu zwracanego.

Po uruchomieniu finalizatora obiektu, finalizatory w dowolnej klasy podstawowej są również wywoływane, począwszy od typu najmniej pochodnego. Finalizatory dla elementów członkowskich danych nie są automatycznie połączone z przez finalizatora klasy.

Jeśli finalizator usuwa wskaźnik macierzysty w typie zarządzanym, należy upewnić się, że odwołania do lub za pośrednictwem wskaźnika macierzystego nie są zbierane przedwcześnie; wywołać destruktora na typ zarządzany <xref:System.GC.KeepAlive%2A>zamiast używać .

W czasie kompilacji można wykryć, czy typ ma finalizatora lub destruktora. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora cech typu](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Następny przykład pokazuje dwa typy, jeden, który ma niezarządzane zasoby i jeden, który zarządzał zasobami, które są deterministycznie zwolnione.

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
