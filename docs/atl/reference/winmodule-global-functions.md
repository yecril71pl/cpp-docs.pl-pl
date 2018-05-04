---
title: Funkcje globalne WinModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 514703e2c7c968035e9defc7677943377778a761
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="winmodule-global-functions"></a>Funkcje globalne WinModule
Funkcje te zapewniają obsługę `_AtlCreateWndData` struktury operacji.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Ta funkcja służy do inicjowania i dodać `_AtlCreateWndData` struktury.|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Wywołanie tej funkcji, aby wyodrębnić istniejące `_AtlCreateWndData` struktury.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData  
 Ta funkcja służy do inicjowania i dodać `_AtlCreateWndData` struktury.  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pWinModule`  
 Wskaźnik do modułu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
 `pData`  
 Wskaźnik do [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury inicjowanie i dodany do bieżącego modułu.  
  
 `pObject`  
 Wskaźnik do obiektu **to** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `_AtlCreateWndData` struktury, która jest używana do przechowywania **to** wskaźnika użyta w odwołaniu do wystąpień klas i dodaje go do listy odwołuje się moduł `_ATL_WIN_MODULE70` struktury. Wywoływane przez [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData  
 Wywołanie tej funkcji, aby wyodrębnić istniejące `_AtlCreateWndData` struktury.  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>Parametry  
 `pWinModule`  
 Wskaźnik do modułu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zostanie wyodrębniona istniejące `_AtlCreateWndData` struktury z listy odwołuje się moduł `_ATL_WIN_MODULE70` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
