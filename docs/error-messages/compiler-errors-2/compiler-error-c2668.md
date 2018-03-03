---
title: "C2668 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e45bff3173013e7a26f9682bb10ec4cc1fda9364
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2668"></a>C2668 błąd kompilatora
"Funkcja": niejednoznaczne wywołanie przeciążonej funkcji  
  
 Nie można rozpoznać wywołania określonej przeciążonej funkcji. Można jawnie rzutować co najmniej jeden z parametrów rzeczywistych.  
  
 Ten błąd można również uzyskać za pomocą szablonu. Jeśli w tej samej klasie są funkcją członkowską regularnych i funkcję szablonem elementu członkowskiego o tej samej sygnaturze, co opartego na szablonie muszą pochodzić pierwszy. Jest to ograniczenie bieżąca implementacja Visual C++.  
  
 Zobacz artykuł bazy wiedzy Knowledge Base Q240869, aby uzyskać więcej informacji na częściowe porządkowanie szablonów funkcji.  
  
 Jeśli tworzysz Projekt ATL zawierający obsługi obiektu COM `ISupportErrorInfo`, zobacz artykuł bazy wiedzy Knowledge Base Q243298.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2668:  
  
```  
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
 Inny sposób, aby rozwiązać ten problem dotyczy [za pomocą deklaracji](../../cpp/using-declaration.md):  
  
```  
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
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: niejednoznaczne konwersji na rzutowanie stała 0.  
  
 Konwersja na rzutowanie przy użyciu stałej 0 jest niejednoznaczne, ponieważ int wymaga konwersji zarówno do długo, jak i do void *. Aby rozwiązać ten problem, należy rzutować 0, aby dokładnie typ parametru funkcji, który jest używany dla dzięki czemu ma konwersji musi nastąpić (ten kod będzie prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET Visual C++).  
  
```  
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
 Ten błąd może wystąpić, ponieważ CRT ma teraz zmiennoprzecinkowych i podwójne formularze wszystkich funkcji matematycznych.  
  
```  
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
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>Przykład  
Ten kod powiedzie się w programie Visual Studio 2015, ale nie powiedzie się w programie Visual Studio 2017 i później z C2668. W programie Visual Studio 2015 kompilator błędnego traktowane Inicjalizacja listy kopii na w taki sam sposób jak regularne inicjacja kopii; uważa się jedynie konwertowanie konstruktorów Rozpoznanie przeciążenia. 

```
C++
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