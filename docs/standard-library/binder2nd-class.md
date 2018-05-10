---
title: binder2nd — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::binder2nd
dev_langs:
- C++
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de37ee92805d35b25e73e0682ce8abe79822a8b5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="binder2nd-class"></a>binder2nd — Klasa

Klasy szablonów dostarczanie konstruktora, który konwertuje obiektu binarnego funkcja na obiekt funkcja jednoargumentowy przez powiązanie drugi argument funkcji binarnego do określonej wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;

protected:
    Operation op;
    typename Operation::second_argument_type value;
};
```

### <a name="parameters"></a>Parametry

`Func` Obiekt binarny funkcji do przekonwertowania na obiekt funkcja jednoargumentowy.

`right` Wartość, do której ma zostać powiązany drugi argument obiektu binarnego funkcji.

`left` Wartość argumentu, który porównuje dostosowane obiektu binarnego stała wartość drugiego argumentu.

## <a name="return-value"></a>Wartość zwracana

Obiekt funkcji jednoargumentowy będącą wynikiem powiązanie drugi argument obiektu, funkcja binarnej na wartość `right.`

## <a name="remarks"></a>Uwagi

Klasy szablonu przechowuje kopię _ obiektu binarnego funkcja *Func* w **op**, a kopia `right` w **wartość**. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie **op**( `left`, **wartość**).

Jeśli `Func` jest obiektem typu **operacji** i c to stała, następnie [bind2nd —](../standard-library/functional-functions.md#bind2nd) ( `Func`, `c` ) jest odpowiednikiem `binder2nd` konstruktora klasy `binder2nd` \< **Operacji**> ( `Func`, `c` ) i wygodniejsze.

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
/* Output:
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
