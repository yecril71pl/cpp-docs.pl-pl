---
title: unary_negate — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::unary_negate
helpviewer_keywords:
- unary_negate class
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
ms.openlocfilehash: 2d9f0bedd9e541e65f04ac20375f16f41413cf03
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684434"
---
# <a name="unary_negate-class"></a>unary_negate — Klasa

Szablon klasy dostarczający funkcję członkowską, która wyklucza wartość zwracaną przez określoną funkcję jednoargumentową. Przestarzałe w języku C++ 17 na korzyść [not_fn](functional-functions.md#not_fn).

## <a name="syntax"></a>Składnia

```cpp
template <class Predicate>
class unary_negate
    : public unaryFunction<typename Predicate::argument_type, bool>
{
    explicit unary_negate(const Predicate& Func);
    bool operator()(const typename Predicate::argument_type& left) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *Func*
Funkcja Jednoargumentowa, która ma być negacją.

\ *lewo*
Operand funkcji jednoargumentowej, która ma być negacją.

## <a name="return-value"></a>Wartość zwracana

Negacja funkcji jednoargumentowej.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię jednoargumentowego obiektu *\_Func*. Definiuje jej funkcję członkowską `operator()` jako zwracającą `!_Func(left)`.

Konstruktor `unary_negate` jest rzadko używany bezpośrednio. Funkcja pomocnika [not1 —](../standard-library/functional-functions.md#not1) zapewnia łatwiejszy sposób deklarowania i używania predykatu adaptacji **unary_negator** .

## <a name="example"></a>Przykład

```cpp
// functional_unary_negate.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        unary_negate<binder2nd <greater<int> > >(bind2nd(greater<int>(),10)));

    // The following helper function not1 also works for the above line
    // not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```
