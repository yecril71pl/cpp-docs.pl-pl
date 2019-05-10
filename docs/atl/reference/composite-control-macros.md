---
title: Makra kontrolek złożonych
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 685bf55910d4746463de30b17b71aa6d246db199
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221102"
---
# <a name="composite-control-macros"></a>Makra kontrolek złożonych

Te makra definiują mapy wychwytywania zdarzeń i zapisy.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Oznacza początek Mapa ujścia zdarzeń dla kontrolek złożonych.|
|[END_SINK_MAP](#end_sink_map)|Oznacza koniec Mapa ujścia zdarzeń dla kontrolek złożonych.|
|[SINK_ENTRY](#sink_entry)|Wpis do mapy obiektu sink zdarzenia.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Wpis do mapy obiektu sink zdarzenia o dodatkowy parametr.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_EX z tą różnicą, że wykorzystuje wskaźnik iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Wpis mapy ujścia zdarzeń za pomocą informacji o typie ręcznie dostarczony do użytku z programem [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_INFO z tą różnicą, że wykorzystuje wskaźnik iid.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

Deklaruje początku Mapa ujścia zdarzeń dla kontrolek złożonych.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[in] Określa kontrolkę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

##  <a name="end_sink_map"></a>  END_SINK_MAP

Deklaruje koniec Mapa ujścia zdarzeń dla kontrolek złożonych.

```
END_SINK_MAP()
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

##  <a name="sink_entry"></a>  SINK_ENTRY

Deklaruje funkcji obsługi (*fn*) dla określonego zdarzenia (*dispid*), kontrolki identyfikowane przez *identyfikator*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikuje formant.

*dispid*<br/>
[in] Identyfikuje określone zdarzenie.

*FN*<br/>
[in] Nazwa funkcji procedury obsługi zdarzeń. Tę funkcję, należy użyć `_stdcall` konwencji wywoływania i mają podpis odpowiedni styl dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX i SINK_ENTRY_EX_P

Deklaruje funkcji obsługi (*fn*) dla określonego zdarzenia (*dispid*), z interfejs ekspedycji (*iid*), dla formantu identyfikowane przez *identyfikator*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikuje formant.

*IID*<br/>
[in] Identyfikuje interfejs ekspedycji.

*piid*<br/>
[in] Wskaźnik do interfejsu wysyłania.

*dispid*<br/>
[in] Identyfikuje określone zdarzenie.

*FN*<br/>
[in] Nazwa funkcji procedury obsługi zdarzeń. Tę funkcję, należy użyć `_stdcall` konwencji wywoływania i mają podpis odpowiedni styl dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

##  <a name="sink_entry_info"></a>  SINK_ENTRY_INFO i SINK_ENTRY_INFO_P

Użyj makra SINK_ENTRY_INFO w mapie obiektu sink zdarzenia, aby Podaj informacje wymagane przez [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) do kierowanie zdarzeń do funkcji odpowiedni program obsługi.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Liczba całkowita bez znaku identyfikacji źródła zdarzenia. Ta wartość musi odpowiadać *nID* parametru szablonu używany w pokrewnym [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy bazowej.

*IID*<br/>
[in] W przypadku identyfikatora IID, który identyfikuje interfejs ekspedycji.

*piid*<br/>
[in] Wskaźnik do identyfikatora IID, który identyfikuje interfejs ekspedycji.

*dispid*<br/>
[in] Identyfikator DISPID identyfikujący określonego zdarzenia.

*FN*<br/>
[in] Nazwa funkcji procedury obsługi zdarzeń. Tę funkcję, należy użyć `_stdcall` konwencji wywoływania i mają podpis odpowiedni styl dispinterface.

*info*<br/>
[in] Wpisz informacje o funkcji procedury obsługi zdarzeń. Informacje o tym typie znajduje się w formularzu wskaźnik do `_ATL_FUNC_INFO` struktury. CC_CDECL jest jedyną opcją, które są obsługiwane w Windows CE dla pola Konwencja WYWOŁANIA `_ATL_FUNC_INFO` struktury. Dowolna inna wartość nie jest obsługiwany związku z tym jego zachowanie jest niezdefiniowane.

### <a name="remarks"></a>Uwagi

Parametry makr pierwsze cztery są takie same jak w przypadku [SINK_ENTRY_EX](#sink_entry_ex) makra. Ostatni parametr zawiera informacje o typie dla zdarzenia. Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne kontrolek złożonych](../../atl/reference/composite-control-global-functions.md)
