---
title: Funkcje globalne mapie modelu COM | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 509479a923203acd80eaac1ef90aa64125d208c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="com-map-global-functions"></a>Funkcje globalne mapie modelu COM
Funkcje te zapewniają obsługę dla modelu COM mapy **IUnknown** implementacji.  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje do **IUnknown** nieagregowane obiektu.|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje kod wydajne porównywania interfejsy przed **IUnknown**.|  

  
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
 `pThis`  
 [in] Wskaźnik do obiektu zawierającego interfejsów narażonych na mapie modelu COM `QueryInterface`.  
  
 `pEntries`  
 [in] Tablica **_ATL_INTMAP_ENTRY** struktur, które uzyskują dostęp do map interfejsów dostępne.  
  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu określonego w `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `AtlInternalQueryInterface` Obsługuje tylko interfejsy COM tabeli mapy. Jeśli obiekt jest agregowana, `AtlInternalQueryInterface` nie delegować do zewnętrznego nieznany. Interfejsy można wprowadzić do tabeli mapy COM z makra [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) lub jednej z jej wariantów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 Wywołanie tej funkcji w przypadku specjalne testowanie pod kątem **IUnknown**.  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>Parametry  
 *rguid1*  
 [in] Identyfikator GUID do porównania **IID_IUnknown**.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra mapy modelu COM](../../atl/reference/com-map-macros.md)
