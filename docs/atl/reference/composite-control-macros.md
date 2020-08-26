---
title: Makra kontroli złożonej
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 7ac13a11646faca53b38ec610dc0388bdd14d251
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833546"
---
# <a name="composite-control-macros"></a>Makra kontroli złożonej

Te makra definiują mapy i wpisy ujścia zdarzeń.

|Makro|Opis|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Oznacza początek mapy ujścia zdarzeń dla formantu złożonego.|
|[END_SINK_MAP](#end_sink_map)|Oznacza koniec mapy ujścia zdarzeń dla kontrolki złożonej.|
|[SINK_ENTRY](#sink_entry)|Wpis do mapy ujścia zdarzeń.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Wpis do mapy ujścia zdarzeń z dodatkowym parametrem.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_EX, z tą różnicą, że Pobiera wskaźnik do IID.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Wpis do mapy ujścia zdarzeń z ręcznie dostarczonymi informacjami o typie do użycia z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobnie jak SINK_ENTRY_INFO, z tą różnicą, że Pobiera wskaźnik do IID.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

Deklaruje początek mapy ujścia zdarzeń dla formantu złożonego.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
podczas Określa kontrolkę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

Deklaruje koniec mapy ujścia zdarzeń dla formantu złożonego.

```
END_SINK_MAP()
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

Deklaruje funkcję procedury obsługi (*Fn*) dla określonego zdarzenia (*DISPID*) dla kontrolki identyfikowanej przez *Identyfikator*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikuje formant.

*DISPID*<br/>
podczas Identyfikuje określone zdarzenie.

*Fn*<br/>
podczas Nazwa funkcji obsługi zdarzeń. Ta funkcja musi używać `_stdcall` konwencji wywoływania i mieć odpowiedni podpis w stylu dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX i SINK_ENTRY_EX_P

Deklaruje funkcję procedury obsługi (*Fn*) dla określonego zdarzenia (*DISPID*) w interfejsie wysyłania (*IID*) dla kontrolki identyfikowanej przez *Identyfikator*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikuje formant.

*IID*<br/>
podczas Identyfikuje interfejs wysyłania.

*piid*<br/>
podczas Wskaźnik do interfejsu wysyłania.

*DISPID*<br/>
podczas Identyfikuje określone zdarzenie.

*Fn*<br/>
podczas Nazwa funkcji obsługi zdarzeń. Ta funkcja musi używać `_stdcall` konwencji wywoływania i mieć odpowiedni podpis w stylu dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Uwagi

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO i SINK_ENTRY_INFO_P

Użyj makra SINK_ENTRY_INFO w ramach mapy ujścia zdarzeń, aby podać informacje wymagane przez [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) do kierowania zdarzeń do odpowiedniej funkcji procedury obsługi.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Liczba całkowita bez znaku identyfikująca Źródło zdarzenia. Ta wartość musi być zgodna z parametrem szablonu *NID* używanym w powiązanej klasie podstawowej [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) .

*IID*<br/>
podczas Identyfikator IID identyfikujący interfejs wysyłania.

*piid*<br/>
podczas Wskaźnik do IID identyfikujący interfejs wysyłania.

*DISPID*<br/>
podczas Identyfikator DISPID identyfikujący określone zdarzenie.

*Fn*<br/>
podczas Nazwa funkcji obsługi zdarzeń. Ta funkcja musi używać `_stdcall` konwencji wywoływania i mieć odpowiedni podpis w stylu dispinterface.

*informacje*<br/>
podczas Informacje o typie funkcji obsługi zdarzeń. Te informacje o typie są dostępne w formie wskaźnika do `_ATL_FUNC_INFO` struktury. CC_CDECL jest jedyną opcją obsługiwaną w Windows CE dla pola CALLCONV `_ATL_FUNC_INFO` struktury. Wszystkie inne wartości są nieobsługiwane w tym przypadku, gdy zachowanie nie jest zdefiniowane.

### <a name="remarks"></a>Uwagi

Pierwsze cztery parametry makr są takie same jak dla makra [SINK_ENTRY_EX](#sink_entry_ex) . Końcowy parametr zawiera informacje o typie dla zdarzenia. Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne kontrolki złożonej](../../atl/reference/composite-control-global-functions.md)
