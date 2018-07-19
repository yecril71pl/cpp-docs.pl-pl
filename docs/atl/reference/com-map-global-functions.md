---
title: Funkcje globalne mapy interfejsu COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a23dc598d499071183cfcf7b0172611a693e569d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884239"
---
# <a name="com-map-global-functions"></a>Funkcje globalne mapy interfejsu COM
Te funkcje umożliwiają mapy interfejsu COM `IUnknown` implementacji.  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje do `IUnknown` nieagregowane obiektu.|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje kod wydajne porównywania interfejsów względem `IUnknown`.|  

  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 *pThis*  
 [in] Wskaźnik do obiektu, która zawiera mapę COM, interfejsów narażonych na `QueryInterface`.  
  
 *pEntries*  
 [in] Tablica `_ATL_INTMAP_ENTRY` struktury, do których dostęp mapę dostępnych interfejsów.  
  
 *IID*  
 [in] Identyfikator GUID interfejsu żądanej.  
  
 *ppvObject*  
 [out] Wskaźnik do wskaźnika interfejsu określonego w *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  
 `AtlInternalQueryInterface` obsługuje tylko interfejsów COM tabeli mapy. Jeśli obiekt jest zagregowany, `AtlInternalQueryInterface` nie delegować do zewnętrznego nieznany. Możesz wprowadzić interfejsy do tabeli mapy COM za pomocą makra [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) lub jedna z jej wariantów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 Wywołaj tę funkcję w specjalnym przypadku sprawdzania pod kątem `IUnknown`.  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>Parametry  
 *rguid1*  
 [in] Identyfikator GUID do porównania z `IID_IUnknown`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra mapy modelu COM](../../atl/reference/com-map-macros.md)
