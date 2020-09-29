---
title: 'Instrukcje: Definiowanie i korzystanie z klas i struktur (C++/CLI)'
description: Jak utworzyć i użyć klasy zdefiniowanej przez użytkownika i typów struktur w kodzie C++/CLI.
ms.date: 09/25/2020
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 17d0885d42febc1d2789c8711b54a76066ee8176
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414584"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Instrukcje: Definiowanie i korzystanie z klas i struktur (C++/CLI)

W tym artykule pokazano, jak definiować i korzystać z typów referencyjnych zdefiniowanych przez użytkownika i typów wartości w języku C++/CLI.

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a> Tworzenie wystąpienia obiektu

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> Klasy abstrakcyjne niejawnie

Nie można utworzyć wystąpienia *niejawnie klasy abstrakcyjnej* . Klasa jest abstrakcyjna niejawnie, gdy:

- podstawowy typ klasy jest interfejsem, a
- Klasa nie implementuje wszystkich funkcji elementów członkowskich interfejsu.

Nie można tworzyć obiektów z klasy, która jest pochodną interfejsu. Przyczyną może być niejawne abstrakcyjność klasy. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstract](../extensions/abstract-cpp-component-extensions.md).

Poniższy przykład kodu pokazuje, że `MyClass` nie można utworzyć wystąpienia klasy, ponieważ funkcja `MyClass::func2` nie jest zaimplementowana. Aby włączyć przykład do kompilowania, Usuń komentarz `MyClass::func2` .

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a> Widoczność typu

Można kontrolować widoczność typów środowiska uruchomieniowego języka wspólnego (CLR). Gdy zestaw jest przywoływany, kontrolujesz, czy typy w zestawie są widoczne, czy nie są widoczne poza zestawem.

`public` wskazuje, że typ jest widoczny dla każdego pliku źródłowego, który zawiera `#using` dyrektywę dla zestawu, który zawiera typ.  `private` wskazuje, że typ nie jest widoczny dla plików źródłowych zawierających `#using` dyrektywę dla zestawu, który zawiera typ. Jednak typy prywatne są widoczne w tym samym zestawie. Domyślnie widoczność klasy to `private` .

