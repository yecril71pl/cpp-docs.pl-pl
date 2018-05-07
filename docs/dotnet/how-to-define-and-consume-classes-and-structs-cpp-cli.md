---
title: 'Porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8356d96b0193566814c0d52173a03a3a79d08d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)
W tym artykule przedstawiono sposób Definiowanie oraz stosowanie typy odwołań zdefiniowanych przez użytkownika i typów wartości w języku C + +/ CLI.  
  
##  <a name="BKMK_Contents"></a> Zawartość  
 [Podczas tworzenia wystąpienia obiektu](#BKMK_Object_instantiation)  
  
 [Klasy niejawnie abstrakcyjne](#BKMK_Implicitly_abstract_classes)  
  
 [Widoczność typów](#BKMK_Type_visibility)  
  
 [Widoczność członków](#BKMK_Member_visibility)  
  
 [Publiczne i prywatne klasach macierzystych](#BKMK_Public_and_private_native_classes)  
  
 [Konstruktory statyczne](#BKMK_Static_constructors)  
  
 [Semantyka wskaźnika](#BKMK_Semantics_of_the_this_pointer)  
  
 [Funkcje ukrywania podpisu](#BKMK_Hide_by_signature_functions)  
  
 [Kopiowanie konstruktorów](#BKMK_Copy_constructors)  
  
 [Destruktory i finalizatory](#BKMK_Destructors_and_finalizers)  
  
##  <a name="BKMK_Object_instantiation"></a> Podczas tworzenia wystąpienia obiektu  
 Typy odwołań (ref) i typy wartości tylko można wdrożyć na stercie zarządzanej, nie na stosie lub w stercie natywnej.  
  
```  
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
 *Niejawnie abstrakcyjne klasy* nie można utworzyć wystąpienia. Klasa jest niejawnie abstrakcyjne, jeśli podstawowy typ klasy jest interfejsem, a klasa nie implementuje wszystkich funkcji Członkowskich interfejsu.  
  
 Jeśli nie można utworzyć obiektów z klasy, która jest pochodną interfejsu, przyczyną może być że klasa jest niejawnie abstrakcyjne. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstrakcyjny](../windows/abstract-cpp-component-extensions.md).  
  
 Poniższy przykład kodu pokazuje, że `MyClass` klasy nie można utworzyć wystąpienia, ponieważ funkcja `MyClass::func2` nie jest zaimplementowana. Aby włączyć w przykładzie skompilować, usuń znaczniki komentarza `MyClass::func2`.  
  
```  
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
 Widoczność typowych języka wspólnego (CLR) można kontrolować, aby umożliwić, jeśli odwołuje się do zestawu, typów w zestawie widoczne lub nie jest widoczny spoza zestawu.  
  
 `public` Wskazuje, że typ jest widoczne dla każdego pliku źródłowego, który zawiera `#using` dyrektywy dla zestawu zawierającego typ.  `private` Wskazuje, że typ nie jest widoczny dla plików źródłowych, które zawierają `#using` dyrektywy dla zestawu zawierającego typ. Typy prywatne będą jednak widoczne w tym samym zestawie. Domyślnie jest widoczności dla klasy `private`.  
  
 Domyślnie przed Visual C++ 2005 natywnych typów miał powszechnej dostępności poza zestaw. Włącz [C4692 ostrzeżenie kompilatora (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) aby zobaczyć, których prywatnej natywnych typów są używane nieprawidłowo. Użyj [make_public](../preprocessor/make-public.md) pragma zapewnienie dostępności publicznych typu macierzystego w pliku kodu źródłowego, który nie można modyfikować.  
  
 Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).  
  
 Poniższy przykład przedstawia sposób deklaruj typy i określić ich dostępności, a dostęp do tych typów w zestawie. Oczywiście jeśli odwołuje się do zestawu, który ma prywatnych typów przy użyciu `#using`tylko typy publiczne w zestawie są widoczne.  
  
```  
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
  
 **Output**  
  
```Output  
in Public_Class  
in Private_Class  
in Private_Class_2  
```  
  
 Teraz załóżmy przepisywania powyższego przykładu tak, że jest ona wbudowana jako biblioteki DLL.  
  
```  
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
  
 Następna próbka pokazano, jak dostęp do tych typów poza zestaw. W tym przykładzie klient zużywa składnik, który jest utworzony w poprzednim przykładzie.  
  
```  
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
  
 **Output**  
  
```Output  
in Public_Class  
```  
  
##  <a name="BKMK_Member_visibility"></a> Widoczność członków  
 Umożliwia dostęp do elementu członkowskiego klasy z publicznych w ramach tego samego zestawu inne niż dostępu z nim poza zestaw przy użyciu pary specyfikatory dostępu `public`, `protected`, i `private`  
  
 Ta tabela zawiera podsumowanie wpływ różne specyfikatory dostępu:  
  
|Specyfikator|Efekt|  
|---------------|------------|  
|public|Element członkowski jest dostępny i spoza zestawu.  Zobacz [publicznego](../cpp/public-cpp.md) Aby uzyskać więcej informacji.|  
|private|Element członkowski nie jest dostępny, wewnątrz ani poza zestaw.  Zobacz [prywatnej](../cpp/private-cpp.md) Aby uzyskać więcej informacji.|  
|protected|Element członkowski jest dostępny w i poza zestaw, ale tylko do typów pochodnych.  Zobacz [chronione](../cpp/protected-cpp.md) Aby uzyskać więcej informacji.|  
|internal|Element członkowski jest publiczny w zestawie, ale prywatnej poza zestaw.  `internal` jest słowem kluczowym kontekstowa.  Aby uzyskać więcej informacji, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).|  
|publicznego public chronionych - lub - chronionych|Element członkowski jest publiczny w zestawie, ale chronionych poza zestaw.|  
|prywatne prywatne chronione - lub - chronionych|Element członkowski jest chroniony w zestawie, ale prywatnej poza zestaw.|  
  
 Poniższy przykład pokazuje typu publicznego, który ma elementów członkowskich, które są zadeklarowane z różnych dostępności, a następnie przedstawiono uzyskiwanie dostępu do tych członków z wewnątrz zestawu.  
  
```  
  
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
  
 **Output**  
  
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
  
 Teraz utworzymy powyższego przykładu jako biblioteki DLL.  
  
```  
  
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
  
 Poniższy przykład wykorzystuje składnik, który jest tworzony w poprzednim przykładzie, a tym samym pokazano, jak uzyskać dostępu do członków z poza zestaw.  
  
```  
  
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
  
 **Output**  
  
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
  
##  <a name="BKMK_Public_and_private_native_classes"></a> Publiczne i prywatne klasach macierzystych  
 Typ macierzysty mogą być przywoływane z typu zarządzanego.  Na przykład funkcja w typu zarządzanego może zająć parametr typu natywnego struktury.  Jeśli typ zarządzany i funkcji są publicznie udostępniane w zestawie, typ macierzysty również należy publicznego.  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 Następnie można utworzyć pliku źródła kodu, który wykorzystuje typ macierzysty:  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 Teraz skompilować klienta:  
  
```  
  
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
 Typ CLR — na przykład klasie lub strukturze — może mieć statycznego konstruktora, który może służyć do zainicjowania statyczne elementy członkowskie danych.  Konstruktor statyczny nazywa co najwyżej jeden raz, a jest przed dowolnego statyczny element członkowski typu jest dostępny po raz pierwszy.  
  
 Konstruktor wystąpienia jest zawsze uruchamiany po Konstruktor statyczny.  
  
 Kompilator nie wbudowanego wywołanie konstruktora, jeśli klasa ma Konstruktor statyczny.  Kompilator nie wbudowanego wywołanie funkcji dowolnego elementu członkowskiego, jeśli klasa jest typem wartości, ma statyczny Konstruktor i nie ma konstruktora wystąpienia.  Środowiska CLR może wbudowanego wywołanie, ale nie przez kompilator.  
  
 Definiowanie statycznego konstruktora w funkcji prywatnego elementu członkowskiego, ponieważ ma być wywoływana tylko przez środowisko CLR.  
  
 Aby uzyskać więcej informacji na temat konstruktorów statycznych zobacz [porady: Definiowanie statycznego konstruktora interfejsu (C + +/ CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .  
  
```  
  
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
  
 **Output**  
  
```Output  
in static constructor  
10  
11  
```  
  
##  <a name="BKMK_Semantics_of_the_this_pointer"></a> Semantyka wskaźnika  
 Gdy używasz programu Visual C++ do definiowania typów, `this` wskaźnika typu odniesienia jest typu "uchwytu". `this` Wskaźnika w typie wartości jest typu "wskaźnik wewnętrzny".  
  
 Te semantykę różną od `this` wskaźnika może spowodować nieoczekiwane zachowanie, gdy jest wywoływana indeksatora domyślne. W kolejnym przykładzie pokazano prawidłowego sposobu dostęp indeksatora domyślne, zarówno w przypadku typu ref, jak i typ wartości.  
  
 Aby uzyskać więcej informacji, zobacz artykuł  
  
-   [Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
```  
  
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
  
 **Output**  
  
```Output  
10.89  
10.89  
```  
  
##  <a name="BKMK_Hide_by_signature_functions"></a> Funkcje ukrywania podpisu  
 W języku C++ standardowych funkcji w klasie podstawowej jest ukryty przez funkcję, która ma taką samą nazwę w klasie pochodnej nawet, jeśli funkcja klas pochodnych nie ma tego samego numeru lub rodzaj parametrów. Jest to określane jako *Ukryj według nazwy* semantyki. W typu odwołania funkcji w klasie podstawowej można tylko ukryte przez funkcję w klasie pochodnej Jeśli zarówno nazwę, jak i na liście parametrów są takie same. Jest to nazywane *ukrywania podpisu* semantyki.  
  
 Klasa jest traktowana jako klasa ukrywania podpisu, gdy wszystkie jego funkcje są oznaczone w metadanych jako `hidebysig`. Domyślnie wszystkie klasy, które zostały utworzone na podstawie **/CLR** ma `hidebysig` funkcji. Jeśli klasa zawiera `hidebysig` funkcje, kompilator nie ukrywanie funkcji o nazwie w żadnych bezpośrednich klas podstawowych, ale jeśli kompilator napotka klasę Ukryj według nazwy w łańcuch dziedziczenia, nadal tego zachowania Ukryj według nazwy.  
  
 W obszarze semantyki ukrywania podpisu, gdy funkcja jest wywoływana dla obiektu, kompilator identyfikuje najbardziej pochodnej klasy, która zawiera funkcję, która może spełnić wywołania funkcji. Jeśli istnieje tylko jedna funkcja w klasie spełniających wywołanie, kompilator wywołanie tej funkcji. Jeśli istnieje więcej niż jedna funkcja klasy, która może spełnić wywołanie, używa kompilatora przeciążenia rozpoznawania reguł umożliwiających określenie, które funkcji do wywołania. Aby uzyskać więcej informacji o regułach przeciążenia, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).  
  
 Wywołania funkcji danej funkcji w klasie podstawowej może być podpisie, który umożliwia dopasowanie nieco lepsza niż funkcji w klasie pochodnej. Jednak jeśli funkcja jawnie została wywołana dla obiekt klasy pochodnej, wywołano tę funkcję w klasie pochodnej.  
  
 Ponieważ wartość zwrotna nie jest uważany za część podpisu funkcji, funkcji klasy podstawowej jest ukryte, jeśli ma taką samą nazwę i ma taką samą liczbę i rodzaj argumentów funkcji klas pochodnych, nawet jeśli różni się typ zwracanej wartości.  
  
 Poniższy przykład pokazuje, że funkcja w klasie podstawowej nie jest ukryty przez funkcję w klasie pochodnej.  
  
```  
  
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
  
 **Output**  
  
```Output  
Base::Test  
```  
  
 Następna próbka pokazuje, że kompilator języka Visual C++ wywołuje funkcję w klasie pochodnej najbardziej — nawet wtedy, gdy konwersji jest konieczne dopasowanie co najmniej jeden z parametrów — i nie mogą wywoływać funkcję w klasie podstawowej, będący lepszym dopasowaniem wywołanie funkcji.  
  
```  
  
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
  
 **Output**  
  
```Output  
Derived::Test2  
```  
  
 Poniższy przykład pokazuje, że istnieje możliwość Ukryj funkcję, nawet wtedy, gdy klasa podstawowa ma taką samą sygnaturę jak klasy pochodnej.  
  
```  
  
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
  
 **Output**  
  
```Output  
Derived::Test4  
97  
```  
  
##  <a name="BKMK_Copy_constructors"></a> Kopiowanie konstruktorów  
 C++ standard mówi, że Konstruktor kopiujący jest wywoływana po przeniesieniu obiektu taki sposób, że utworzona i zniszczona na ten sam adres obiektu.  
  
 Jednakże, gdy **/CLR** służy do kompilacji i funkcję, która ma być kompilowana wywołania MSIL natywny działać w przypadku, gdy klasy natywnej — lub więcej niż jedną — jest przekazywany przez wartość i gdzie klasy natywnej ma konstruktora kopiującego i/lub destruktor, nie Kopiuj Konstruktor jest wywoływany i obiekt zostanie zniszczony na inny adres niż której został utworzony. Może to powodować problemy, jeśli klasa zawiera wskaźnik do tego samego lub kod służy do śledzenia obiektów za pomocą adresu.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 W poniższym przykładzie pokazano, gdy Konstruktor kopiujący nie jest generowany.  
  
```  
  
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
  
 **Output**  
  
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
 Destruktory w typ referencyjny wykonać deterministyczne Oczyszczanie zasobów. Finalizatory wyczyścić zasoby niezarządzane i może zostać wywołana sposób niejednoznaczny, destruktor lub niejednoznaczny przez moduł garbage collector. Informacje destruktory w standard C++, zobacz [destruktory](../cpp/destructors-cpp.md).  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 Zachowanie destruktory w klasie zarządzanej Visual C++ różni się od rozszerzeń zarządzanych dla języka C++. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [zmiany w semantyce destruktora](../dotnet/changes-in-destructor-semantics.md).  
  
 Moduł zbierający elementy bezużyteczne CLR Usuwa nieużywane zarządzanych obiektów i zwalnia pamięć ich, gdy nie są już wymagane. Jednak typ może używać zasobów, które moduł garbage collector nie wiadomo, jak do zwolnienia. Te zasoby są określane jako niezarządzane zasoby (natywny plik obsługiwane, na przykład). Firma Microsoft zaleca, aby zwolnić wszystkie zasoby niezarządzane w finalizatora. Ponieważ zasoby zarządzane są wydawane w sposób niedeterministyczny przez moduł garbage collector, nie jest bezpieczne do odwoływania się do zasobów zarządzanych w finalizator ponieważ możliwe jest, że moduł zbierający elementy bezużyteczne ma już wyczyszczone tego zasobu zarządzanego.  
  
 Finalizator Visual C++ nie jest taka sama jak <xref:System.Object.Finalize%2A> metody. (Dokumentacja CLR używa finalizatora i <xref:System.Object.Finalize%2A> metody jako synonim). <xref:System.Object.Finalize%2A> Metoda jest wywoływana przez moduł garbage collector, który wywołuje każdego finalizator w łańcuch dziedziczenia klasy. W odróżnieniu od destruktory Visual C++ wywołania finalizator klasy pochodnej nie powoduje kompilator, aby wywołać finalizatora w wszystkie klasy podstawowe.  
  
 Ponieważ kompilatora Visual C++ obsługuje deterministyczne zwolnienia zasobów, nie należy próbować wdrożyć <xref:System.IDisposable.Dispose%2A> lub <xref:System.Object.Finalize%2A> metody. Jeśli znasz tych metod, w tym miejscu jest jednak sposobu finalizator Visual C++ i destruktor, który wywołuje finalizator mapowania <xref:System.IDisposable.Dispose%2A> wzorca:  
  
```  
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
  
 Typ zarządzany może używać również zarządzane zasoby, które chcesz użyć do wersji w sposób niejednoznaczny, a nie pozostawić do modułu zbierającego elementy bezużyteczne zwolnienia niejednoznaczny w pewnym momencie po obiektu nie jest już wymagane. Deterministyczne zwolnienia zasobów może znacznie poprawić wydajność.  
  
 Kompilator Visual C++ umożliwia definicji — destruktor w sposób niejednoznaczny wyczyścić obiektów. Użyj destruktor, aby zwolnić wszystkie zasoby, które mają zostać wydane w sposób niejednoznaczny.  Jeśli finalizator, należy go wywoływać z destruktor, aby uniknąć zduplikowania kodu.  
  
```  
  
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
  
 Jeśli kod, który wykorzystuje danego typu nie mogą wywoływać destruktor, moduł zbierający elementy bezużyteczne ostatecznie zwalnia wszystkie zasoby zarządzane.  
  
 Obecność destruktor nie oznacza obecności finalizator. Jednak obecności finalizator oznacza to, że użytkownik musi zdefiniowanie destruktora wywołać finalizatora z tym destruktora. Zapewnia to deterministyczne wersji zasoby niezarządzane.  
  
 Wywoływanie destruktor pomija — za pomocą <xref:System.GC.SuppressFinalize%2A>— finalizacji obiektu. Jeśli destruktor nie jest wywoływany, finalizator z typu ostatecznie zostanie wywołana przez moduł garbage collector.  
  
 Sposób niejednoznaczny Oczyszczanie zasobów do obiektu przez wywołanie destruktora może poprawić wydajność w porównaniu z umożliwienie niejednoznaczny finalize obiekt CLR.  
  
 Kod, który został napisany w języku Visual C++ i skompilowanych przy użyciu **/CLR** typu destruktora jest uruchamiany, jeśli:  
  
-   Obiekt, który jest tworzony przy użyciu semantyka stosu wykracza poza zakres. Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów referencyjnych](../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
-   Wyjątek podczas konstruowania obiektu.  
  
-   Obiekt jest elementem członkowskim obiektu, którego destruktora jest uruchomiona.  
  
-   Należy wywołać [usunąć](../cpp/delete-operator-cpp.md) operator uchwyt ([Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)).  
  
-   Jawne wywołania destruktora.  
  
 Jeśli z danym typem jest są używane przez klienta, który jest zapisany w innym języku, destruktor jest wywoływana w następujący sposób:  
  
-   W wywołaniu <xref:System.IDisposable.Dispose%2A>.  
  
-   W wywołaniu `Dispose(void)` w typie.  
  
-   Jeśli typ wykracza poza zakresem w języku C# `using` instrukcji.  
  
 W przypadku utworzenia typu odwołanie do obiektu na stercie zarządzanej (nie używa semantyka stosu dla typów referencyjnych), użyj [try-finally](../cpp/try-finally-statement.md) składni, aby upewnić się, wyjątek nie uniemożliwia destruktor uruchamianie.  
  
```  
  
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
  
 Jeśli z danym typem ma destruktora, kompilator generuje `Dispose` metodę, która implementuje <xref:System.IDisposable>. Jeśli typ, który jest napisany w języku Visual C++ i ma destruktor, który jest używany w innym języku, wywoływania `IDisposable::Dispose` tego typu powoduje, że destruktora typu do wywołania. Jeśli typ jest używany przez klienta programu Visual C++, nie można bezpośrednio wywołać `Dispose`; zamiast tego wywołać destruktor przy użyciu `delete` operatora.  
  
 Jeśli z danym typem ma finalizator, kompilator generuje `Finalize(void)` metodę, która zastępuje <xref:System.Object.Finalize%2A>.  
  
 Jeśli typ ma finalizator lub destruktor, kompilator generuje `Dispose(bool)` metody zgodnie z modelu. (Aby uzyskać informacje, zobacz [wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). Nie można jawnie tworzyć ani wywołać `Dispose(bool)` w programie Visual C++.  
  
 Jeśli typ ma klasy podstawowej, które odpowiada wzorca projektowego, destruktory dla wszystkich klas podstawowych są nazywane wywołanego destruktor w klasie pochodnej. (Jeśli danego typu został napisany w języku Visual C++, kompilator zapewnia, że Twoje typy wdrożenia tego wzorca.) Innymi słowy, destruktor klasy reference powiązany z jej baz i elementów członkowskich określonych przez C++ standard — pierwszy destruktor klasy jest uruchomić, a następnie destruktory dla jego elementów członkowskich w odwrotnej kolejności, w której zostały utworzone, a na końcu destruktory dla jej klasy podstawowe w odwrotnej kolejności, w której zostały utworzone.  
  
 Destruktory i finalizatory są niedozwolone w typach wartości lub interfejsów.  
  
 Finalizator może być tylko zdefiniowane lub zadeklarowana w typie odwołania. Podobnie jak Konstruktor i destruktor finalizator nie ma zwracanego typu.  
  
 Po uruchomieniu finalizatora obiektu finalizatory w dowolnej klasy podstawowe są również nazywane, począwszy od typu najmniej pochodnego. Finalizatory elementów członkowskich danych są nie automatycznie powiązane łańcuchem zależności przez finalizator klasy.  
  
 Jeśli finalizator usuwa wskaźnik natywny w typ zarządzany, należy upewnić się czy odwołania lub za pośrednictwem wskaźnik natywny nie są zbierane przedwcześnie; Wywołaj destruktor na typ zarządzany zamiast <xref:System.GC.KeepAlive%2A>.  
  
 W czasie kompilacji może wykryć, czy typ ma finalizator lub destruktor. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Następna próbka zawiera dwa typy, który ma zasoby niezarządzane i taki, który ma zarządzane zasoby, które są dostępne w sposób niejednoznaczny.  
  
```  
  
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
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)