---
title: Klasa is_final | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 877e2b057487ff17befcd97509abb29ed99ef237
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="isfinal-class"></a>is_final — klasa
Sprawdza, czy typ jest oznaczony jako typ klasy `final`.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct is_final;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest oznaczony jako typ klasy `final`, w przeciwnym razie ma wartość false. Jeśli `T` jest typem klasy musi być typu ukończone.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [final, specyfikator](../cpp/final-specifier.md)



