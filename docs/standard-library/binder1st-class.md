---
title: binder1st — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 384a870a10c9f806684443d8c67647e924b6b2aa
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243384"
---
# <a name="binder1st-class"></a>binder1st — Klasa

Klasa szablonu, zapewniając konstruktora, który konwertuje obiekt binarny funkcji do obiektu funkcyjnego jednoargumentowe przez powiązanie pierwszy argument funkcji binarnego na określoną wartość. Przestarzałe w C ++ 11 uzyskać [powiązania](functional-functions.md#bind)i usuwane w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Parametry

*binary_fn*\
Obiekt binarny funkcji do konwersji na obiekt funkcyjny jednoargumentowy.

*po lewej stronie*\
Wartość, do którego ma zostać powiązany pierwszy argument obiektu binarnego funkcji.

*po prawej stronie*\
Wartość argumentu, który porównuje dostosowane obiektu binarnego stała wartość drugiego argumentu.

## <a name="return-value"></a>Wartość zwracana

Obiekt funkcji Jednoelementowy, będącą wynikiem powiązanie pierwszy argument obiektu binarnego funkcji z wartością *po lewej stronie*.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię obiektu binarnego funkcja *binary_fn* w `op`, a kopia *po lewej stronie* w `value`. Definiuje jej funkcji członkowskiej `operator()` powrotu `op(value, right)`.

Jeśli *binary_fn* jest obiektem typu `Operation` i `c` jest stałą, następnie `bind1st(binary_fn, c)` jest bardziej wygodne odpowiednikiem `binder1st<Operation>(binary_fn, c)`. Aby uzyskać więcej informacji, zobacz [bind1st —](../standard-library/functional-functions.md#bind1st).

## <a name="example"></a>Przykład

```cpp
// functional_binder1st.cpp
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
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
