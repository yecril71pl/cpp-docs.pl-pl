---
title: "Funkcje globalne kontekstu urządzenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlwin/ATL::AtlCreateTargetDC
dev_langs: C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9aa685604580423262ab694d1285897cd29eef63
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia
Ta funkcja tworzy kontekstu urządzenia dla danego urządzenia.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|  
  
##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC  
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