Domyślnie przed programem Visual Studio 2005 typy natywne miały publiczny dostęp poza zestawem. Włącz [Ostrzeżenie kompilatora (poziom 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) , aby ułatwić sprawdzenie, gdzie prywatne typy natywne są używane nieprawidłowo. Użyj dyrektywy pragma [make_public](../preprocessor/make-public.md) , aby zapewnić publiczny dostęp do typu natywnego w pliku kodu źródłowego, którego nie można modyfikować.

Aby uzyskać więcej informacji, zobacz [#using dyrektywie](../preprocessor/hash-using-directive-cpp.md).

Poniższy przykład pokazuje, jak zadeklarować typy i określić ich dostępność, a następnie uzyskać dostęp do tych typów wewnątrz zestawu. Jeśli do zestawu, do którego odwołuje się typ prywatny, przywoływane jest użycie `#using` , widoczne są tylko typy publiczne w zestawie.

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a> Widoczność elementów członkowskich

Dostęp do elementu członkowskiego klasy publicznej można uzyskać z poziomu tego samego zestawu innego niż dostęp do niego spoza zestawu przy użyciu par specyfikatorów dostępu **`public`** , **`protected`** i **`private`**

Ta tabela zawiera podsumowanie wpływu różnych specyfikatorów dostępu:

|Specyfikator|Efekt|
|---------------|------------|
|`public`|Element członkowski jest dostępny wewnątrz i na zewnątrz zestawu. Aby uzyskać więcej informacji, zobacz [`public`](../cpp/public-cpp.md).|
|`private`|Składowa jest niedostępna, zarówno wewnątrz, jak i na zewnątrz zestawu.  Aby uzyskać więcej informacji, zobacz [`private`](../cpp/private-cpp.md).|
|`protected`|Składowa jest dostępna wewnątrz i na zewnątrz zestawu, ale tylko dla typów pochodnych. Aby uzyskać więcej informacji, zobacz [`protected`](../cpp/protected-cpp.md).|
|`internal`|Składowa jest publiczna wewnątrz zestawu, ale jest prywatna poza zestawem. `internal` jest kontekstowym słowem kluczowym.  Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|`public protected` oraz `protected public`|Składowa jest publiczna wewnątrz zestawu, ale chroniona poza zestawem.|
|`private protected` oraz `protected private`|Składowa jest chroniona wewnątrz zestawu, ale prywatny poza zestawem.|

Poniższy przykład pokazuje typ publiczny, który ma składowe, które są zadeklarowane przy użyciu różnych specyfikatorów dostępu. Następnie wyświetla dostęp do tych członków z wnętrza zestawu.

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

Poniższy przykład zużywa składnik, który został utworzony w poprzednim przykładzie. Pokazuje, jak uzyskać dostęp do elementów członkowskich spoza zestawu.

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> Publiczne i prywatne klasy natywne

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> Konstruktory statyczne

Typ CLR — na przykład Klasa lub struktura — może mieć Konstruktor statyczny, którego można użyć do zainicjowania statycznych elementów członkowskich danych.  Konstruktor statyczny jest wywoływany najwyżej raz i jest wywoływany przed uzyskaniem dostępu do dowolnego statycznego elementu członkowskiego typu po raz pierwszy.

Konstruktor wystąpienia zawsze jest uruchamiany po konstruktorze statycznym.

Kompilator nie może wykonać wywołania konstruktora, jeśli klasa ma Konstruktor statyczny. Kompilator nie może wbudowana wywołania żadnej funkcji członkowskiej, jeśli klasa jest typem wartości, ma statyczny Konstruktor i nie ma konstruktora wystąpienia. Środowisko CLR może być wbudowane wywołanie, ale kompilator nie może.

Zdefiniuj statyczny Konstruktor jako prywatną funkcję członkowską, ponieważ jest przeznaczony do wywoływania tylko przez środowisko CLR.

Aby uzyskać więcej informacji na temat konstruktorów statycznych, zobacz [How to: define an static Interface konstruktora (C++/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a> Semantyka `this` wskaźnika

Gdy używasz języka C++ \CLI do definiowania typów, **`this`** wskaźnik w typie referencyjnym jest *uchwytem typu dojście*. **`this`** Wskaźnik w typie wartości jest typu *wskaźnika wewnętrznego*.

Te różne semantyki **`this`** wskaźnika mogą spowodować nieoczekiwane zachowanie w przypadku wywołania domyślnego indeksatora. W następnym przykładzie pokazano poprawny sposób dostępu do domyślnego indeksatora zarówno w typie referencyjnym, jak i w typie wartości.

Aby uzyskać więcej informacji, zobacz [uchwyt do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) i [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> Funkcje ukrywania za pomocą podpisu

W standardowym języku C++ funkcja w klasie bazowej jest ukryta przez funkcję, która ma taką samą nazwę w klasie pochodnej, nawet jeśli funkcja klasy pochodnej nie ma tego samego rodzaju lub liczby parametrów. Jest ona znana jako semantyka *ukrycia przez nazwę* . W typie referencyjnym funkcja w klasie bazowej jest tylko ukryta przez funkcję w klasie pochodnej, jeśli zarówno nazwa, jak i lista parametrów są takie same. Jest ona znana jako semantyka *ukrycia przez podpis* .

Klasa jest traktowana jako Klasa ukrywania według podpisu, gdy wszystkie jej funkcje są oznaczone w metadanych jako `hidebysig` . Domyślnie wszystkie klasy, które są tworzone w **`/clr`** programie mają `hidebysig` funkcje. Gdy Klasa ma `hidebysig` funkcje, kompilator nie ukrywa funkcji według nazwy w żadnej bezpośredniej klasie podstawowej, ale jeśli kompilator napotyka klasę ukrycia-by-name w łańcuchu dziedziczenia, kontynuuje działanie ukrywania przez nazwę.

W obszarze semantyka ukrycia po podpisie, gdy funkcja jest wywoływana w obiekcie, kompilator identyfikuje najbardziej pochodną klasę, która zawiera funkcję, która może spełnić wywołanie funkcji. Jeśli istnieje tylko jedna funkcja w klasie, która spełnia wywołanie, kompilator wywołuje tę funkcję. Jeśli w klasie jest więcej niż jedna funkcja, która może spełnić wywołanie, kompilator używa reguł rozpoznawania przeciążenia, aby określić, która funkcja ma być wywoływana. Aby uzyskać więcej informacji na temat reguł przeciążenia, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

Dla danego wywołania funkcji funkcja w klasie bazowej może mieć sygnaturę, która sprawia, że jest nieco lepszym dopasowaniem niż funkcja w klasie pochodnej. Jeśli jednak funkcja została jawnie wywołana dla obiektu klasy pochodnej, wywoływana jest funkcja klasy pochodnej.

Ponieważ wartość zwracana nie jest uważana za część podpisu funkcji, funkcja klasy bazowej jest ukryta, jeśli ma taką samą nazwę i ma ten sam rodzaj i liczbę argumentów jak funkcja klasy pochodnej, nawet jeśli różni się w typie wartości zwracanej.

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

Następny przykład pokazuje, że kompilator języka Microsoft C++ wywołuje funkcję w najbardziej pochodnej klasie — nawet wtedy, gdy konwersja jest wymagana do dopasowania jednego lub kilku parametrów — i nie wywołuje funkcji w klasie bazowej, która jest lepszym dopasowaniem wywołania funkcji.

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a> Kopiuj konstruktory

Standard C++ oznacza, że Konstruktor kopiujący jest wywoływany, gdy obiekt jest przenoszony, w taki sposób, że obiekt jest tworzony i niszczony pod tym samym adresem.

Jeśli jednak funkcja, która jest skompilowana do MSIL wywołuje funkcję natywną, w której Klasa macierzysta lub więcej niż jedna — jest przenoszona przez wartość i gdzie Klasa macierzysta ma Konstruktor kopiujący lub destruktor, Konstruktor kopiujący nie jest wywoływany i obiekt jest niszczony pod innym adresem niż w miejscu, w którym został utworzony. Takie zachowanie może spowodować problemy, jeśli klasa ma wskaźnik do samego siebie lub jeśli kod śledzi obiekty według adresu.

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> Destruktory i finalizatory

Destruktory w typie referencyjnym mają niejednoznaczne czyszczenie zasobów. Finalizatory czyścią niezarządzane zasoby i mogą być wywoływane przez destruktora lub niejednoznaczne przez moduł wyrzucania elementów bezużytecznych. Aby uzyskać informacje o destruktorach w standardowym języku C++, zobacz [destruktory](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Moduł wyrzucania elementów bezużytecznych CLR usuwa nieużywane obiekty zarządzane i zwalnia ich pamięć, gdy nie są już potrzebne. Jednak typ może korzystać z zasobów, które nie wiedzą, jak zwolnić. Te zasoby są znane jako *niezarządzane* zasoby (na przykład natywne uchwyty plików). Zalecamy wydanie wszystkich niezarządzanych zasobów w programie finalizatora. Moduł wyrzucania elementów bezużytecznych zwalnia zarządzane zasoby w sposób niedeterministyczny, dlatego nie można bezpiecznie odwoływać się do zarządzanych zasobów w finalizatorze. Dzieje się tak, ponieważ istnieje możliwość, że moduł zbierający elementy bezużyteczne już je wyczyszczone.

Finalizator Visual C++ nie jest taki sam jak <xref:System.Object.Finalize%2A> Metoda. (Dokumentacja środowiska CLR używa finalizatora i <xref:System.Object.Finalize%2A> metody z synonimem). <xref:System.Object.Finalize%2A>Metoda jest wywoływana przez moduł wyrzucania elementów bezużytecznych, który wywołuje każdy finalizator w łańcuchu dziedziczenia klas. W przeciwieństwie do Visual C++ destruktorów, wywołanie finalizatora klasy pochodnej nie powoduje, że kompilator wywołuje finalizator we wszystkich klasach bazowych.

Ponieważ kompilator języka Microsoft C++ obsługuje deterministyczną wersję zasobów, nie należy próbować zaimplementować <xref:System.IDisposable.Dispose%2A> metod lub <xref:System.Object.Finalize%2A> . Jeśli jednak znasz te metody, poniżej przedstawiono sposób, w jaki Visual C++ finalizator i destruktor wywołujący mapę finalizatora do <xref:System.IDisposable.Dispose%2A> wzorca:

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

Typ zarządzany może również wykorzystywać zarządzane zasoby, które wolisz zwolnić. Nie można chcieć, aby moduł wyrzucania elementów bezużytecznych zwolnił obiekt w pewnym momencie, gdy obiekt nie jest już wymagany. Deterministyczna wersja zasobów może znacząco poprawić wydajność.

Kompilator języka Microsoft C++ umożliwia definiowanie destruktora do niejednoznacznego czyszczenia obiektów. Użyj destruktora, aby zwolnić wszystkie zasoby, które mają być wydane w sposób deterministyczny.  Jeśli jest obecny finalizator, wywołaj go z destruktora, aby uniknąć duplikowania kodu.

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

Jeśli kod, który zużywa typ, nie wywołuje destruktora, Moduł wyrzucania elementów bezużytecznych ostatecznie zwolni wszystkie zarządzane zasoby.

Obecność destruktora nie oznacza obecności finalizatora. Jednak obecność finalizatora oznacza, że należy zdefiniować destruktor i wywołać finalizator z tego destruktora. To wywołanie umożliwia jednoznaczne wydawanie niezarządzanych zasobów.

Wywoływanie destruktora pomijania — przy użyciu <xref:System.GC.SuppressFinalize%2A> — finalizowanie obiektu. Jeśli destruktor nie jest wywoływany, finalizator typu będzie ostatecznie wywoływany przez moduł wyrzucania elementów bezużytecznych.

Aby zwiększyć wydajność, można wywołać destruktor, aby w sposób niejednoznaczny wyczyścić zasoby obiektu, zamiast pozwolić, aby środowisko CLR w sposób niejednoznaczny zakończył obiekt.

Kod, który został zapisany w Visual C++ i skompilowany przy użyciu, **`/clr`** uruchamia destruktor typu, jeśli:

- Obiekt, który jest tworzony przy użyciu semantyki stosu, wykracza poza zakres. Aby uzyskać więcej informacji, zobacz [semantyka stosu języka C++ dla typów referencyjnych](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Wyjątek jest zgłaszany podczas konstruowania obiektu.

- Obiekt jest członkiem w obiekcie, którego destruktor jest uruchomiony.

- Należy wywołać operator [delete](../cpp/delete-operator-cpp.md) w dojściu ([uchwyt do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Użytkownik jawnie wywołuje destruktor.

Jeśli klient, który jest zapisany w innym języku zużywa swój typ, destruktor zostaje wywołany w następujący sposób:

- W wywołaniu <xref:System.IDisposable.Dispose%2A> .

- W wywołaniu `Dispose(void)` typu.

- Jeśli typ wykracza poza zakres w instrukcji języka C# **`using`** .

Jeśli nie korzystasz z semantyki stosu dla typów referencyjnych i utworzysz obiekt typu referencyjnego na stercie zarządzanym, użyj składni [try-finally](../cpp/try-finally-statement.md) , aby upewnić się, że wyjątek nie uniemożliwia uruchomienia destruktora.

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

Jeśli typ ma destruktor, kompilator generuje `Dispose` metodę implementującą <xref:System.IDisposable> . Jeśli typ, który jest pisany w Visual C++ i ma destruktor, który jest używany z innego języka, wywołanie `IDisposable::Dispose` tego typu powoduje wywoływanie destruktora typu. Gdy typ jest używany z klienta Visual C++, nie można bezpośrednio wywołać metody `Dispose` ; zamiast tego należy wywołać destruktor przy użyciu **`delete`** operatora.

Jeśli typ ma finalizator, kompilator generuje `Finalize(void)` metodę, która zastąpi <xref:System.Object.Finalize%2A> .

Jeśli typ ma finalizator lub destruktor, kompilator generuje `Dispose(bool)` metodę, zgodnie ze wzorcem projektu. (Aby uzyskać więcej informacji, zobacz artykuł usuwanie [wzorców](/dotnet/standard/design-guidelines/dispose-pattern)). Nie można jawnie tworzyć ani wywoływać `Dispose(bool)` w Visual C++.

Jeśli typ ma klasę bazową, która jest zgodna ze wzorcem projektu, destruktory dla wszystkich klas podstawowych są wywoływane, gdy wywoływana jest destruktor klasy pochodnej. (Jeśli typ jest zapisywana w Visual C++, kompilator zapewnia, że typy implementują ten wzorzec.) Innymi słowy, destruktor klasy referencyjnej łańcuchuje do jej baz i członków zgodnie z definicją w standardzie C++. Najpierw jest uruchamiany destruktor klasy. Następnie destruktory dla swoich elementów członkowskich są uruchamiane w odwrotnej kolejności, w której zostały skonstruowane. Na koniec destruktory dla jego klas bazowych są uruchamiane w odwrocie od kolejności, w której zostały skonstruowane.

Destruktory i finalizatory nie są dozwolone wewnątrz typów wartości lub interfejsów.

Finalizator może być zdefiniowany lub zadeklarowany tylko w typie referencyjnym. Podobnie jak Konstruktor i destruktor, finalizator nie ma zwracanego typu.

Po uruchomieniu finalizatora obiektu finalizatory w każdej klasie bazowej są również wywoływane, zaczynając od najmniej typu pochodnego. Finalizatory elementów członkowskich danych nie są automatycznie łańcuchowe przez finalizator klasy.

Jeśli finalizator usuwa wskaźnik natywny w typie zarządzanym, należy się upewnić, że odwołania do lub przez wskaźnik natywny nie są przedwcześnie zbierane. Wywołaj destruktor w typie zarządzanym zamiast używać <xref:System.GC.KeepAlive%2A> .

W czasie kompilacji można wykryć, czy typ ma finalizator lub destruktor. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Następny przykład przedstawia dwa typy: jeden, który ma niezarządzane zasoby i jeden, który ma zarządzane zasoby, które są wystawione w sposób deterministyczny.

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

[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
