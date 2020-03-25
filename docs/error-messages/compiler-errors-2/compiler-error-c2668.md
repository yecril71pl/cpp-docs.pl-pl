---
title: Błąd kompilatora C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177160"
---
# <a name="compiler-error-c2668"></a>Błąd kompilatora C2668

"Function": niejednoznaczne wywołanie przeciążonej funkcji

Nie można rozpoznać określonego przeciążonego wywołania funkcji. Możesz chcieć jawnie rzutować co najmniej jeden z rzeczywistych parametrów.

Ten błąd można także uzyskać za pomocą szablonu. Jeśli w tej samej klasie istnieje zwykła funkcja członkowska i wbudowana funkcja członkowska o tym samym podpisie, szablon, który musi być wcześniej. Jest to ograniczenie bieżącej implementacji wizualizacji C++.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2668:

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

Innym sposobem na rozwiązanie tego błędu jest [użycie deklaracji using](../../cpp/using-declaration.md):

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

Ten błąd może być również wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio .NET 2003: niejednoznaczna konwersja na rzutowanie stałej 0.

Konwersja na rzutowanie przy użyciu stałej 0 jest niejednoznaczna, ponieważ int wymaga konwersji zarówno na wartość Long, jak i na wartość pustą *. Aby rozwiązać ten problem, należy rzutować 0 do dokładnego typu parametru funkcji, który jest używany przez, aby nie trzeba było przeprowadzać konwersji (kod ten będzie prawidłowy w Visual Studio .NET 2003 i Visual Studio .NET C++

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

Ten błąd może wystąpić, ponieważ CRT ma teraz zmiennoprzecinkowe i podwójne formy wszystkich funkcji matematycznych.

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

Ten błąd może wystąpić, ponieważ pow (int, int) została usunięta z Math. h w CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Przykład

Ten kod działa prawidłowo w programie Visual Studio 2015, ale kończy się niepowodzeniem w programie Visual Studio 2017 lub nowszym z C2668. W programie Visual Studio 2015 kompilator błędnie traktował inicjalizację listy kopiowania w taki sam sposób jak regularne inicjowanie kopiowania; jest on uważany tylko za konwersję konstruktorów w celu rozpoznania przeciążenia.

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
