---
title: 'Porady: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich'
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: 495ceea6afb222d13953b3a25b7a1c836b299de6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216404"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>Porady: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich

W tym artykule pokazano, jak definiować i używać delegatów w języku C++/CLI.

Chociaż .NET Framework udostępnia wiele delegatów, czasami może być konieczne zdefiniowanie nowych delegatów.

Poniższy przykład kodu definiuje delegata o nazwie `MyCallback` . Kod obsługi zdarzeń — funkcja, która jest wywoływana, gdy ten nowy delegat jest uruchamiany — musi mieć typ zwracany **`void`** i mieć <xref:System.String> odwołanie.

Funkcja Main używa metody statycznej zdefiniowanej przez program `SomeClass` w celu utworzenia wystąpienia `MyCallback` obiektu delegowanego. Delegat stanie się alternatywną metodą wywołania tej funkcji, jak pokazano przez wysłanie ciągu "Single" do obiektu delegowanego. Następnie dodatkowe wystąpienia `MyCallback` są połączone ze sobą, a następnie wykonywane przez jedno wywołanie do obiektu delegowanego.

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

Następny przykład kodu pokazuje, jak skojarzyć delegata z elementem członkowskim klasy wartości.

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>Jak redagować delegatów

Można użyć `-` operatora "", aby usunąć delegata składnika z delegata złożonego.

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**Dane wyjściowe**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>Przekaż delegata ^ do funkcji natywnej, która oczekuje wskaźnika funkcji

Za pomocą zarządzanego składnika można wywołać funkcję natywną z parametrami wskaźnika funkcji, gdzie funkcja natywna może wywołać funkcję członkowską delegata zarządzanego składnika.

Ten przykład tworzy plik dll, który eksportuje funkcję natywną:

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

Następny przykład zużywa plik. dll i przekazuje uchwyt delegata do funkcji natywnej, która oczekuje wskaźnika funkcji.

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**Dane wyjściowe**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>Aby skojarzyć delegatów z funkcjami niezarządzanymi

Aby skojarzyć delegata z funkcją natywną, należy otoczyć funkcję natywną w typie zarządzanym i zadeklarować funkcję do wywołania przez `PInvoke` .

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**Dane wyjściowe**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>Aby użyć niezwiązanych delegatów

Możesz użyć niepowiązanego delegata, aby przekazać wystąpienie typu, którego funkcja ma być wywoływana, gdy obiekt delegowany jest wywoływany.

Niepowiązane Delegaty są szczególnie przydatne, jeśli chcesz wykonać iterację obiektów w kolekcji — za pomocą [for each w](../dotnet/for-each-in.md) słowach kluczowych — i wywołaj funkcję członkowską dla każdego wystąpienia.

Poniżej przedstawiono sposób deklarowania, tworzenia wystąpień i powiązania powiązań i niepowiązanych obiektów delegowanych:

|Akcja|Powiązane Delegaty|Niezwiązane obiekty delegowane|
|------------|---------------------|-----------------------|
|Zadeklarować|Podpis delegata musi być zgodny z podpisem funkcji, która ma zostać wywołana przez delegata.|Pierwszy parametr podpisu delegata jest typem **`this`** obiektu, który chcesz wywołać.<br /><br /> Po pierwszym parametrze podpis delegata musi być zgodny z podpisem funkcji, która ma zostać wywołana przez delegata.|
|Tworzenia|Podczas tworzenia wystąpienia powiązanego delegata można określić funkcję wystąpienia lub globalną lub statyczną funkcję członkowską.<br /><br /> Aby określić funkcję wystąpienia, pierwszy parametr jest wystąpieniem typu, którego funkcja członkowska ma być wywoływana, a drugi parametr jest adresem funkcji, która ma zostać wywołana.<br /><br /> Jeśli chcesz wywołać globalną lub statyczną funkcję członkowską, wystarczy przekazać nazwę funkcji globalnej lub nazwę statycznej funkcji członkowskiej.|Podczas tworzenia wystąpienia niepowiązanego delegata wystarczy przekazać adres funkcji, która ma zostać wywołana.|
|Call|Po wywołaniu powiązanego delegata, wystarczy przekazać parametry, które są wymagane przez podpis delegata.|Analogicznie jak powiązany delegat, ale należy pamiętać, że pierwszy parametr musi być wystąpieniem obiektu, który zawiera funkcję, która ma zostać wywołana.|

Ten przykład pokazuje sposób deklarowania, tworzenia wystąpienia i wywołania niezwiązanych delegatów:

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**Dane wyjściowe**

```Output
2
3
2
3
2
7
8
7
8
7
```

Następny przykład pokazuje, jak używać niezwiązanych delegatów i [dla każdego w](../dotnet/for-each-in.md) słowach kluczowych do iteracji przez obiekty w kolekcji i wywoływać funkcję członkowską dla każdego wystąpienia.

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

Ten przykład tworzy niezwiązany delegat do funkcji akcesora właściwości:

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**Dane wyjściowe**

```Output
11
```

Poniższy przykład pokazuje, jak wywołać delegata multiemisji, gdzie jedno wystąpienie jest powiązane i jedno wystąpienie jest niepowiązane.

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**Dane wyjściowe**

```Output
in f(R ^ r)
in f()
```

Następny przykład pokazuje, jak utworzyć i wywołać niezwiązany Delegat ogólny.

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**Dane wyjściowe**

```Output
12
14
```

## <a name="see-also"></a>Zobacz także

[delegate (C++ Component Extensions)](../extensions/delegate-cpp-component-extensions.md)
