---
title: "remove_reference — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::remove_reference
dev_langs:
- C++
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ba826580bd06c83a735899f298574fab353445a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="removereference-class"></a>remove_reference — Klasa
Tworzy typ inny niż odwołanie z typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>  
struct remove_reference;  
 
template <class T>  
using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `remove_reference<T>` przechowuje zmodyfikowane — typ danych `T1` podczas `T` ma postać `T1&`, w przeciwnym razie `T`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [add_lvalue_reference, klasa](../standard-library/add-lvalue-reference-class.md)
