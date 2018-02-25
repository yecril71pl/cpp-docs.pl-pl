---
title: Klasa is_move_constructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15c1fb9b3b4e3dc27b887ac70005be55813399a7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ismoveconstructible-class"></a>is_move_constructible — klasa
Sprawdza, czy typ ma konstruktora przenoszenia.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
struct is_move_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 T  
 Typ, który ma zostać obliczone  
  
## <a name="remarks"></a>Uwagi  
 Predykat typów, która daje w wyniku wartość true, jeśli typ `T` może być skonstruowany przy użyciu operacji przenoszenia. Odpowiada to predykatu `is_constructible<T, T&&>`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



