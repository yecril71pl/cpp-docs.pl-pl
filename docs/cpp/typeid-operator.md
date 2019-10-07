---
title: typeid — operator
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 93a2d3c494cd5aadafedcaaae9ec72809d633a4a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998749"
---
# <a name="typeid-operator"></a>typeid — operator

## <a name="syntax"></a>Składnia

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Uwagi

Operator **typeid** umożliwia określenie typu obiektu w czasie wykonywania.

Wynikiem elementu **typeid** jest `const type_info&`. Wartość jest odwołaniem do obiektu `type_info`, który reprezentuje *Identyfikator typu* lub typ *wyrażenia*, w zależności od tego, który formularz **typeid** jest używany. Aby uzyskać więcej informacji, zobacz [Klasa type_info](../cpp/type-info-class.md).

Operator **typeid** nie działa z typami zarządzanymi (abstrakcyjne Deklaratory lub Instances). Aby uzyskać informacje na temat pobierania <xref:System.Type> określonego typu, zobacz [typeid](../extensions/typeid-cpp-component-extensions.md).

Operator **typeid** wykonuje sprawdzanie w czasie wykonywania w przypadku zastosowania do l-wartości typu polimorficznej klasy, w której nie można ustalić prawdziwego typu obiektu za pomocą dostarczonych informacji statycznych. Takie przypadki są:

- Odwołaniem do klasy

- Wskaźnik, do którego odwołuje się `*`

- Wskaźnik indeksu dolnego (`[ ]`). (Użycie indeksu dolnego ze wskaźnikiem do typu polimorficznego nie jest bezpieczne.)

Jeśli *wyrażenie* wskazuje typ klasy bazowej, a obiekt faktycznie jest typu pochodnego od tej klasy bazowej, to wynik jest odwołaniem `type_info` dla klasy pochodnej. *Wyrażenie* musi wskazywać na typ polimorficzny (Klasa z funkcjami wirtualnymi). W przeciwnym razie wynik jest `type_info` dla klasy statycznej, do której odwołuje się w *wyrażeniu*. Dodatkowo, wskaźnik musi być wywoływany, aby użyty obiekt był punktem, do którego się odwołuje. Bez wyłuskania wskaźnika, wynik będzie `type_info` dla wskaźnika, a nie wskazuje. Na przykład:

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

Jeśli *wyrażenie* odwołuje się do wskaźnika, a wartość wskaźnika jest równa zero, **typeid** zgłasza [wyjątek bad_typeid](../cpp/bad-typeid-exception.md). Jeśli wskaźnik nie wskazuje prawidłowego obiektu, zostanie zgłoszony wyjątek `__non_rtti_object`. Wskazuje ona próbę analizy RTTI, która wyzwoliła błąd, ponieważ obiekt jest w jakiś sposób nieprawidłowy. (Na przykład jest to zły wskaźnik lub kod nie został skompilowany z [/gr](../build/reference/gr-enable-run-time-type-information.md)).

Jeśli *wyrażenie* nie jest wskaźnikiem ani odwołaniem do klasy bazowej obiektu, wynikiem jest odwołanie `type_info` reprezentujące typ statyczny *wyrażenia*. *Typ statyczny* wyrażenia odwołuje się do typu wyrażenia, ponieważ jest on znany w czasie kompilacji. Semantyka wykonania jest ignorowana przy ocenie typu statycznego wyrażenia. Ponadto, odwołania są ignorowane, gdy to możliwe przy określaniu typu statycznego wyrażenia:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

elementu **typeid** można także użyć w szablonach, aby określić typ parametru szablonu:

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

[Informacje o typie czasu wykonywania](../cpp/run-time-type-information.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
