---
title: "add_pointer — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2824ce777e2f146adc6e8f3cbd20eb6aff887f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="addpointer-class"></a>add_pointer — Klasa
Tworzy wskaźnik do typu z określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>  
struct add_pointer;  
 
template <class T>
using add_pointer_t = typename add_pointer<T>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
*T*  
Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
Element członkowski typedef `type` nazwy tego samego typu co `remove_reference<T>::type*`. Alias `add_pointer_t` to skrót do dostępu — element członkowski typedef `type`.  
  
Ponieważ jest on nieprawidłowy wskaźnik z odwołania, aby `add_pointer` Usuwa odwołanie, z określonego typu przed nią sprawia, że wskaźnik do typu. W związku z tym, można użyć typu z `add_pointer` bez trwa zależy od tego, czy typ jest odwołanie.  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie pokazano, że `add_pointer` typu jest taka sama jak wskaźnik do typu.  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_pointer_t<int> *p = (int **)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_pointer_t<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
add_pointer_t<int> == int *  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_pointer, klasa](../standard-library/remove-pointer-class.md)
