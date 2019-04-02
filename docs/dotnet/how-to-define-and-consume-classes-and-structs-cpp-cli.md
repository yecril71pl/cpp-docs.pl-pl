---
title: 'Instrukcje: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 090259a4ad6b46eccf66dca6c99b4eb532b7ae5c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774922"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Instrukcje: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)

W tym artykule pokazano, jak definiowanie oraz stosowanie typy odwołań zdefiniowanych przez użytkownika i typów wartości w języku C + +/ interfejsu wiersza polecenia.

##  <a name="BKMK_Contents"></a> Zawartość

[Podczas tworzenia wystąpienia obiektu](#BKMK_Object_instantiation)

[Klasy niejawnie abstrakcyjne](#BKMK_Implicitly_abstract_classes)

[Widoczność typów](#BKMK_Type_visibility)

[Element członkowski wglądu](#BKMK_Member_visibility)

[Macierzystych klas publicznych i prywatnych](#BKMK_Public_and_private_native_classes)

[Konstruktory statyczne](#BKMK_Static_constructors)

[Semantyka wskaźnika](#BKMK_Semantics_of_the_this_pointer)

[Funkcje ukrywania podpisu](#BKMK_Hide_by_signature_functions)

[Kopiowanie konstruktorów](#BKMK_Copy_constructors)

[Destruktory i finalizatory](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a> Podczas tworzenia wystąpienia obiektu

Tylko można utworzyć wystąpienia typu odwołanie (ref), w zarządzanym stosie, nie na stosie lub do natywnej sterty. Typy wartości mogą być utworzone na stosie lub zarządzanego stosu.

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

##  <a name="BKMK_Implicitly_abstract_classes"></a> Klasy niejawnie abstrakcyjne

*Niejawnie abstrakcyjne klasy* nie można utworzyć wystąpienia. Klasa jest niejawnie abstrakcyjne, jeśli typ podstawowy tej klasy jest interfejsem, a klasa nie obsługuje wszystkie funkcje składowe interfejsu.

Jeśli nie jest możliwe do konstruowania obiektów z klasy, który pochodzi z interfejsu, przyczyną może być, że klasa jest niejawnie abstrakcyjne. Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [abstrakcyjne](../extensions/abstract-cpp-component-extensions.md).

Poniższy przykład kodu pokazuje, że `MyClass` klasy nie można utworzyć wystąpienia, ponieważ funkcja `MyClass::func2` nie jest zaimplementowana. Aby włączyć przykładu tak, aby skompilować, usuń znaczniki komentarza `MyClass::func2`.

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

##  <a name="BKMK_Type_visibility"></a> Widoczność typów

Można kontrolować widoczność typowych języka wspólnego (CLR), tak, że jeśli zestawu odwołuje się do typów w zestawie może być widoczny lub nie jest widoczny spoza zestawu.

`public` Wskazuje, że typ jest widoczny dla dowolnego pliku źródłowego, który zawiera `#using` dyrektywy dla zestawu, który zawiera tekst.  `private` Wskazuje, że typ jest widoczny dla plików źródłowych, które zawierają `#using` dyrektywy dla zestawu, który zawiera tekst. Typy prywatne będą jednak widoczne w ramach tego samego zestawu. Domyślnie jest widoczność dla klasy `private`.

Domyślnie przed Visual C++ 2005 typy natywne miał powszechnej dostępności spoza zestawu. Włącz [ostrzeżenie kompilatora (poziom 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) ułatwiające możesz zobaczyć, gdzie prywatnej typy natywne są używane niepoprawnie. Użyj [make_public](../preprocessor/make-public.md) pragma, aby zapewnić dostęp publiczny do typu natywnego w pliku kodu źródłowego, który nie można zmodyfikować.

Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).

Poniższy przykład pokazuje sposób deklarowania typów i określić ich dostępność i następnie uzyskać dostęp do tych typów w zestawie. Oczywiście, jeśli zestaw, który ma typy prywatnych jest wywoływany przy użyciu `#using`tylko typy publiczne w zestawie są widoczne.

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

Teraz sklonujemy Nadpisz poprzedni przykład tak, aby go jest kompilowany jako biblioteka DLL.

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

Następny przykład pokazuje, jak uzyskiwać dostęp do typów spoza zestawu. W tym przykładzie klient używa składnika, która jest wbudowana w poprzednim przykładzie.

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

##  <a name="BKMK_Member_visibility"></a> Element członkowski wglądu

Możesz wprowadzić dostępu do składowej klasy publiczne z w obrębie tego samego zestawu inny niż dostęp do niego z spoza zestawu, za pomocą pary specyfikatory dostępu `public`, `protected`, i `private`

Ta tabela zawiera podsumowanie wpływu różnych specyfikatory dostępu:

|Specyfikator|Efekt|
|---------------|------------|
|public|Element członkowski jest dostępny i spoza zestawu.  Zobacz [publicznych](../cpp/public-cpp.md) Aby uzyskać więcej informacji.|
|prywatna|Element członkowski jest niedostępny, wewnątrz ani spoza zestawu.  Zobacz [prywatnej](../cpp/private-cpp.md) Aby uzyskać więcej informacji.|
|protected|Element członkowski jest dostępny, wewnątrz lub na spoza zestawu, ale tylko dla typów pochodnych.  Zobacz [chronione](../cpp/protected-cpp.md) Aby uzyskać więcej informacji.|
|internal|Element członkowski jest publiczna w zestawie, ale prywatnej spoza zestawu.  `internal` jest kontekstowej słowem kluczowym.  Aby uzyskać więcej informacji, zobacz [Context-Sensitive Keywords](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|publiczne chronionych - lub - chronione publiczne|Element członkowski jest publiczna w zestawie, którzy są chronieni spoza zestawu.|
|prywatne prywatnych chronionych - lub - chronionych|Element członkowski jest chroniony wewnątrz zestawu, ale prywatnej spoza zestawu.|

Poniższy przykład pokazuje publiczny typ, który ma elementy członkowskie, które są zadeklarowane za pomocą różnych możliwości dostępu i pokazuje, uzyskiwanie dostępu do tych członków z wewnątrz zestawu.

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

Teraz Utwórzmy poprzedniemu jako biblioteki DLL.

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

Poniższy przykład wykorzystuje składnik, który zostanie utworzony w poprzednim przykładzie, a tym samym pokazuje, jak dostęp do członków z spoza zestawu.

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

##  <a name="BKMK_Public_and_private_native_classes"></a> Macierzystych klas publicznych i prywatnych

Typ natywny mogą być przywoływane z typu zarządzanego.  Na przykład funkcja w typ zarządzany może potrwać parametr, którego typ jest strukturą natywnych.  Jeśli typu zarządzanego i funkcja znajdują się publiczny w zestawie, następnie typ natywny również musi być publiczny.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Następnie utwórz plik kodu źródłowego, który wykorzystuje typ macierzysty:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Teraz można skompilować klienta:

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

##  <a name="BKMK_Static_constructors"></a> Konstruktory statyczne

Typ CLR — na przykład, klasie lub strukturze — może mieć Konstruktor statyczny, który może służyć do zainicjowania elementów członkowskich danych statycznych.  Statyczny Konstruktor jest wywoływana co najwyżej jeden raz i jest wywoływana przed dowolnego członka statycznego o typie odbywa się po raz pierwszy.

Konstruktor wystąpienia jest zawsze uruchamiany po Konstruktor statyczny.

Kompilator nie wbudowanego wywołanie konstruktora, jeśli klasa ma Konstruktor statyczny.  Kompilator nie tekście wywołania do żadnej funkcji składowej, jeśli klasa jest typem wartości, ma statyczny Konstruktor i nie ma konstruktora wystąpienia.  Środowisko CLR może być wbudowany wywołanie, ale nie kompilator.

Umożliwia definiowanie statycznego konstruktora jako funkcja prywatnego elementu członkowskiego, ponieważ oznaczało to ma zostać wywołana tylko przez środowisko CLR.

Aby uzyskać więcej informacji na temat konstruktorów statycznych, zobacz [jak: Definiowanie statycznego konstruktora interfejsu (C + +/ CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

##  <a name="BKMK_Semantics_of_the_this_pointer"></a> Semantyka wskaźnika

Kiedy używasz języka Visual C++ do definiowania typów, `this` wskaźnika w typ odwołania jest typu "uchwytu". `this` Wskaźnika w typ wartości jest typu "wskaźnika wewnętrznego".

Te różne semantykę `this` wskaźnika może spowodować nieoczekiwane zachowanie podczas nosi nazwę indeksatora domyślne. W kolejnym przykładzie pokazano poprawny sposób dostęp do indeksatora domyślne, zarówno w przypadku typu referencyjnego, jak i typu wartości.

Aby uzyskać więcej informacji, zobacz artykuł

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

##  <a name="BKMK_Hide_by_signature_functions"></a> Funkcje ukrywania podpisu

W standardzie języka C++ funkcja w klasie bazowej jest ukryty przez funkcję, która ma taką samą nazwę w klasie pochodnej, nawet jeśli funkcja klasy pochodnej ma ten sam numer i typ parametrów. Jest to określane jako *Ukryj według nazwy* semantyki. W typem odwołania funkcji w klasie bazowej można tylko ukryte przez funkcję w klasie pochodnej, jeśli zarówno nazwę, jak i listy parametrów są takie same. Jest to nazywane *ukryte przez podpis* semantyki.

Klasa jest uznawany za klasy ukrywania podpisu, gdy wszystkie jego funkcje są oznaczone w metadanych jako `hidebysig`. Domyślnie wszystkie klasy, które zostały utworzone na podstawie **/CLR** mają `hidebysig` funkcji. Jeśli klasa ma `hidebysig` funkcje, kompilator nie ukrywa funkcje według nazwy w żadnych bezpośrednich klas bazowych, ale jeśli kompilator napotka Ukryj według nazwy klasy w łańcuch dziedziczenia, będzie nadal tego zachowania Ukryj według nazwy.

W obszarze semantyki ukryte przez podpis gdy funkcja jest wywoływana dla obiektu, kompilator identyfikuje najbardziej pochodnej klasy, która zawiera funkcję, która może spełnić wywołania funkcji. Jeśli istnieje tylko jedna funkcja w klasie, która może spełnić wywołanie, kompilator wywołuje tę funkcję. Jeśli istnieje więcej niż jedna funkcja w klasie, która może spełnić wywołanie, używa kompilatora przeciążenia reguł rozwiązywania, aby określić, które funkcja do wywołania. Aby uzyskać więcej informacji o regułach przeciążenia, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

Wywołania danej funkcji funkcja w klasie bazowej może być podpisu, który sprawia, że nieco lepsze dopasowane niż funkcja w klasie pochodnej. Jednakże jeśli funkcja została jawnie wywołana dla obiektu klasy pochodnej, funkcja w klasie pochodnej jest wywoływana.

Ponieważ wartość zwracana nie jest uznawana za część podpisu funkcji, funkcji klasy podstawowej jest ukryte, jeśli ma taką samą nazwę i przyjmuje tej samej liczby i typu argumentów jako funkcja klasy pochodnej, nawet jeśli różni się w typie wartości zwracanej.

Poniższy przykład pokazuje, że funkcja w klasie bazowej nie jest ukryty przez funkcję w klasie pochodnej.

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

Następny przykład pokazuje, że kompilator języka Visual C++ wywołuje funkcję w klasie pochodnej najbardziej — nawet jeśli konwersja jest wymagany do dopasowania jednego lub więcej parametrów — i nie wywołać funkcję w klasie bazowej, która ma lepsze dopasowanie na wywołanie funkcji.

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

Poniższy przykład pokazuje, że może się zdarzyć ukryć funkcji, nawet jeśli klasa bazowa ma taką samą sygnaturę jak klasy pochodnej.

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

##  <a name="BKMK_Copy_constructors"></a> Kopiowanie konstruktorów

C++ standard mówi, że Konstruktor kopiujący jest wywoływana, gdy obiekt zostanie przeniesiony, taki sposób, że obiekt jest tworzona i niszczona w ten sam adres.

Jednak gdy **/CLR** służy do kompilacji i funkcję, która jest skompilowane do MSIL wywołania funkcji macierzystej, gdzie klasy natywnej — lub więcej niż jedną — jest przekazywany przez wartość i gdzie natywnych klasa ma Konstruktor kopiujący i/lub destruktor, nie Kopiuj Konstruktor jest wywoływany i że obiekt jest niszczony na inny adres, od której został utworzony. Może to powodować problemy, jeśli klasa zawiera wskaźnik do tego samego lub kod służy do śledzenia obiektów przy użyciu adresu.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

W poniższym przykładzie pokazano, gdy Konstruktor kopiujący nie jest generowany.

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

##  <a name="BKMK_Destructors_and_finalizers"></a> Destruktory i finalizatory

Destruktory w typ referencyjny wykonać deterministyczne Oczyszczanie zasobów. Finalizatory wyczyścić niezarządzane zasoby i może być wywoływana sposób deterministyczny, przez destruktor lub w sposób niedeterministyczny przez moduł odśmiecania pamięci. Aby uzyskać informacji dotyczących destruktorów w standardzie języka C++, zobacz [destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Działanie destruktory w klasie zarządzanej Visual C++ różni się od zarządzanych rozszerzeń języka C++. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [zmiany w semantyce destruktora](../dotnet/changes-in-destructor-semantics.md).

Moduł odśmiecania pamięci CLR spowoduje usunięcie nieużywanych zarządzanych obiektów i zwalnia pamięć ich, gdy nie są już wymagane. Jednak typem może używać zasobów, które moduł odśmiecania pamięci nie wie jak zwolnić. Te zasoby są znane jako zasoby niezarządzane (natywne uchwyty plików, na przykład). Firma Microsoft zaleca zwolnieniu wszystkich zasobów niezarządzanych w finalizatora. Ponieważ zarządzane zasoby są wydawane w sposób niedeterministyczny przez moduł odśmiecania pamięci, nie jest bezpieczny do odwoływania się do zasobów zarządzanych w finalizator ponieważ możliwe jest, że moduł odśmiecania pamięci ma już wyczyszczone zarządzanego zasobu.

Finalizator Visual C++ nie jest taka sama jak <xref:System.Object.Finalize%2A> metody. (Dokumentacja CLR używa finalizator i <xref:System.Object.Finalize%2A> metoda synonimów). <xref:System.Object.Finalize%2A> Metoda jest wywoływana przez moduł odśmiecania pamięci, które wywołuje każdego finalizatora w łańcuchu dziedziczenia klasy. W przeciwieństwie do języka Visual C++ destruktory wywołanie finalizatory klasy pochodnej nie powoduje kompilator, aby wywołać finalizatora w klasach bazowych, wszystkie.

Ponieważ kompilator języka Visual C++ obsługuje deterministyczne zwolnienia zasobów, nie należy próbować wdrożyć <xref:System.IDisposable.Dispose%2A> lub <xref:System.Object.Finalize%2A> metody. Jeśli jesteś zaznajomiony z tych metod, w tym miejscu jest jednak sposób mapowania finalizator Visual C++ i destruktor, który wywołuje finalizator na <xref:System.IDisposable.Dispose%2A> wzorca:

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

Typ zarządzany może również użyć zarządzanych zasobów, które chcesz użyć do wersji w sposób deterministyczny, a nie pozostaw moduł odśmiecania pamięci, aby zwolnić niedeterministyczny w pewnym momencie po obiektu nie jest już wymagany. Deterministycznego zwalniania zasobów może znacznie poprawić wydajność.

Kompilator języka Visual C++ umożliwia definicji destruktora w sposób deterministyczny czyszczenie obiektów. Użyj destruktor, aby zwolnić wszystkie zasoby, które chcesz zwolnić w sposób deterministyczny.  Jeśli ma finalizator, należy wywołać go z destruktora, aby uniknąć zduplikowania kodu.

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

Jeśli kod, który wykorzystuje danego typu, nie wywołuje destruktor, moduł zbierający elementy bezużyteczne po pewnym czasie zwalnia wszystkie zasoby zarządzane.

Obecność destruktor nie oznacza obecność finalizatora. Jednak obecność finalizator oznacza należy zdefiniować destruktor i wywoływać finalizator z tym destruktora. Zapewnia to deterministycznego zwalniania niezarządzanych zasobów.

Pomija wywołanie destruktora — za pomocą <xref:System.GC.SuppressFinalize%2A>— finalizacja obiektu. Jeśli destruktor nie jest wywoływana, danego typu finalizator ostatecznie zostanie wywołana przez moduł odśmiecania pamięci.

Sposób deterministyczny Oczyszczanie zasobów obiektu przez wywołanie destruktora może poprawić wydajność w porównaniu z informacją o CLR, w sposób niedeterministyczny finalize obiektu.

Kod, który został napisany w języku Visual C++ i kompilowany przy użyciu **/CLR** typu destruktor jest wykonywany, gdy:

- Obiekt, który jest tworzony przy użyciu semantyka stosu wykracza poza zakres. Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów odwołań](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Wyjątek jest generowany podczas konstruowania obiektu.

- Obiekt jest elementem członkowskim w obiekcie, którego destruktor jest uruchomiona.

- Należy wywołać [Usuń](../cpp/delete-operator-cpp.md) operator uchwyt ([Operator uchwytu do obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Jawnie wywołać destruktor.

Jeśli danego typu zużywanych przez klienta, który jest zapisywany w innym języku, destruktor jest wywoływany w następujący sposób:

- W wywołaniu <xref:System.IDisposable.Dispose%2A>.

- W wywołaniu `Dispose(void)` w typie.

- Jeśli typ wykracza poza zakres w języku C# `using` instrukcji.

Jeśli tworzysz obiekt typu odwołania na stosie zarządzanym (bez użycia semantyka stosu dla typów odwołania), użyj [try-finally](../cpp/try-finally-statement.md) składni, aby upewnić się, że wyjątek nie uniemożliwia destruktor uruchamianie.

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

Jeśli danego typu ma destruktora, kompilator generuje `Dispose` metody, która implementuje <xref:System.IDisposable>. Jeśli typ, który jest napisany w języku Visual C++, a ma destruktor, który jest używany z innego języka, wywołanie `IDisposable::Dispose` tego typu powoduje, że typ destruktora wywoływany. Gdy typ jest używany z klienta programu Visual C++, nie można bezpośrednio wywołać `Dispose`; zamiast tego należy wywołać destruktor przy użyciu `delete` operatora.

Jeśli danego typu ma finalizator, kompilator generuje `Finalize(void)` metodę, która zastępuje <xref:System.Object.Finalize%2A>.

Jeśli typ ma finalizator lub destruktor, kompilator generuje `Dispose(bool)` metoda zgodnie ze wzorca projektowego. (Aby uzyskać informacje, zobacz [wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). Nie można jawnie tworzyć lub wywołać `Dispose(bool)` w programie Visual C++.

Jeśli typ ma klasę bazową, który jest zgodny ze wzorca projektowego, destruktory dla wszystkich klas bazowych są wywoływane, gdy destruktor klasy pochodnej jest wywoływana. (Jeśli Twój typ został napisany w języku Visual C++, kompilator zapewnia, że Twoje typy implementacji tego wzorca.) Innymi słowy, destruktor klasy odniesienia tworzy powiązanie jej baz i elementów członkowskich określonych przez C++ standard — pierwszy destruktor klasy jest przebieg, a następnie destruktory dla jego elementów członkowskich w odwrotnej kolejności, w której zostały skonstruowane, a na koniec destruktory dla jej klasy bazowe w odwrotnej kolejności, w której zostały skonstruowane.

Destruktory i finalizatory są niedozwolone w typach wartości lub interfejsów.

Finalizator może być tylko zdefiniowane lub zostało zadeklarowane w typie odwołania. Podobnie jak Konstruktor i destruktor finalizator nie ma zwracanego typu.

Po uruchomieniu finalizatora obiektu finalizatory w żadnych klas bazowych są również nazywane, począwszy od najmniej pochodnego typu. Finalizatory składowych danych są nie automatycznie powiązane łańcuchem zależności według finalizatory klasy.

Jeśli finalizator usunie wskaźnik natywny w typ zarządzany, upewnij się, czy odwołania lub za pośrednictwem wskaźnik natywny nie są zbierane przedwcześnie; wywołać destruktor dla typu zarządzanego zamiast <xref:System.GC.KeepAlive%2A>.

W czasie kompilacji można wykryć, czy typ ma finalizator lub destruktor. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Następny przykład zawiera dwa typy: taki, który ma zasoby niezarządzane, a taki, który ma zarządzane zasoby, które są dostępne w sposób deterministyczny.

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

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
