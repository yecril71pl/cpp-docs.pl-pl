---
title: equal_to — Struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::equal_to
helpviewer_keywords:
- equal_to function
- equal_to struct
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
ms.openlocfilehash: d441d171db518352289a76ca50e807e4042ad23f
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006594"
---
# <a name="equalto-struct"></a>equal_to — Struktura

Predykat binarny, który wykonuje operacje równości (`operator==`) na jego argumenty.

## <a name="syntax"></a>Składnia

```cpp
template <class Type = void>
struct equal_to : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator==
template <>
struct equal_to<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
      ->  decltype(std::forward<T>(Left) == std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator==` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand operacji porównania. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand operacji porównania. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

## <a name="return-value"></a>Wartość zwracana

Wynik `Left == Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator==`.

## <a name="remarks"></a>Uwagi

Obiekty typu *typu* musi umożliwiać porównywanie równości. Takie rozwiązanie wymaga `operator==` zdefiniowane na zestaw obiektów spełnia matematyczne właściwości relacji równoważności. Wszystkie wbudowane typy liczbowe i wskaźnik spełnienia tego wymagania.

## <a name="example"></a>Przykład

```cpp
// functional_equal_to.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 ( 6 );
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i+=2 )
   {
      v1.push_back( 2.0 *i );
      v1.push_back( 2.0 * i + 1.0 );
   }

   int j;
   for ( j = 0 ; j <= 5 ; j+=2 )
   {
      v2.push_back( - 2.0 * j );
      v2.push_back( 2.0 * j + 1.0 );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Testing for the element-wise equality between v1 & v2
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      equal_to<double>( ) );

   cout << "The result of the element-wise equal_to comparison\n"
      << "between v1 & v2 is: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 0 1 4 5 8 9 )
The vector v2 = ( -0 1 -4 5 -8 9 )
The result of the element-wise equal_to comparison
between v1 & v2 is: ( 1 1 0 1 0 1 )
```

