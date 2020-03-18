---
title: 'Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418294"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)

W tym artykule pokazano, jak definiować i korzystać z typów referencyjnych zdefiniowanych przez użytkownika i C++typów wartości w/CLI.

##  <a name="BKMK_Contents"></a>Contents

[Tworzenie wystąpienia obiektu](#BKMK_Object_instantiation)

[Klasy abstrakcyjne niejawnie](#BKMK_Implicitly_abstract_classes)

[Widoczność typu](#BKMK_Type_visibility)

[Widoczność elementów członkowskich](#BKMK_Member_visibility)

[Publiczne i prywatne klasy natywne](#BKMK_Public_and_private_native_classes)

[Konstruktory statyczne](#BKMK_Static_constructors)

[Semantyka tego wskaźnika](#BKMK_Semantics_of_the_this_pointer)

[Funkcje ukrywania za pomocą podpisu](#BKMK_Hide_by_signature_functions)

[Kopiuj konstruktory](#BKMK_Copy_constructors)

[Destruktory i finalizatory](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a>Tworzenie wystąpienia obiektu

Typy odwołań (ref) można tworzyć tylko na stercie zarządzanym, a nie na stosie ani na stercie natywnym. Typy wartości można tworzyć przy użyciu stosu lub sterty zarządzanej.

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

##  <a name="BKMK_Implicitly_abstract_classes"></a>Klasy abstrakcyjne niejawnie

Nie można utworzyć wystąpienia *niejawnie klasy abstrakcyjnej* . Klasa jest abstrakcyjna niejawnie, jeśli typ podstawowy klasy jest interfejsem, a Klasa nie implementuje wszystkich funkcji elementów członkowskich interfejsu.

Jeśli nie można skonstruować obiektów z klasy, która jest pochodną interfejsu, przyczyną może być niejawne abstrakcyjność klasy. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstract](../extensions/abstract-cpp-component-extensions.md).

Poniższy przykład kodu demonstruje, że nie można utworzyć wystąpienia klasy `MyClass`, ponieważ `MyClass::func2` funkcji nie jest zaimplementowana. Aby włączyć przykład do kompilowania, Usuń komentarz `MyClass::func2`.

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

##  <a name="BKMK_Type_visibility"></a>Widoczność typu

Można kontrolować widoczność typów środowiska uruchomieniowego języka wspólnego (CLR), tak aby, jeśli odwołuje się do zestawu, typy w zestawie mogą być widoczne lub nie być widoczne poza zestawem.

`public` wskazuje, że typ jest widoczny dla każdego pliku źródłowego, który zawiera `#using` dyrektywy dla zestawu, który zawiera typ.  `private` wskazuje, że typ nie jest widoczny dla plików źródłowych, które zawierają `#using` dyrektywy dla zestawu, który zawiera typ. Jednak typy prywatne są widoczne w tym samym zestawie. Domyślnie widoczność klasy jest `private`.

Domyślnie przed programem Visual Studio 2005 typy natywne miały publiczny dostęp poza zestawem. Włącz [Ostrzeżenie kompilatora (poziom 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) , aby ułatwić sprawdzenie, gdzie prywatne typy natywne są używane nieprawidłowo. Użyj dyrektywy pragma [make_public](../preprocessor/make-public.md) , aby zapewnić publiczny dostęp do typu natywnego w pliku kodu źródłowego, którego nie można modyfikować.

Aby uzyskać więcej informacji, zobacz [#using dyrektywie](../preprocessor/hash-using-directive-cpp.md).

Poniższy przykład pokazuje, jak zadeklarować typy i określić ich dostępność, a następnie uzyskać dostęp do tych typów wewnątrz zestawu. Oczywiście, jeśli do zestawu, który ma typy prywatne jest przywoływany za pomocą `#using`, widoczne są tylko typy publiczne w zestawie.

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

Teraz ponownie napiszemy poprzedni przykład, tak aby był skompilowany jako biblioteka DLL.

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

Następny przykład pokazuje, jak uzyskać dostęp do typów poza zestawem. W tym przykładzie klient korzysta ze składnika skompilowanego w poprzednim przykładzie.

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

##  <a name="BKMK_Member_visibility"></a>Widoczność elementów członkowskich

Dostęp do elementu członkowskiego klasy publicznej można uzyskać z poziomu tego samego zestawu innego niż dostęp do niego spoza zestawu przy użyciu par specyfikatorów dostępu `public`, `protected`i `private`

Ta tabela zawiera podsumowanie wpływu różnych specyfikatorów dostępu:

|Specyfikator|Efekt|
|---------------|------------|
|{1&gt;public&lt;1}|Element członkowski jest dostępny wewnątrz i na zewnątrz zestawu.  Aby uzyskać więcej informacji, zobacz [Public](../cpp/public-cpp.md) .|
|prywatna|Składowa nie jest dostępna, ani wewnątrz ani poza zestawem.  Aby uzyskać więcej informacji, zobacz [Private](../cpp/private-cpp.md) .|
|protected|Składowa jest dostępna wewnątrz i na zewnątrz zestawu, ale tylko dla typów pochodnych.  Aby uzyskać więcej informacji, zobacz [chroniona](../cpp/protected-cpp.md) .|
|internal|Składowa jest publiczna wewnątrz zestawu, ale jest prywatna poza zestawem.  `internal` jest kontekstowego słowa kluczowego.  Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|publiczna chroniona lub chroniona publicznie|Składowa jest publiczna wewnątrz zestawu, ale chroniona poza zestawem.|
|prywatne chronione lub chronione prywatnie|Składowa jest chroniona wewnątrz zestawu, ale prywatny poza zestawem.|

Poniższy przykład pokazuje publiczny typ, który ma składowe, które są zadeklarowane przy użyciu różnych podano, a następnie pokazuje dostęp tych członków z wewnątrz zestawu.

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

Teraz skompilujemy poprzedni przykład jako bibliotekę DLL.

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

Poniższy przykład zużywa składnik, który został utworzony w poprzednim przykładzie, i w ten sposób pokazuje, jak uzyskać dostęp do elementów członkowskich spoza zestawu.

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

##  <a name="BKMK_Public_and_private_native_classes"></a>Publiczne i prywatne klasy natywne

Z typem zarządzanym można odwoływać się do typu natywnego.  Na przykład funkcja w typie zarządzanym może przyjmować parametr, którego typ jest strukturą natywną.  Jeśli typ zarządzany i funkcja są publiczne w zestawie, wówczas typem natywnym również musi być Public.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Następnie utwórz plik kodu źródłowego, który używa typu natywnego:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Teraz Skompiluj klienta:

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

##  <a name="BKMK_Static_constructors"></a>Konstruktory statyczne

Typ CLR — na przykład Klasa lub struktura — może mieć Konstruktor statyczny, którego można użyć do zainicjowania statycznych elementów członkowskich danych.  Konstruktor statyczny jest wywoływany najwyżej raz i jest wywoływany przed uzyskaniem dostępu do dowolnego statycznego elementu członkowskiego typu po raz pierwszy.

Konstruktor wystąpienia zawsze jest uruchamiany po konstruktorze statycznym.

Kompilator nie może wywołać wywołania konstruktora, jeśli klasa ma Konstruktor statyczny.  Kompilator nie może wbudowana wywołania żadnej funkcji członkowskiej, jeśli klasa jest typem wartości, ma statyczny Konstruktor i nie ma konstruktora instancji.  Środowisko CLR może być wbudowane wywołanie, ale kompilator nie może.

Zdefiniuj statyczny Konstruktor jako prywatną funkcję członkowską, ponieważ jest przeznaczony do wywoływania tylko przez środowisko CLR.

Aby uzyskać więcej informacji na temat konstruktorów statycznych, zobacz [How to: define an staticC++Interface Konstruktor (/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

##  <a name="BKMK_Semantics_of_the_this_pointer"></a>Semantyka tego wskaźnika

W przypadku używania wizualizacji C++ do definiowania typów, `this` wskaźnik w typie referencyjnym jest typu "dojście". `this` wskaźnik w typie wartości jest typu "wskaźnik wewnętrzny".

Te różne semantyki wskaźnika `this` mogą spowodować nieoczekiwane zachowanie w przypadku wywołania domyślnego indeksatora. W następnym przykładzie pokazano poprawny sposób dostępu do domyślnego indeksatora zarówno w typie referencyjnym, jak i w typie wartości.

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

##  <a name="BKMK_Hide_by_signature_functions"></a>Funkcje ukrywania za pomocą podpisu

W warstwie C++standardowa funkcja w klasie bazowej jest ukryta przez funkcję, która ma taką samą nazwę w klasie pochodnej, nawet jeśli funkcja klasy pochodnej nie ma tej samej liczby lub rodzaju parametrów. Jest to nazywane semantyką *ukrywania przez nazwę* . W typie referencyjnym funkcja w klasie bazowej może być ukryta przez funkcję w klasie pochodnej, jeśli zarówno nazwa, jak i lista parametrów są takie same. Jest to nazywane semantyką *Ukryj przez podpis* .

Klasa jest traktowana jako Klasa ukrywania za pomocą podpisu, gdy wszystkie jej funkcje są oznaczone w metadanych jako `hidebysig`. Domyślnie wszystkie klasy, które są tworzone w obszarze **/CLR** mają `hidebysig` funkcje. Gdy Klasa ma `hidebysig` funkcje, kompilator nie ukrywa funkcji według nazwy w żadnej bezpośredniej klasie podstawowej, ale jeśli kompilator napotka klasę ukrycia przez nazwę w łańcuchu dziedziczenia, kontynuuje działanie ukrywania przez nazwę.

W obszarze semantyka ukrycia po podpisie, gdy funkcja jest wywoływana w obiekcie, kompilator identyfikuje najbardziej pochodną klasę, która zawiera funkcję, która może spełnić wywołanie funkcji. Jeśli w klasie jest tylko jedna funkcja, która może spełnić wywołanie, kompilator wywołuje tę funkcję. Jeśli w klasie jest więcej niż jedna funkcja, która może spełnić wywołanie, kompilator używa reguł rozpoznawania przeciążenia, aby określić, która funkcja ma być wywoływana. Aby uzyskać więcej informacji na temat reguł przeciążenia, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

Dla danego wywołania funkcji funkcja w klasie bazowej może mieć sygnaturę, która sprawia, że jest nieco lepszym dopasowaniem niż funkcja w klasie pochodnej. Jeśli jednak funkcja została jawnie wywołana dla obiektu klasy pochodnej, wywoływana jest funkcja klasy pochodnej.

Ponieważ wartość zwracana nie jest uważana za część podpisu funkcji, funkcja klasy bazowej jest ukryta, jeśli ma taką samą nazwę i ma tę samą liczbę i rodzaj argumentów jak funkcja klasy pochodnej, nawet jeśli różni się w typie wartości zwracanej.

Poniższy przykład pokazuje, że funkcja w klasie bazowej nie jest ukryta przez funkcję w klasie pochodnej.

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

Następny przykład pokazuje, że kompilator firmy C++ Microsoft wywołuje funkcję w najbardziej pochodnej klasie — nawet wtedy, gdy konwersja jest wymagana do dopasowania jednego lub kilku parametrów — i nie wywołuje funkcji w klasie bazowej, która jest lepszym dopasowaniem dla wywołania funkcji.

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

Poniższy przykład pokazuje, że istnieje możliwość ukrycia funkcji nawet wtedy, gdy klasa podstawowa ma taki sam podpis jak Klasa pochodna.

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

##  <a name="BKMK_Copy_constructors"></a>Kopiuj konstruktory

W C++ standardzie występuje, że Konstruktor kopiujący jest wywoływany, gdy obiekt jest przenoszony, w taki sposób, że obiekt jest tworzony i niszczony pod tym samym adresem.

Jednakże, gdy **/CLR** jest używany do kompilowania i funkcja, która jest skompilowana do MSIL wywołuje funkcję natywną, w której Klasa macierzysta — lub więcej niż jedna — jest przenoszona przez wartość i gdzie Klasa macierzysta ma Konstruktor kopiujący i/lub destruktor, Konstruktor kopiujący nie jest wywoływany i obiekt jest niszczony pod innym adresem niż w miejscu, w którym został utworzony. Może to spowodować problemy, jeśli klasa ma wskaźnik do samego siebie lub jeśli kod śledzi obiekty według adresu.

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

Poniższy przykład pokazuje, kiedy Konstruktor kopiujący nie jest generowany.

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

##  <a name="BKMK_Destructors_and_finalizers"></a>Destruktory i finalizatory

Destruktory w typie referencyjnym wykonują jednoznaczne czyszczenie zasobów. Finalizatory czyścią niezarządzane zasoby i mogą być wywoływane przez destruktor lub Niedeterministyczny przez moduł wyrzucania elementów bezużytecznych. Aby uzyskać informacje o destruktorach w C++warstwie Standardowa, zobacz [destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Zachowanie destruktorów w zarządzanej klasie wizualnej C++ różni się od rozszerzeń zarządzanych dla C++programu. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [zmiany w semantyce destruktora](../dotnet/changes-in-destructor-semantics.md).

Moduł wyrzucania elementów bezużytecznych CLR usuwa nieużywane obiekty zarządzane i zwalnia ich pamięć, gdy nie są już wymagane. Jednak typ może korzystać z zasobów, które nie wiedzą, jak zwolnić. Te zasoby są znane jako niezarządzane zasoby (na przykład natywne uchwyty plików). Zalecamy wydanie wszystkich niezarządzanych zasobów w programie finalizatora. Ponieważ zarządzane zasoby są wydawane w sposób Niedeterministyczny przez moduł wyrzucania elementów bezużytecznych, nie ma bezpiecznego odwoływania się do zasobów zarządzanych w finalizatorze, ponieważ istnieje możliwość, że moduł zbierający elementy bezużyteczne już wyczyszczone.

Program Visual C++ finalizator nie jest taki sam jak Metoda <xref:System.Object.Finalize%2A>. (Dokumentacja środowiska CLR używa metody Finalize i metodę <xref:System.Object.Finalize%2A>. Metoda <xref:System.Object.Finalize%2A> jest wywoływana przez moduł wyrzucania elementów bezużytecznych, który wywołuje każdy finalizator w łańcuchu dziedziczenia klas. W przeciwieństwie C++ do destruktorów wizualnych, wywołanie finalizatora klasy pochodnej nie powoduje, że kompilator wywołuje finalizator we wszystkich klasach bazowych.

Ponieważ kompilator firmy C++ Microsoft obsługuje deterministyczną wersję zasobów, nie należy próbować zaimplementować <xref:System.IDisposable.Dispose%2A> ani <xref:System.Object.Finalize%2A> metod. Jeśli jednak znasz te metody, poniżej przedstawiono sposób, w jaki program Visual C++ finalizatorer i destruktor wywołujący mapę finalizatora do wzorca <xref:System.IDisposable.Dispose%2A>:

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

Typem zarządzanym może być również użycie zarządzanych zasobów, które wolisz zwolnić, i nie pozostawać do wyrzucania elementów bezużytecznych, aby zwolnić niedeterministycznie w pewnym momencie, gdy obiekt nie jest już wymagany. Deterministyczna wersja zasobów może znacząco poprawić wydajność.

Kompilator firmy C++ Microsoft umożliwia definiowanie destruktora do niejednoznacznego czyszczenia obiektów. Użyj destruktora, aby zwolnić wszystkie zasoby, które mają być wydane w sposób deterministyczny.  Jeśli jest obecny finalizator, wywołaj go z destruktora, aby uniknąć duplikowania kodu.

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

Jeśli kod wykorzystujący typ nie wywołuje destruktora, Moduł wyrzucania elementów bezużytecznych ostatecznie zwolni wszystkie zarządzane zasoby.

Obecność destruktora nie sugeruje obecności finalizatora. Jednak obecność finalizatora oznacza, że należy zdefiniować destruktor i wywołać finalizator z tego destruktora. Zapewnia to jednoznaczne wydawanie niezarządzanych zasobów.

Wywoływanie destruktora zostanie pominięte — przy użyciu <xref:System.GC.SuppressFinalize%2A>— finalizowanie obiektu. Jeśli destruktor nie jest wywoływany, finalizator typu będzie ostatecznie wywoływany przez moduł wyrzucania elementów bezużytecznych.

Jednoznaczne czyszczenie zasobów obiektu przez wywołanie destruktora może poprawić wydajność w porównaniu z umożliwieniem niedeterministycznemu zapełnieniu obiektu przez środowisko CLR.

Kod Zapisano w wizualizacji C++ i skompilowany przy użyciu **/CLR** uruchamia destruktor typu, jeśli:

- Obiekt, który jest tworzony przy użyciu semantyki stosu, wykracza poza zakres. Aby uzyskać więcej informacji, zobacz [ C++ semantyka stosu dla typów referencyjnych](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Wyjątek jest zgłaszany podczas konstruowania obiektu.

- Obiekt jest członkiem w obiekcie, którego destruktor jest uruchomiony.

- Należy wywołać operator [delete](../cpp/delete-operator-cpp.md) w dojściu ([uchwyt do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Użytkownik jawnie wywołuje destruktor.

Jeśli typ jest zużywany przez klienta, który jest zapisywany w innym języku, destruktor jest wywoływany w następujący sposób:

- W wywołaniu <xref:System.IDisposable.Dispose%2A>.

- W wywołaniu `Dispose(void)` typu.

- Jeśli typ wykracza poza zakres w instrukcji C# `using`.

Jeśli utworzysz obiekt typu referencyjnego na stercie zarządzanym (nie korzystasz z semantyki stosu dla typów referencyjnych), użyj składni [try-finally](../cpp/try-finally-statement.md) , aby upewnić się, że wyjątek nie uniemożliwia uruchomienia destruktora.

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

Jeśli typ ma destruktor, kompilator generuje metodę `Dispose` implementującą <xref:System.IDisposable>. Jeśli typ, który jest pisany w wizualizacji C++ i ma destruktor, który jest używany z innego języka, wywoływanie `IDisposable::Dispose` w tym typie powoduje wywołanie destruktora typu. Gdy typ jest używany przez klienta wizualnego C++ , nie można bezpośrednio wywołać `Dispose`; Zamiast tego należy wywołać destruktor przy użyciu operatora `delete`.

Jeśli typ ma finalizator, kompilator generuje metodę `Finalize(void)`, która zastąpi <xref:System.Object.Finalize%2A>.

Jeśli typ ma finalizator lub destruktor, kompilator generuje metodę `Dispose(bool)`, zgodnie ze wzorcem projektu. (Aby uzyskać więcej informacji, zobacz artykuł usuwanie [wzorców](/dotnet/standard/design-guidelines/dispose-pattern)). Nie można jawnie utworzyć lub wywołać `Dispose(bool)` w wizualizacji C++.

Jeśli typ ma klasę bazową, która jest zgodna ze wzorcem projektu, destruktory dla wszystkich klas podstawowych są wywoływane, gdy wywoływana jest destruktor klasy pochodnej. (Jeśli typ jest pisany w wizualizacji C++, kompilator zapewnia, że typy implementują ten wzorzec). Innymi słowy, destruktor klasy referencyjnej łańcuchuje do jej baz i elementów członkowskich określonych przez C++ Standard — najpierw jest uruchamiany destruktor klasy, a następnie destruktory dla swoich elementów członkowskich w odwrocie do kolejności, w której zostały zbudowane, a wreszcie destruktory dla klas bazowych w odwrocie do kolejności, w której zostały zbudowane.

Destruktory i finalizatory nie są dozwolone wewnątrz typów wartości lub interfejsów.

Finalizator może być zdefiniowany lub zadeklarowany tylko w typie referencyjnym. Podobnie jak Konstruktor i destruktor, finalizator nie ma zwracanego typu.

Po uruchomieniu finalizatora obiektu finalizatory w każdej klasie bazowej są również wywoływane, zaczynając od najmniej typu pochodnego. Finalizatory elementów członkowskich danych nie są automatycznie łańcuchowe przez finalizator klasy.

Jeśli finalizator usuwa wskaźnik natywny w typie zarządzanym, należy się upewnić, że odwołania do lub przez wskaźnik natywny nie są przedwcześnie zbierane; Wywołaj destruktor w typie zarządzanym zamiast używać <xref:System.GC.KeepAlive%2A>.

W czasie kompilacji można wykryć, czy typ ma finalizator lub destruktor. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Następny przykład przedstawia dwa typy, jeden, który ma niezarządzane zasoby i jeden, który ma zarządzane zasoby, które są w sposób jednoznaczny wystawione.

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
