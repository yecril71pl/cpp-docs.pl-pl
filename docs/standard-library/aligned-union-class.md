---
title: "aligned_union — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::aligned_union
dev_langs: C++
helpviewer_keywords: aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b85dac1c4abccd15dbf4755026a1288a2c4ee1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="alignedunion-class"></a>aligned_union — klasa
Zawiera typ POD wystarczająco duży i odpowiednio wyrównany do przechowywania typem Unii i rozmiar wymagany.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <std::size_t Len, class... Types>  
struct aligned_union;  
 
template <std::size_t Len, class... Types>  
using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Len`  
 Wartość wyrównania największy typu złożenia.  
  
 `Types`  
 Różne typy w podstawowej Unii.  
  
## <a name="remarks"></a>Uwagi  
 Użyj klasy szablonu, aby pobrać niezbędne do przechowywania w magazynie niezainicjowanej Unii wielkości i. Element członkowski typedef `type` wpisz odpowiednie do przechowywania dowolnego typu na liście nazw POD `Types`; rozmiar minimalny to `Len`. Statyczny element członkowski `alignment_value` typu `std::size_t` zawiera najbardziej rygorystyczne wyrównanie wymagane wszystkich typów na liście `Types`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `aligned_union` można przydzielić bufora stosu wyrównany umieścić Unii.  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
value of u->i is 1065353216  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [alignment_of — klasa](../standard-library/alignment-of-class.md)
