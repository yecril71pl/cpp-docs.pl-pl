---
title: Błąd kompilatora C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: e1ec032878fefdc1992605df5ee1aa13c673d4cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572812"
---
# <a name="compiler-error-c2280"></a>Błąd kompilatora C2280

"*deklaracji*": próba odwania do usuniętej funkcji do

Kompilator wykrył próbę odwołania `deleted` funkcji. Ten błąd może być spowodowany przez wywołanie do funkcji składowej, która została jawnie oznaczona jako `= deleted` w kodzie źródłowym. Ten błąd, również może być spowodowany przez wywołanie niejawne specjalną funkcję członkowską struktury lub klasy, która jest zadeklarowana i automatycznie oznaczone jako `deleted` przez kompilator. Aby uzyskać więcej informacji na temat gdy kompilator automatycznie generuje `default` lub `deleted` specjalnych funkcji Członkowskich, zobacz [specjalnych funkcji Członkowskich](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Przykład: Jawnie usunięte funkcje

Wywołania jawne `deleted` funkcji powoduje, że ten błąd. Jawnie `deleted` funkcja elementu członkowskiego oznacza, że klasy lub struktury jest celowo ustalono, aby uniemożliwić korzystanie z niego, tak aby rozwiązać ten problem, należy zmienić swój kod, aby uniknąć tego błędu.

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>Przykład: Niezainicjowane składowe danych

Element członkowski danych typu odwołania niezainicjowanej lub `const` element członkowski danych powoduje, że kompilator niejawnie zadeklarować `deleted` domyślnego konstruktora. Aby rozwiązać ten problem, należy zainicjować element członkowski danych, gdy jest on zadeklarowany.

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>Przykład: Odwołań i stałych elementów członkowskich danych

A `const` lub odwołanie do typu element członkowski danych powoduje, że kompilator, aby zadeklarować `deleted` operator przypisania kopiowania. Po zainicjowaniu, nie można przypisać te elementy członkowskie, więc prostego kopiowania lub przenoszenia nie mogą działać. Aby rozwiązać ten problem, zalecamy, zmień logikę w taki sposób, aby usunąć operacji przypisania, których przyczyną błędu.

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>Przykład: Ruchome usuwa niejawne kopiowanie

Jeśli klasa deklaruje Konstruktor przenoszący lub operator przypisania przenoszenia, ale nie deklaruje jawnie konstruktora kopiującego, kompilator niejawnie deklaruje Konstruktor kopiujący i definiuje ją jako `deleted`. Podobnie, jeśli klasa deklaruje Konstruktor przenoszący lub operator przypisania przenoszenia, ale nie jawnie deklarować operatora przypisania kopii, kompilator niejawnie deklaruje operator przypisania kopiowania i definiuje ją jako `deleted`. Aby rozwiązać ten problem, należy jawnie zadeklarować te składowe.

Po wyświetleniu błędu C2280 w połączeniu z `unique_ptr`, jest prawie na pewno ponieważ próbujesz wywołać konstruktora kopiującego, który jest `deleted` funkcji. Zgodnie z projektem `unique_ptr` nie mogą być kopiowane. Użyj konstruktora przenoszącego, aby przenieść własność zamiast tego.

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>Przykład: Elementy członkowskie typu Variant i nietrwałe

Wersje kompilatora przed Visual Studio 2015 Update 2 było niezgodnych i generowanej domyślne konstruktory i destruktory związki anonimowe. Teraz są one niejawnie zadeklarowany jako `deleted`. Te wersje również dozwolone niezgodnych niejawne definicji `default` kopiowanie i przenoszenie konstruktorów i `default` skopiuj i Przenieś operatory przypisania w klas i struktur, które mają `volatile` zmiennych Członkowskich. Kompilator teraz traktuje te nietrywialnymi konstruktorami i operatory przypisania i nie generuje `default` implementacji. Jeśli taka klasa jest elementem członkowskim Unii lub anonimowej Unii wewnątrz klasy, konstruktorach kopiowania i przenoszenia i operatory przypisania kopiowania i przenoszenia, Unia lub klasa jest niejawnie definiowany jako `deleted`. Aby rozwiązać ten problem, należy jawnie zadeklarować wymagane specjalne funkcje Członkowskie.

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>Przykład: Pośrednich podstawowy elementy członkowskie usunięte

Wersje kompilatora przed Visual Studio 2015 Update 2 były niezgodne i dozwolone klasy pochodnej w celu wywołania funkcji pośrednio pochodzi specjalnych elementów członkowskich `private virtual` klas bazowych. Kompilator generuje błąd kompilatora C2280 teraz, gdy takie połączenie jest nawiązywane.

W tym przykładzie klasa `top` pośrednio pochodzi z prywatnego wirtualnego `base`. W kodzie odpowiadające temu członkowie `base` dostępnych dla `top`; obiekt typu `top` nie może być domyślny zbudowanych lub zniszczone. Aby rozwiązać ten problem w kodzie, który opierał się na stare zachowanie kompilatora, należy zmienić klasa pośrednicząca do użycia `protected virtual` pochodnym lub zmień `top` klasy bezpośrednie tworzenie wartości pochodnych:

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
