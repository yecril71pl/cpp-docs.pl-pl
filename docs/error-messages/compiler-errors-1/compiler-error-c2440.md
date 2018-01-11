---
title: "C2440 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2440
dev_langs: C++
helpviewer_keywords: C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62a83da358738f7892fd5db06fbe775ff0b7d7da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2440"></a>C2440 błąd kompilatora
"konwersji": nie można przekonwertować z "type1" na "type2".  
  
Nie można rzutować kompilator `type1` do `type2`.  
  
## <a name="example"></a>Przykład  
Może być spowodowany C2440, jeśli podjęto próbę zainicjowania z systemem innym niż stała `char*` (lub `wchar_t*`) przy użyciu ciągu literału w kodzie C++ po opcji kompilatora zgodność [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) jest ustawiona. W języku C, typ literału ciągu jest tablica `char`, ale w języku C++ jest tablica `const char`. W tym przykładzie generuje C2440:  
  
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
 C2440 również może być spowodowany, jeśli można przekonwertować wskaźnika do elementu członkowskiego do void *. Następna próbka generuje C2440:  
  
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
 Przy próbie rzutowania z typu, który jest tylko do przodu zadeklarowane, ale nie zdefiniowano, może być również spowodowane C2440. W tym przykładzie generuje C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## <a name="example"></a>Przykład  
 Błędy C2440 w wierszach 15 i 16 Następna próbka jest kwalifikowany za pomocą `Incompatible calling conventions for UDT return value` wiadomości. A *UDT* jest typ zdefiniowany przez użytkownika, takich jak klasy, struktury lub związku. Tego rodzaju błędów niezgodności są spowodowane konwencja wywołania UDT określone w zwracany typ deklaracja przekazująca dalej powoduje konflikt z rzeczywistego Konwencja wywoływania UDT i uczestniczy wskaźnik funkcji.  
  
 W tym przykładzie najpierw istnieją deklaracje do przodu dla struktury i funkcji, która zwraca struktury; Kompilator przyjęto założenie, że struktury używa konwencji wywoływania języka C++. Następnie jest definicji struktury, która domyślnie używa C konwencji wywoływania. Ponieważ kompilator nie ma konwencję wywołania struktury do momentu zakończenia odczytywania całej struktury Konwencja wywoływania dla struktury, w zwracanym typem `get_c2` również zakłada się, że C++.  
  
 Struktura następuje innej deklaracji funkcji, która zwraca struktury, ale w tym momencie kompilator wie, że Konwencja wywoływania struktury jest C++. Podobnie wskaźnik funkcji, która zwraca struktury, jest zdefiniowany po definicji struktury tak, że kompilator wie, że struktury używa konwencji wywoływania języka C++.  
  
 Aby rozwiązać C2440, która występuje z powodu niezgodne Konwencje wywoływania, należy zadeklarować funkcji zwracających UDT po definicji UDT.  
  
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
 C2440 może wystąpić, gdy przypisujesz zera na wskaźnik wewnętrzny:  
  
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
 C2440 może również wystąpić niepoprawne użycie konwersji zdefiniowanej przez użytkownika. Na przykład, gdy operator konwersji została zdefiniowana jako `explicit`, kompilator nie może być używany w niejawnej konwersji. Aby uzyskać więcej informacji na temat konwersje zdefiniowane przez użytkownika, zobacz [konwersje zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). W tym przykładzie generuje C2440:  
  
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
 C2440 może także wystąpić w przypadku próby utworzenia wystąpienia tablicy Visual C++, którego typ jest <xref:System.Array>.  Aby uzyskać więcej informacji, zobacz [tablice](../../windows/arrays-cpp-component-extensions.md).  Następna próbka generuje C2440:  
  
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
 Kompilatora Visual C++ nie umożliwia już [const_cast Operator](../../cpp/const-cast-operator.md) w dół rzutować kiedy źródła kodu, który używa **/CLR** programowania w języku ma być kompilowana.  
  
 Aby rozwiązać ten C2440, użyj operatora rzutowania poprawne. Aby uzyskać więcej informacji, zobacz [operatory rzutowania](../../cpp/casting-operators.md).  
  
 W tym przykładzie generuje C2440:  
  
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
C2440 może wystąpić z powodu zmiany zgodności dla kompilatora w Visual Studio 2015 Update 3. Wcześniej, kompilator niepoprawnie traktowane niektórych różnych wyrażeń jako ten sam typ dopasowania szablonu w celu identyfikacji `static_cast` operacji. Kompilator prawidłowo odróżnia typy i kod, który zależał od poprzedniej `static_cast` zachowanie jest uszkodzona. Aby rozwiązać ten problem, zmień argument szablonu jest zgodny z typem parametru szablonu lub użyj `reinterpret_cast` lub rzutowania w stylu języka C.
  
W tym przykładzie generuje C2440:  
  
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
### <a name="copy-list-initialization"></a>Inicjalizacja listy kopii

Visual Studio 2017 i nowsze poprawnie Zgłoś błędy kompilatora dotyczące tworzenia obiektów przy użyciu listy inicjatorów, które nie zostały przechwycono w programie Visual Studio 2015 i może prowadzić do awarii lub niezdefiniowane zachowanie środowiska wykonawczego. W C ++ 17 kopiowania listy Inicjalizacja kompilator należy wziąć pod uwagę jawny Konstruktor Rozpoznanie przeciążenia, ale musi Zgłoś błąd, jeśli faktycznie jest wybierany tego przeciążenia.

Poniższy przykład tworzy w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 r.

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
  
Aby naprawić błąd, użyj bezpośredniego inicjowania:  
  
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
### <a name="cv-qualifiers-in-class-construction"></a>kwalifikatorów CV konstrukcji klasy

W programie Visual Studio 2015 Kompilator ignoruje czasami niepoprawnie kwalifikatorów cv podczas generowania obiektu klasy za pośrednictwem wywołania konstruktora. To może potencjalnie spowodować awarię lub nieoczekiwane zachowanie. W poniższym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd kompilatora w Visual Studio 2017 i nowszych wersjach:

```cpp
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby naprawić błąd, należy zadeklarować operatora int() jako stała.
