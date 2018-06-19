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
ms.openlocfilehash: 52acf2f0b9936903b4359e21e23ae50c95d2f31a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876738"
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
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Nazwa interfejsu; Pierwszy interfejs na liście cyklicznego.  
  
 `U`  
 Nazwa interfejsu; pozostałe interfejsy na liście cyklicznego.  
  
## <a name="remarks"></a>Uwagi  
 Pozwala utworzyć listę cykliczne interfejsów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`FirstT`|Synonim dla parametru szablonu `T`.|  
|`RestT`|Synonim dla parametru szablonu `U`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InterfaceList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)