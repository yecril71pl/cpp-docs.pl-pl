---
title: greater — Struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
ms.openlocfilehash: 7867de3a56893499f8d705e81ac3b34fabcf188c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159486"
---
# <a name="greater-struct"></a>greater — Struktura

Predykat binarny, który wykonuje większą-niż operacji (`operator>`) na jego argumenty.

## <a name="syntax"></a>Składnia

```cpp
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

};

// specialized transparent functor for operator>
template <>
struct greater<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator>` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand większą-niż operacji. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand większą-niż operacji. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

## <a name="return-value"></a>Wartość zwracana

Wynik `Left > Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator>`.

## <a name="remarks"></a>Uwagi

Predykat dwuelementowy `greater` <  `Type`> udostępnia ścisłe słabe porządkowanie zestaw wartości elementów typu *typu* na klasy równoważności, tylko wtedy, gdy ten typ spełnia standard matematyczne wymagania dotyczące więc szeregowane. Specjalizacje dla dowolnego typu wskaźnika yield, łączna liczba kolejność elementów, w tym, że wszystkie elementy unikatowe wartości są uporządkowane względem siebie.

## <a name="example"></a>Przykład

```cpp
// functional_greater.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i < 8 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater<int>( )
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
