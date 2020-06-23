---
title: 'Operator wywołania funkcji: ()'
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 59fd36a5ae135c55813019f04b0f5df4be2800b3
ms.sourcegitcommit: 2d7550d0f375aafa428ef0fb2e3962e4232be28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84777308"
---
# <a name="function-call-operator-"></a>Operator wywołania funkcji: ()

Wywołanie funkcji jest rodzajem *`postfix-expression`* , utworzonym przez wyrażenie identyfikujące funkcję, po której następuje operator wywołania funkcji **`()`** . Obiekt może zadeklarować `operator ()` funkcję, która zapewnia semantykę wywołań funkcji dla obiektu.

## <a name="syntax"></a>Składnia

> *`postfix-expression`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>Uwagi

Argumenty operatora wywołania funkcji pochodzą z *`argument-expression-list`* , rozdzielana przecinkami lista wyrażeń. Wartości tych wyrażeń są przekazane do funkcji jako argumenty. *Argument-expression-list* może być pusty. Przed C++ 17 kolejność obliczania wyrażenia funkcji i wyrażeń argumentów jest nieokreślona i może wystąpić w dowolnej kolejności. W języku C++ 17 i nowszych wyrażenie funkcji jest oceniane przed wszystkimi wyrażeniami argumentów lub argumentami domyślnymi. Wyrażenia argumentów są oceniane w nieokreślonej kolejności.

*`postfix-expression`* Identyfikuje funkcję, która ma zostać wywołana. Musi on być obliczany jako adres funkcji. Może to być jeden z kilku form:

- Nazwa lub wskaźnik funkcji lub obiektu funkcji,
- wyrażenie lvalue odwołujące się do funkcji lub obiektu funkcji,
- Metoda dostępu do funkcji składowej, jawnie lub implikowana.

Funkcja określona przez *`postfix-expression`* może być funkcją przeciążoną. Zwykle reguły rozpoznawania przeciążenia określają rzeczywistą funkcję do wywołania.

Przykładowe deklaracje:

- Funkcja zwraca typ `T` . Przykładowa deklaracja to

    ```cpp
    T func( int i );
    ```

- Wskaźnik do zwracanego typu funkcji `T` . Przykładowa deklaracja to

    ```cpp
    T (*func)( int i );
    ```

- Odwołanie do zwracanego typu funkcji `T` . Przykładowa deklaracja to

    ```cpp
    T (&func)(int i);
    ```

- Zwracany typ odwołania funkcji wskaźnika do składowej `T` . Przykładowe wywołania funkcji to

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

Wywołanie funkcji jest oceniane do elementu rvalue, chyba że funkcja jest zadeklarowana jako typ referencyjny. Funkcje z zwracanymi typami odwołań są oceniane do lvalues. Te funkcje mogą być używane z lewej strony instrukcji przypisania, jak pokazano tutaj:

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

Poprzedni kod definiuje klasę o nazwie `Point` , która zawiera obiekty danych prywatnych, które reprezentują współrzędne *x* i *y* . Te obiekty danych muszą być modyfikowane i ich wartości są pobierane. Ten program jest tylko jednym z kilku projektów dla takiej klasy; Korzystanie z `GetX` funkcji i `SetX` lub `GetY` i `SetY` jest innym możliwym projektem.

Funkcje, które zwracają typy klas, wskaźniki do typów klas lub odwołania do typów klasy mogą być używane jako lewy operand do operatorów wyboru elementu członkowskiego. Następujący kod jest dozwolony:

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

## <a name="see-also"></a>Zobacz też

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wywołanie funkcji](../c-language/function-call-c.md)
