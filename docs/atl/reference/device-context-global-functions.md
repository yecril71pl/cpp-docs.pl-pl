---
title: Funkcje globalne kontekstu urządzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37d54fbe9391cb53cca1d84401e90bb6fd47a479
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358592"
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia
Ta funkcja tworzy kontekstu urządzenia dla danego urządzenia.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|  
  
##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC  
 Tworzy kontekstu urządzenia urządzenia określone w [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) struktury.  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>Parametry  
 *elementu hdc*  
 [in] Istniejące uchwyt kontekstu urządzenia, lub **NULL**.  
  
 `ptd`  
 [in] Wskaźnik do **DVTARGETDEVICE** struktury, który zawiera informacje o urządzeniu docelowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do kontekstu urządzenia urządzenia określone w **DVTARGETDEVICE**. Jeśli urządzenie nie jest określone, zwraca dojście do domyślnego ekranu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli struktura jest **NULL** i *elementu hdc* jest **NULL**, tworzy dla urządzenia wyświetlającego domyślnego kontekstu urządzenia.  
  
 Jeśli *elementu hdc* nie jest **NULL** i `ptd` jest **NULL**, funkcja zwraca istniejące *elementu hdc*.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
   
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
