---
title: typeid — operator
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: e17b88d81d9987ec586401e025e108cfbe88cb3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223527"
---
# <a name="typeid-operator"></a>typeid — operator

## <a name="syntax"></a>Składnia

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Uwagi

**`typeid`** Operator umożliwia określenie typu obiektu w czasie wykonywania.

Wynik **`typeid`** jest `const type_info&` . Wartość jest odwołaniem do `type_info` obiektu, który reprezentuje *Identyfikator typu* lub typ *wyrażenia*, w zależności od tego, która forma **`typeid`** jest używana. Aby uzyskać więcej informacji, zobacz [type_info Class](../cpp/type-info-class.md).

**`typeid`** Operator nie działa z typami zarządzanymi (abstrakcyjne Deklaratory lub Instances). Aby uzyskać informacje na temat pobierania <xref:System.Type> określonego typu, zobacz [typeid](../extensions/typeid-cpp-component-extensions.md).

**`typeid`** Operator wykonuje sprawdzanie w czasie wykonywania w przypadku zastosowania do l-wartości typu polimorficznej klasy, gdzie prawdziwy typ obiektu nie może być określony przez podane informacje statyczne. Takie przypadki są:

- Odwołaniem do klasy

- Wskaźnik, do którego odwołuje się`*`

- Wskaźnik indeksu dolnego ( `[ ]` ). (Użycie indeksu dolnego ze wskaźnikiem do typu polimorficznego nie jest bezpieczne.)

Jeśli *wyrażenie* wskazuje typ klasy bazowej, a obiekt faktycznie jest typu pochodzącego od tej klasy bazowej, to `type_info` wynik jest odwołaniem dla klasy pochodnej. *Wyrażenie* musi wskazywać na typ polimorficzny (Klasa z funkcjami wirtualnymi). W przeciwnym razie wynik jest `type_info` dla klasy statycznej, do której odwołuje się w *wyrażeniu*. Dodatkowo, wskaźnik musi być wywoływany, aby użyty obiekt był punktem, do którego się odwołuje. Bez wyłuskania wskaźnika, wynik będzie `type_info` dla wskaźnika, a nie do czego wskazuje. Na przykład:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Jeśli *wyrażenie* odwołuje się do wskaźnika, a wartość wskaźnika jest równa zero, **`typeid`** zgłasza [wyjątek bad_typeid](../cpp/bad-typeid-exception.md). Jeśli wskaźnik nie wskazuje prawidłowego obiektu, `__non_rtti_object` zostanie zgłoszony wyjątek. Wskazuje ona próbę analizy RTTI, która wyzwoliła błąd, ponieważ obiekt jest w jakiś sposób nieprawidłowy. (Na przykład jest to zły wskaźnik lub kod nie został skompilowany z [/gr](../build/reference/gr-enable-run-time-type-information.md)).

Jeśli *wyrażenie* nie jest wskaźnikiem ani odwołaniem do klasy bazowej obiektu, wynik jest `type_info` odwołaniem reprezentującym typ statyczny *wyrażenia*. *Typ statyczny* wyrażenia odwołuje się do typu wyrażenia, ponieważ jest on znany w czasie kompilacji. Semantyka wykonania jest ignorowana przy ocenie typu statycznego wyrażenia. Ponadto, odwołania są ignorowane, gdy to możliwe przy określaniu typu statycznego wyrażenia:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** można go również użyć w szablonach do określenia typu parametru szablonu:

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>Zobacz także

[Informacje o typie w czasie wykonywania](../cpp/run-time-type-information.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
