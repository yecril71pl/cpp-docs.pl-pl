---
title: C2280 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
dev_langs:
- C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b55e07a7109c090126dfdec61bbc18bdaf5ef710
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2280"></a>C2280 błąd kompilatora  
  
"*deklaracji*": próba odwołania usunięta funkcja  
  
Kompilator wykrył próbę odwołania `deleted` funkcji. Ten błąd może być spowodowany przez wywołanie funkcji Członkowskich, które zostało jawnie oznaczone jako `= deleted` w kodzie źródłowym. Przyczyną tego błędu może również być wywołania niejawnego specjalnej funkcji członkowskiej struktury lub klasy, która jest zadeklarowana i automatycznie oznaczone jako `deleted` przez kompilator. Aby uzyskać więcej informacji na temat gdy kompilator automatycznie generuje `default` lub `deleted` specjalnych funkcji Członkowskich, zobacz [specjalnych funkcji Członkowskich](../../cpp/special-member-functions.md).  
  
## <a name="example-explicitly-deleted-functions"></a>Przykład: Jawnie usunięte funkcje  

Wywołanie jawnie `deleted` funkcja powoduje, że ten błąd. Jawnie `deleted` funkcji członkowskiej oznacza, że klasy lub struktury celowo ma uniemożliwić korzystanie z niego, tak aby rozwiązać ten problem, należy zmienić swój kod, aby uniknąć tego problemu.  
  
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
  
## <a name="example-uninitialized-data-members"></a>Przykład: Elementy członkowskie danych niezainicjowanej  
  
Element członkowski danych typu niezainicjowanej odwołanie lub `const` element członkowski danych powoduje, że kompilator niejawnie deklaruje `deleted` domyślnego konstruktora. Aby rozwiązać ten problem, należy zainicjować element członkowski danych, gdy jest on zadeklarowany jako.  
  
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
  
## <a name="example-reference-and-const-data-members"></a>Przykład: Odwołania i const elementy członkowskie danych  
  
A `const` lub element członkowski odwołania typu danych powoduje, że kompilator, aby zadeklarować `deleted` operatora przypisania kopii. Po zainicjowany, tych elementów członkowskich nie można przypisać, dlatego prostego kopiowania lub przenoszenia nie może działać. Aby rozwiązać ten problem, firma Microsoft zaleca się, że możesz zmienić logiki, aby usunąć operacje przydziałów, które przyczyną błędu.  
  
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
  
## <a name="example-movable-deletes-implicit-copy"></a>Przykład: Usuwa ruchome niejawne kopiowania  
  
Jeśli klasa deklaruje Konstruktor przenoszenia lub operator przypisania przenoszenia, ale nie deklaruje jawnie konstruktora kopiującego, kompilator niejawnie deklaruje konstruktora kopiującego i definiuje ją jako `deleted`. Podobnie, jeśli klasa deklaruje Konstruktor przenoszenia lub operator przypisania przenoszenia, ale nie jawnie deklarować operatora przypisania kopii, kompilator niejawnie deklaruje operatora przypisania kopii i definiuje ją jako `deleted`. Aby rozwiązać ten problem, musisz jawnie zadeklarować tych elementów członkowskich.  
 
Po wyświetleniu błędu C2280 w połączeniu z `unique_ptr`, jest prawie na pewno ponieważ podjęto próbę wywołania konstruktora kopiującego, który jest `deleted` funkcji. Zgodnie z projektem `unique_ptr` nie można skopiować. Konstruktor przenoszący umożliwia zamiast tego przeniesienia własności.  

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
  
Wersje kompilatora przed Visual Studio 2015 Update 2 były domyślne niezgodnych i generowane konstruktory i destruktory w przypadku anonimowych Unii. Teraz są one niejawnie zadeklarowany jako `deleted`. Tymi wersjami mogą również niezgodnych niejawnego definiowania elementu `default` kopiowanie i przenoszenie konstruktory i `default` kopiowanie i przenoszenie operatory przypisania w klasy i struktury, która ma `volatile` zmiennych Członkowskich. Kompilator teraz traktuje te mają nieuproszczony konstruktory i operatory przypisania i nie generuje `default` implementacji. Jeśli taka klasa jest elementem członkowskim Unii lub anonimowego związku wewnątrz klasy, konstruktorach kopiowania i przenoszenia i operatory przypisania kopiowania i przenoszenia klasy lub union niejawnie są zdefiniowane jako `deleted`. Aby rozwiązać ten problem, musisz jawnie zadeklarować wymagane specjalne funkcje Członkowskie.  
  
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
  
## <a name="example-indirect-base-members-deleted"></a>Przykład: Pośrednie podstawowe elementy członkowskie usunięte  
  
Wersje kompilatora przed Visual Studio 2015 Update 2 zostały niezgodnych i dozwolone klasy pochodnej w celu wywołać elementu członkowskiego specjalne funkcje pośrednio pochodzi `private virtual` klasy podstawowej. Kompilator generuje teraz błąd kompilatora C2280, jeśli takie połączenie jest nawiązywane.  
  
W tym przykładzie klasa `top` pośrednio pochodzi z prywatnego wirtualnego `base`. W kodzie zgodnych to sprawia, że członkowie `base` niedostępne do `top`; obiekt typu `top` nie może być domyślny zbudowanych lub zniszczony. Aby rozwiązać ten problem w kodzie, który będzie zależał od starego zachowania kompilatora, zmień klasa pośrednicząca do użycia `protected virtual` pochodnym lub zmień `top` klasy do użycia bezpośredniego pochodnym:  

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
  