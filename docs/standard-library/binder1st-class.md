---
title: "binder1st — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::binder1st
dev_langs:
- C++
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3764a4ef76425ef1b92b7eef2f46803d291a91a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="binder1st-class"></a>binder1st — Klasa
Klasy szablonów dostarczanie konstruktora, który konwertuje obiektu binarnego funkcja na obiekt funkcja jednoargumentowy przez powiązanie pierwszy argument funkcji binarnego do określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& Func,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Func`  
 Obiekt binarny funkcji do przekonwertowania na obiekt funkcja jednoargumentowy.  
  
 `left`  
 Wartość, do której ma zostać powiązany pierwszy argument obiektu binarnego funkcji.  
  
 `right`  
 Wartość argumentu, który porównuje dostosowane obiektu binarnego stała wartość drugiego argumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt funkcji jednoargumentowy będącą wynikiem powiązanie pierwszy argument obiektu, funkcja binarnej na wartość `left.`  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonu przechowuje kopię obiektu binarnego funkcja `Func` w **op**, a kopia `left` w **wartość**. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie **op**( **wartość**, `right`).  
  
 Jeśli `Func` jest obiektem typu **operacji** i `c` jest stałą, następnie [bind1st —](../standard-library/functional-functions.md#bind1st) ( `Func`, `c` ) jest odpowiednikiem `binder1st` — klasa Konstruktor `binder1st` \< **operacji**> ( `Func`, `c` ) i wygodniejsze.  
  
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
\* Output:   
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 less than 10 is: 2.  
*\  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



