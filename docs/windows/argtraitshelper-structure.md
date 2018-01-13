---
title: "Argtraitshelper — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs: C++
helpviewer_keywords: ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31d9072ebf8c36453a74c75ff4a8997805d0973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename TDelegateInterface  
>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Interfejs delegata.  
  
## <a name="remarks"></a>Uwagi  
 Pomaga zdefiniować wspólne cechy argumentów delegata.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`methodType`|Jest to synonim `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Jest to synonim `ArgTraits<methodType>`.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ArgTraitsHelper::args, stała](../windows/argtraitshelper-args-constant.md)|Pomaga [argtraits::args —](../windows/argtraits-args-constant.md) na bieżąco z informacjami liczba parametrów metody Invoke interfejsu delegata.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)