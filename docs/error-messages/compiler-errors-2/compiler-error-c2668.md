---
title: Błąd kompilatora C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: 1920af8873578c63ab768dae4bcdf4d91fe7cd57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164816"
---
# <a name="compiler-error-c2668"></a>Błąd kompilatora C2668

'Funkcja': niejednoznaczne wywołanie przeciążonej funkcji

Nie można rozpoznać wywołania określonej przeciążonej funkcji. Można jawnie rzutowane co najmniej jeden z parametrów rzeczywistych.

Ten błąd można także uzyskać za pomocą szablonu. W przypadku, w tej samej klasie funkcja regularny członek i oparte na szablonach składowa o tej samej sygnaturze, oparte na szablonach jeden musi umieszczone jako pierwsze. To ograniczenie bieżąca implementacja języka Visual C++.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2668:

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>Przykład

Innym sposobem, aby rozwiązać ten problem jest [użycie — deklaracja](../../cpp/using-declaration.md):

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>Przykład

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: niejednoznaczne konwersję na rzutowanie stała 0.

Konwersja na rzutowanie za pomocą stała 0 jest niejednoznaczny, ponieważ int wymaga konwersji zarówno do czasu i typ void *. Aby rozwiązać ten problem, należy rzutować 0, aby dokładnie typ parametru funkcji, który jest używany dla tak, aby konwersji muszą mieć miejsce (ten kod będzie prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET, Visual c++).

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>Przykład

Ten błąd może wystąpić, ponieważ CRT ma teraz zmiennoprzecinkowe i podwójne formularze wszystkich funkcji matematycznych.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>Przykład

Ten błąd może wystąpić, ponieważ pow (int, int) został usunięty z math.h w CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Przykład

Ten kod zakończy się pomyślnie w programie Visual Studio 2015, ale nie powiedzie się w programie Visual Studio 2017 i nowszym z C2668. W programie Visual Studio 2015 kompilator błędnie traktowane listy Inicjalizacja kopiowania na w taki sam sposób, jak regularne Inicjowanie kopiowania; uznaje się jedynie konwertowanie konstruktory przeciążeń z późnym wiązaniem.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```