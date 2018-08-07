---
title: Interfacelist — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 267ef2d9e1b24028016831e050385997ac0037e6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604843"
---
# <a name="interfacelist-structure"></a>InterfaceList — Struktura
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T,  
   typename U  
>  
struct InterfaceList;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Nazwa interfejsu; Pierwszy interfejs na liście cykliczne.  
  
 *U*  
 Nazwa interfejsu; pozostałe interfejsy na liście cykliczne.  
  
## <a name="remarks"></a>Uwagi  
 Użyty do utworzenia cyklicznego listę interfejsów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`FirstT`|Synonim dla parametru szablonu *T*.|  
|`RestT`|Synonim dla parametru szablonu *U*.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)