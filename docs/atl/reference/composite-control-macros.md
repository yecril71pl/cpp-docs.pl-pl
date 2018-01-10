---
title: "Makra formantu złożonego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
dev_langs: C++
helpviewer_keywords: composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b609801a1716e47b208644be02d4746abf8c288a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="composite-control-macros"></a>Makra złożonych kontrolek
Te makra zdefiniuj mapy wychwytywania zdarzeń i zapisów.  
  
|||  
|-|-|  
|[BEGIN_SINK_MAP](#begin_sink_map)|Oznacza początek mapy obiekt sink zdarzenia dla formantu złożonego.|  
|[END_SINK_MAP](#end_sink_map)|Oznacza koniec mapy obiekt sink zdarzenia dla formantu złożonego.|  
|[SINK_ENTRY](#sink_entry)|Wpis mapy obiekt sink zdarzenia.|  
|[SINK_ENTRY_EX](#sink_entry_ex)|Wpis mapy obiekt sink zdarzenia z dodatkowy parametr.| 
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_EX z tym że jej wskaźnik do identyfikatora iid.|  
|[SINK_ENTRY_INFO](#sink_entry_info)|Wpis do mapy obiekt sink zdarzenia ręcznie podanego typu informacji do użycia z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|  
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_INFO z tym że jej wskaźnik do identyfikatora iid.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP  
 Deklaruje początku mapy obiekt sink zdarzenia dla formantu złożonego.  
  
```
BEGIN_SINK_MAP(_class)
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [in] Określa formant.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Uwagi  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
##  <a name="end_sink_map"></a>END_SINK_MAP  
 Deklaruje koniec mapy obiekt sink zdarzenia dla formantu złożonego.  
  
```
END_SINK_MAP()
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Uwagi  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
##  <a name="sink_entry"></a>SINK_ENTRY  
 Deklaruje funkcji obsługi ( `fn`) dla określonego zdarzenia ( `dispid`), formantu identyfikowane przez `id`.  
  
```
SINK_ENTRY( id, dispid, fn )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikuje formant.  
  
 `dispid`  
 [in] Identyfikuje określone zdarzenie.  
  
 `fn`  
 [in] Nazwa funkcji programu obsługi zdarzeń. Należy użyć tej funkcji **_stdcall** konwencji wywoływania i ma odpowiedni styl dispinterface podpisu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Uwagi  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX i SINK_ENTRY_EX_P
 Deklaruje funkcji obsługi ( `fn`) dla określonego zdarzenia ( `dispid`), interfejsu wysyłania ( *iid)*, formantu identyfikowane przez `id`.  
  
```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikuje formant.  
  
 `iid`  
 [in] Określa interfejs wysyłania.  

 `piid`  
 [in] Wskaźnik do interfejsu wysyłania.  
  
 `dispid`  
 [in] Identyfikuje określone zdarzenie.  
  
 `fn`  
 [in] Nazwa funkcji programu obsługi zdarzeń. Należy użyć tej funkcji **_stdcall** konwencji wywoływania i ma odpowiedni styl dispinterface podpisu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]  
  
### <a name="remarks"></a>Uwagi  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO i SINK_ENTRY_INFO_P  
 Użyj `SINK_ENTRY_INFO` makra w mapie obiekt sink zdarzenia o podanie informacji wymaganych przez [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) zdarzeń trasy do obsługi odpowiednich funkcji.  
  
```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Liczba całkowita bez znaku identyfikacji źródła zdarzenia. Ta wartość musi być zgodna `nID` parametru szablonu użytego w odnośnych [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy podstawowej.  
  
 `iid`  
 [in] Identyfikator IID, który identyfikuje interfejs wysyłania.  

 `piid`  
 [in] Wskaźnik do identyfikatora IID, który identyfikuje interfejs wysyłania.
  
 `dispid`  
 [in] Identyfikator DISPID identyfikujący określonego zdarzenia.  
  
 `fn`  
 [in] Nazwa funkcji programu obsługi zdarzeń. Należy użyć tej funkcji **_stdcall** konwencji wywoływania i ma odpowiedni styl dispinterface podpisu.  
  
 `info`  
 [in] Wpisywanie informacji o funkcji procedury obsługi zdarzeń. Tego typu informacje w formularzu wskaźnik do `_ATL_FUNC_INFO` struktury. `CC_CDECL`jest to jedyna opcja obsługiwana w systemie Windows CE dla `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Wszelkie inne wartości są nieobsługiwane w związku z tym niezdefiniowane zachowanie.  
  
### <a name="remarks"></a>Uwagi  
 Makro pierwsze cztery parametry są takie same jak te dotyczące [SINK_ENTRY_EX](#sink_entry_ex) makra. Ostatni parametr zawiera informacje o typie dla zdarzenia. Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  

## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)   
 [Funkcje globalne kontrolek złożonych](../../atl/reference/composite-control-global-functions.md)
