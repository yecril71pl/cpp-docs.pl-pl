---
title: Obiekt stanu makra | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs: C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1139c30fa5d23f3320cef76d09fb5bd86c8c4bc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="object-status-macros"></a>Obiekt stanu makra
To makro ustawia flagi należących do formantu ActiveX.  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Używana w kontrolkach ATL ActiveX do ustawiania **OLEMISC** flagi.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 Używane w formantach ATL ActiveX można ustawić flagi OLEMISC.  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>Parametry  
 *miscstatus*  
 Wszystkie odpowiednie OLEMISC flagi.  
  
### <a name="remarks"></a>Uwagi  
 To makro jest używana do ustawiania flagi OLEMISC dla formantu ActiveX. Zapoznaj się [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) więcej szczegółów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
