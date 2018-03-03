---
title: "Isbaseofstrict — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a8e40bec0f4dedf02aab14b2c8072ccc3e60bbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Typ podstawowy.  
  
 `Derived`  
 Typ pochodny.  
  
## <a name="remarks"></a>Uwagi  
 Sprawdza, czy jest jeden typ podstawowy innego.  
  
 Pierwszy szablon sprawdza, czy typ pochodzi z typu podstawowego, może dać **true** lub **false**. Drugi szablon sprawdza, czy typ jest pochodną, która zawsze daje w wyniku **false**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IsBaseOfStrict::value, stała](../windows/isbaseofstrict-value-constant.md)|Wskazuje, czy jeden typ jest podstawą innego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)