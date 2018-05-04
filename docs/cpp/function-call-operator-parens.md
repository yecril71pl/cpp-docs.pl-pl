---
title: 'Operator wywołania funkcji: () | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb1cdd4ec5dc556f0427914ca8ec746ad3ad2ccc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="function-call-operator-"></a>Operator wywołania funkcji: ()
Wyrażenie przyrostek następuje operator wywołania funkcji **()**, określa wywołania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
postfix-expression   
( [argument-expression-list ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Argumenty operator wywołania funkcji są zero lub więcej wyrażeń oddzielonych przecinkami — rzeczywistych argumentów do funkcji.  
  
 *Wyrażenie przyrostek* musi być adresem funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), i *lista wyrażeń argument* znajduje się lista wyrażeń (oddzielone przecinkami) których wartości (argumenty) są przekazywane do funkcji. *Lista wyrażeń argument* argument może być pusta.  
  
 *Wyrażenie przyrostek* musi mieć jeden z następujących typów:  
  
-   Funkcja zwracająca typ `T`. Przykład deklaracja jest  
  
    ```  
    T func( int i )  
    ```  
  
-   Wskaźnik do funkcji zwracającej typ `T`. Przykład deklaracja jest  
  
    ```  
    T (*func)( int i )  
    ```  
  
-   Odwołanie do funkcji zwracającej typ `T`. Przykład deklaracja jest  
  
    ```  
    T (&func)(int i)  
    ```  
  
-   Funkcja wskaźnik do elementu członkowskiego wyłuskania zwracająca typ `T`. Przykład wywołania funkcji są  
  
    ```  
    (pObject->*pmf)();  
    (Object.*pmf)();  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje funkcję biblioteki standardowej `strcat_s` z trzech argumentów:  
  
```  
// expre_Function_Call_Operator.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
  
// C++ Standard Library name space  
using namespace std;  
  
int main()  
{  
    enum  
    {  
        sizeOfBuffer = 20  
    };  
  
    char s1[ sizeOfBuffer ] = "Welcome to ";  
    char s2[ ] = "C++";  
  
    strcat_s( s1, sizeOfBuffer, s2 );  
  
    cout << s1 << endl;  
}  
```  
  
```Output  
Welcome to C++  
```  
  
## <a name="function-call-results"></a>Wyniki wywołania funkcji  
 Wywołanie funkcji ma r, chyba, że funkcja jest zadeklarowany jako typ referencyjny. Funkcje z typem zwracanym odwołanie obliczyć wartości l i może służyć po lewej stronie instrukcji przypisania w następujący sposób:  
  
```  
// expre_Function_Call_Results.cpp  
// compile with: /EHsc  
#include <iostream>  
class Point  
{  
public:  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
using namespace std;  
int main()  
{  
    Point ThePoint;  
  
    ThePoint.x() = 7;           // Use x() as an l-value.  
    unsigned y = ThePoint.y();  // Use y() as an r-value.  
  
    // Use x() and y() as r-values.  
    cout << "x = " << ThePoint.x() << "\n"  
         << "y = " << ThePoint.y() << "\n";  
}  
```  
  
 Poprzedni kod definiuje klasę o nazwie `Point`, który zawiera dane prywatne obiekty reprezentujące *x* i *y* współrzędnych. Obiekty te dane muszą zostać zmodyfikowane i pobrać ich wartości. Ten program jest tylko jeden z kilku projektów dla klasy; użycie `GetX` i `SetX` lub `GetY` i `SetY` funkcji jest inny projekt możliwe.  
  
 Funkcje tego typu zwracanego klasy, wskaźniki do typu klasy ani odwołania do typu klasy może być używany jako lewy operand operatory wyboru elementu członkowskiego. W związku z tym następujący kod jest prawnych:  
  
```  
// expre_Function_Results2.cpp  
class A {  
public:  
   A() {}  
   A(int i) {}  
   int SetA( int i ) {  
      return (I = i);  
   }  
  
   int GetA() {  
      return I;  
   }  
  
private:  
   int I;  
};  
  
A func1() {  
   A a = 0;  
   return a;  
}  
  
A* func2() {  
   A *a = new A();  
   return a;  
}  
  
A& func3() {  
   A *a = new A();  
   A &b = *a;  
   return b;  
}  
  
int main() {  
   int iResult = func1().GetA();  
   func2()->SetA( 3 );  
   func3().SetA( 7 );  
}  
```  
  
 Rekursywnie można wywołać funkcji. Aby uzyskać więcej informacji na temat deklaracje funkcji, zobacz [funkcji](functions-cpp.md). Trwa pokrewnego [Program i połączenie](../cpp/program-and-linkage-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia przyrostków](../cpp/postfix-expressions.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Wywołanie funkcji](../c-language/function-call-c.md)   
