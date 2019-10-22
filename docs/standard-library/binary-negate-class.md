---
title: binary_negate — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::binary_negate
helpviewer_keywords:
- binary_negate class
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
ms.openlocfilehash: 01396384cbd551cca5682c7ffd1b31d89e6d1dc2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688398"
---
# <a name="binary_negate-class"></a>binary_negate — Klasa

Szablon klasy dostarczający funkcję członkowską, która wyklucza wartość zwracaną określonej funkcji binarnej. Przestarzałe w języku C++ 17 na korzyść [not_fn](functional-functions.md#not_fn).

## <a name="syntax"></a>Składnia

```cpp
template <class Operation>
class binary_negate
    : public binaryFunction <typename Operation::first_argument_type,
                              typename Operation::second_argument_type, bool>
{
    explicit binary_negate(const Operation& Func);
    bool operator()(const typename Operation::first_argument_type& left,
                    const typename Operation::second_argument_type& right) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *Func*
Funkcja binarna, która ma być negacją.

\ *lewo*
Lewy operand funkcji binarnej, która ma być negacją.

*prawa* \
Prawy operand funkcji binarnej, która ma być negacją.

## <a name="return-value"></a>Wartość zwracana

Negacja funkcji binarnej.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *obiektu funkcji*binarnej. Definiuje jej funkcję członkowską `operator()` jako zwracającą `!Func(left, right)`.

Konstruktor `binary_negate` jest rzadko używany bezpośrednio. Funkcja pomocnika [not2 —](../standard-library/functional-functions.md#not2) jest zwykle preferowana do zadeklarowania i użycia predykatu adaptera **binary_negator** .

## <a name="example"></a>Przykład

```cpp
// functional_binary_negate.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>

#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector <unsigned int> v1;
   vector <unsigned int>::iterator Iter1;

   unsigned int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   unsigned int randVal = 0;
   for ( i = 0 ; i < 5 ; i++ )
   {
      rand_s(&randVal);
      v1.push_back( randVal );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<unsigned int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate function
   sort( v1.begin( ), v1.end( ),
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );

   // The helper function not2 could also have been used
   // in the above line and is usually preferred for convenience
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );

   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 2233879413 2621500314 580942933 3715465425 3739828298 )
Sorted vector v1 = ( 6262 6262 580942933 2233879413 2621500314 3715465425 3739828298 )
Resorted vector v1 = ( 3739828298 3715465425 2621500314 2233879413 580942933 6262 6262 )
```
