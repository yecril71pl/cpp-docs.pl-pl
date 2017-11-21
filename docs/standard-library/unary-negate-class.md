---
title: "unary_negate — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::unary_negate
dev_langs: C++
helpviewer_keywords: unary_negate class
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37383047b16b26f1d059896d892693e67664cb47
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unarynegate-class"></a>unary_negate — Klasa
Zapewnianie funkcji członkowskiej, która Negacja wartość zwracana funkcji jednoargumentowy określonej klasy szablonów.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Predicate>
class unary_negate
    : public unaryFunction<typename Predicate::argument_type, bool>
{
public:
    explicit unary_negate(const Predicate& Func);
    bool operator()(const typename Predicate::argument_type& left) const;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Func`  
 Jednoargumentowy funkcję, która ma być zanegowane.  
  
 `left`  
 Operand operatora jednoargumentowego funkcję, która ma być zanegowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Negacja funkcja jednoargumentowy.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonu przechowuje kopię _ obiektu funkcja jednoargumentowy *Func.* Definiuje jego funkcji członkowskiej `operator()` jako zwracanie **!**\_ *FUNC(LEFT).*  
  
 Konstruktor obiektu `unary_negate` jest rzadko używana bezpośrednio. Funkcja Pomocnika [not1 —](../standard-library/functional-functions.md#not1) umożliwia łatwiejsze deklarowanie i użycie **unary_negator** predykatu karty.  
  
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
/* Output:  
The vector v1 = ( 0 5 10 15 20 25 30 35 )  
The number of elements in v1 greater than 10 is: 5.  
The number of elements in v1 not greater than 10 is: 3.  
*/  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



