---
title: Klasa is_move_constructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_move_constructible
dev_langs: C++
helpviewer_keywords: is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c0ca88d938bca629dff15718d8057bd91b96886
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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



