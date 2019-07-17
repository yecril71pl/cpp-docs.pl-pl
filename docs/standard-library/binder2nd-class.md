---
title: binder2nd — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 5f59887e6c9d2965a6c8680f17a40c5bd93869c0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243355"
---
# <a name="binder2nd-class"></a>binder2nd — Klasa

Klasa szablonu, zapewniając konstruktora, który konwertuje obiekt binarny funkcji do obiektu funkcyjnego jednoargumentowe przez powiązanie drugi argument funkcji binarnego na określoną wartość. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>Parametry

*FUNC*\
Obiekt binarny funkcji do konwersji na obiekt funkcyjny jednoargumentowy.

*po prawej stronie*\
Wartość, do którego ma zostać powiązany drugi argument obiektu binarnego funkcji.

*po lewej stronie*\
Wartość argumentu, który porównuje dostosowane obiektu binarnego stała wartość drugiego argumentu.

## <a name="return-value"></a>Wartość zwracana

Obiekt funkcji Jednoelementowy, będącą wynikiem powiązanie drugi argument obiektu binarnego funkcji z wartością *prawo*.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię _ obiektu binarnego funkcja *Func* w `op`, a kopia *prawo* w `value`. Definiuje jej funkcji członkowskiej `operator()` powrotu **op**(`left`, **wartość**).

Jeśli `Func` jest obiektem typu `Operation` i języka c jest stałą, następnie [bind2nd —](../standard-library/functional-functions.md#bind2nd) (`Func`, `c`) jest odpowiednikiem `binder2nd` konstruktora klasy `binder2nd` \<  **Operacja**> (`Func`, `c`) i wygodniejsze.

## <a name="example"></a>Przykład

```cpp
// functional_binder2nd.cpp
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
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
