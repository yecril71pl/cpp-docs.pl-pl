---
title: "remove_cv — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::remove_cv
dev_langs:
- C++
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dba786f04cdb114160fd0f0388203c26bd90b41d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="removecv-class"></a>remove_cv — Klasa
Tworzy typ inny niż const/volatile z typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>  
struct remove_cv;  
 
template <class T>  
using remove_cv_t = typename remove_cv<T>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `remove_cv<T>` przechowuje zmodyfikowane — typ danych `T1` podczas `T` ma postać `const T1`, `volatile T1`, lub `const volatile T1`, w przeciwnym razie `T`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_cv_t<const volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_cv_t<const volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_cv_t<const volatile int> == int  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_const — klasa](../standard-library/remove-const-class.md)   
 [remove_volatile, klasa](../standard-library/remove-volatile-class.md)
