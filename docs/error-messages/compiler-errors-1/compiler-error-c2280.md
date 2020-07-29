---
title: Błąd kompilatora C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 9ee5b8105241ee347812a0dcc083a4f1cc7dca49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208411"
---
# <a name="compiler-error-c2280"></a>Błąd kompilatora C2280

"*Deklaracja*": próba odwołująca się do usuniętej funkcji

Kompilator wykrył próbę odwołania do `deleted` funkcji. Ten błąd może być spowodowany wywołaniem funkcji członkowskiej, która została jawnie oznaczona jako `= deleted` w kodzie źródłowym. Ten błąd może być również spowodowany wywołaniem niejawnej specjalnej funkcji składowej struktury lub klasy, która jest automatycznie deklaruje i oznaczona jako `deleted` kompilator. Aby uzyskać więcej informacji o tym, kiedy kompilator automatycznie generuje **`default`** lub `deleted` Specjalna funkcja członkowska, zobacz [specjalne funkcje składowe](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Przykład: jawnie usunięte funkcje

Wywołanie `deleted` funkcji jawnie powoduje wystąpienie tego błędu. Jawna `deleted` funkcja członkowska oznacza, że Klasa lub struktura jest celowo zaprojektowana tak, aby zapobiec jej użyciu, więc aby rozwiązać ten problem, należy zmienić kod, aby go uniknąć.

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

## <a name="example-uninitialized-data-members"></a>Przykład: Niezainicjowany element członkowski danych

Niezainicjowany element członkowski danych typu odwołania lub **`const`** składowa danych powoduje, że kompilator niejawnie deklaruje `deleted` domyślnego konstruktora. Aby rozwiązać ten problem, zainicjuj element członkowski danych, gdy jest on zadeklarowany.

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

## <a name="example-reference-and-const-data-members"></a>Przykład: elementy członkowskie danych Reference i const

**`const`** Element członkowski danych typu lub referencyjnego powoduje, że kompilator deklaruje `deleted` operator przypisania kopii. Po zainicjowaniu tych członków nie można przypisać do, więc nie można wykonać prostej kopii ani przeniesienia. Aby rozwiązać ten problem, zalecamy zmianę logiki w celu usunięcia operacji przypisania, które powodują wystąpienie błędu.

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

## <a name="example-movable-deletes-implicit-copy"></a>Przykład: Movable usuwa niejawną kopię

Jeśli Klasa deklaruje Konstruktor przenoszący lub przeniesienie przypisania, ale nie deklaruje jawnie konstruktora kopiującego, kompilator niejawnie deklaruje Konstruktor kopiujący i definiuje go jako `deleted` . Podobnie, jeśli Klasa deklaruje Konstruktor przenoszący lub przeniesienie operatora przypisania, ale nie deklaruje jawnie operatora przypisania kopii, kompilator niejawnie deklaruje operator przypisania kopii i definiuje go jako `deleted` . Aby rozwiązać ten problem, należy jawnie zadeklarować tych członków.

Gdy zobaczysz błąd C2280 w połączeniu z `unique_ptr` , prawie jest to spowodowane tym, że próbujesz wywołać jego Konstruktor kopiujący, który jest `deleted` funkcją. Po zaprojektowaniu `unique_ptr` nie można skopiować elementu. Zamiast tego Przenieś własność przy użyciu konstruktora przenoszenia.

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

## <a name="example-variant-and-volatile-members"></a>Przykład: Variant i lotnych elementów członkowskich

Wersje kompilatora przed Visual Studio 2015 Update 2 były niezgodne i wygenerowały domyślne konstruktory i destruktory dla Unii anonimowych. Są one teraz niejawnie zadeklarowane jako `deleted` . Wersje te mogą również niezgodność z niezgodnością definicji **`default`** konstruktorów kopiowania i przenoszenia oraz **`default`** kopiowania i przenoszenia operatorów przypisania w klasach i strukturach, które mają **`volatile`** zmienne składowe. Kompilator uważa teraz, że mają nieuproszczone konstruktory i operatory przypisania, i nie generuje **`default`** implementacji. Gdy taka Klasa jest członkiem Unii lub z anonimowej Unii wewnątrz klasy, konstruktory kopiowania i przenoszenia oraz operatory przypisania kopiowania i przenoszenia dla Unii lub klasy są niejawnie zdefiniowane jako `deleted` . Aby rozwiązać ten problem, należy jawnie zadeklarować wymagane specjalne funkcje składowe.

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

## <a name="example-indirect-base-members-deleted"></a>Przykład: Usunięto pośrednie składowe podstawowe

Wersje kompilatora przed niezgodnością programu Visual Studio 2015 Update 2 i dopuszczają klasę pochodną do wywołania specjalnych funkcji Członkowskich `private virtual` klas podstawowych pochodnych. Kompilator wystawia teraz błąd kompilatora C2280, gdy takie wywołanie zostało wykonane.

W tym przykładzie Klasa `top` pośrednio pochodzi od prywatnej wirtualnej `base` . W przypadku zgodności z kodem sprawia to, że elementy członkowskie są `base` niedostępne dla `top` ; obiekt typu `top` nie może być skonstruowany lub zniszczony jako domyślny. Aby rozwiązać ten problem w kodzie, który opierał się na Starym zachowaniu kompilatora, Zmień klasę pośrednią na Użyj `protected virtual` pochodnej lub Zmień `top` klasę, aby używała bezpośredniego wyprowadzenia:

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
