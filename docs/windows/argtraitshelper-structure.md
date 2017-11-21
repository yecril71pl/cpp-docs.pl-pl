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
ms.openlocfilehash: e8c42db196836a4a618003bfa14cd08d53105a04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Argtraitshelper::args — stała](../windows/argtraitshelper-args-constant.md)|Pomaga [argtraits::args —](../windows/argtraits-args-constant.md) na bieżąco z informacjami liczba parametrów metody Invoke interfejsu delegata.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)