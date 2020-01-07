---
title: 'Operator wywołania funkcji: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
ms.openlocfilehash: 3194c34bacfe7b2ed758ab245c5858eadb18e64e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301525"
---
# <a name="function-call-operator-"></a>Operator wywołania funkcji: ()

Wyrażenie przyrostkowe, po którym następuje operator wywołania funkcji **()** , określa wywołanie funkcji.

## <a name="syntax"></a>Składnia

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Uwagi

Argumenty operatora wywołania funkcji są równe zero lub więcej wyrażeń oddzielonych przecinkami — rzeczywiste argumenty funkcji.

*Wyrażenie przyrostkowe* musi być szacowane do adresu funkcji (na przykład identyfikatora funkcji lub wartości wskaźnika funkcji), a *Lista argumentów wyrażenia* jest listą wyrażeń (rozdzielonych przecinkami), których wartości (argumenty) są przekazane do funkcji. Argument *-Expression-List* może być pusty.

*Wyrażenie przyrostkowe* musi mieć jeden z następujących typów:

- Funkcja zwracająca typ `T`. Przykładowa deklaracja to

    ```cpp
    T func( int i )
    ```

- Wskaźnik do funkcji zwracającej typ `T`. Przykładowa deklaracja to

    ```cpp
    T (*func)( int i )
    ```

- Odwołanie do funkcji zwracającej typ `T`. Przykładowa deklaracja to

    ```cpp
    T (&func)(int i)
    ```

- Zwraca odwołanie do funkcji typu wskaźnik-do-Członkowskiego zwracającego typ `T`. Przykładowe wywołania funkcji to

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Przykład

Poniższy przykład wywołuje funkcję biblioteki standardowej `strcat_s` z trzema argumentami:

```cpp
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

Wywołanie funkcji zwraca wartość r-Value, chyba że funkcja jest zadeklarowana jako typ referencyjny. Funkcje z typem zwracanym odwołania są oceniane do l-wartości i mogą być używane po lewej stronie instrukcji przypisania w następujący sposób:

```cpp
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

Poprzedni kod definiuje klasę o nazwie `Point`, która zawiera obiekty danych prywatnych, które reprezentują współrzędne *x* i *y* . Te obiekty danych muszą być modyfikowane i ich wartości są pobierane. Ten program jest tylko jednym z kilku projektów dla takiej klasy; Korzystanie z `GetX` i `SetX` lub `GetY` oraz funkcji `SetY` jest innym możliwym projektem.

Funkcje, które zwracają typy klas, wskaźniki do typów klas lub odwołania do typów klasy mogą być używane jako lewy operand do operatorów wyboru elementu członkowskiego. W związku z tym Poniższy kod jest dozwolony:

```cpp
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

Funkcje mogą być wywoływane cyklicznie. Aby uzyskać więcej informacji na temat deklaracji funkcji, zobacz [Functions](functions-cpp.md). Powiązane materiały są w [jednostkach translacji i powiązaniach](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wywołanie funkcji](../c-language/function-call-c.md)