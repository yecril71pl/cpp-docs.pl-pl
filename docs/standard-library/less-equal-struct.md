---
title: less_equal — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::less_equal
dev_langs:
- C++
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb6c0051fbf4a1d5b58cb53891325058effb0db1
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108996"
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

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator<=` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand operacji mniej niż lub równe to. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand operacji mniej niż lub równe to. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

## <a name="return-value"></a>Wartość zwracana

Wynik `Left <= Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ zwracany przez `operator<=`.

## <a name="remarks"></a>Uwagi

Predykat dwuelementowy `less_equal` <  `Type`> udostępnia ścisłe słabe porządkowanie zestaw wartości elementów typu *typu* na klasy równoważności, tylko wtedy, gdy ten typ spełnia standard matematyczne wymagania dotyczące więc szeregowane. Specjalizacje dla dowolnego typu wskaźnika yield, łączna liczba kolejność elementów, w tym, że wszystkie elementy unikatowe wartości są uporządkowane względem siebie.

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

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
