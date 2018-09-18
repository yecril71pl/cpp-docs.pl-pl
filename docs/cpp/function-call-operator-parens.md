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
ms.openlocfilehash: d0d42bf1d594e06c78b031267df56e2665b5d6f6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017550"
---
# <a name="function-call-operator-"></a>Operator wywołania funkcji: ()

Wyrażenie przyrostkowe następują operator wywołania funkcji **()**, określa wywołania funkcji.

## <a name="syntax"></a>Składnia

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Uwagi

Argumenty dla operatora wywołania funkcji są zero lub więcej wyrażeń oddzielonych przecinkami — rzeczywiste argumenty do funkcji.

*Wyrażeniem przyrostkowym* musi zwrócić adresu funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), a *argument-expression-list* jest listą wyrażeń (oddzielonych przecinkami) których wartości (argumenty) są przekazywane do funkcji. *Argument-expression-list* argument może być pusta.

*Wyrażeniem przyrostkowym* musi być jedną z następujących typów:

- Funkcja zwracająca typ `T`. Deklaracja przykład jest

    ```cpp
    T func( int i )
    ```

- Wskaźnik do funkcji zwracająca typ `T`. Deklaracja przykład jest

    ```cpp
    T (*func)( int i )
    ```

- Odwołanie do funkcji zwracająca typ `T`. Deklaracja przykład jest

    ```cpp
    T (&func)(int i)
    ```

- Funkcja wskaźnika do elementu członkowskiego wyłuskania typ zwracanych `T`. Przykład wywołania funkcji są

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Przykład

Poniższy przykład wywołuje funkcję biblioteki standardowej `strcat_s` z trzech argumentów:

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

Wywołania funkcji ocenia do r-wartości, chyba że funkcja jest zadeklarowana jako typ odwołania. Funkcje z typem zwracanym odwołanie l-wartościami i może służyć po lewej stronie instrukcji przypisania w następujący sposób:

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

Powyższy kod definiuje klasę o nazwie `Point`, który zawiera dane prywatne obiekty reprezentujące *x* i *y* współrzędnych. Obiekty te dane muszą zostać zmodyfikowane, a następnie pobrać ich wartości. Ten program jest tylko jeden z kilku projektów dla klasy; Korzystanie z `GetX` i `SetX` lub `GetY` i `SetY` funkcji jest inny projekt to możliwe.

Funkcje tego typu zwracanego klasy, wskaźniki do typu klasy lub odwołania do typu klasy, które mogą być używane jako lewy operand operatory wyboru elementu członkowskiego. W związku z tym poniższy kod jest dozwolony:

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

Funkcje mogą być wywoływane cyklicznie. Aby uzyskać więcej informacji na temat deklaracji funkcji, zobacz [funkcji](functions-cpp.md). Trwa pokrewnego [Program i połączenie](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wywołanie funkcji](../c-language/function-call-c.md)