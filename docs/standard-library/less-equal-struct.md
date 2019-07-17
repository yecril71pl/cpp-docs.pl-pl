---
title: less_equal — Struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::less_equal
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
ms.openlocfilehash: 67a686b139ae4abbf25a42a994cceaba008decf5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245383"
---
# <a name="lessequal-struct"></a>less_equal — Struktura

Predykat binarny, który wykonuje operacje mniej niż lub równe to (`operator<=`) na jego argumenty.

## <a name="syntax"></a>Składnia

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Dowolny typ, który obsługuje `operator<=` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*\
Lewy operand operacji mniej niż lub równe to. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*\
Prawy operand operacji mniej niż lub równe to. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

## <a name="return-value"></a>Wartość zwracana

Wynik `Left <= Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ zwracany przez `operator<=`.

## <a name="remarks"></a>Uwagi

Predykat dwuelementowy `less_equal` < `Type`> udostępnia ścisłe słabe porządkowanie zestaw wartości elementów typu *typu* na klasy równoważności, tylko wtedy, gdy ten typ spełnia standard matematyczne wymagania dotyczące więc szeregowane. Specjalizacje dla dowolnego typu wskaźnika yield, łączna liczba kolejność elementów, w tym, że wszystkie elementy unikatowe wartości są uporządkowane względem siebie.

## <a name="example"></a>Przykład

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
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
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```
