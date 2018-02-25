---
title: "is_standard_layout — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27f9d94132b979ac096147cd5a3926733d6414b2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="isstandardlayout-class"></a>is_standard_layout — Klasa
Testy, jeśli typ jest standardowego układu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_standard_layout;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Ty`|Typ do zapytania|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienia tego typu predykatu przechowuje wartość PRAWDA, jeśli typ `Ty` jest klasa, która ma układ standardowy wszystkich obiektów w pamięci, w przeciwnym razie posiada wartość false.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



