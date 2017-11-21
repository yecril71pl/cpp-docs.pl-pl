---
title: "add_pointer — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_pointer
dev_langs: C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c8a55af99a2a058c967ad87dadb038ce06cf56b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [remove_pointer — klasa](../standard-library/remove-pointer-class.md)
