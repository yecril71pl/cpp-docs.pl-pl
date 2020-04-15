---
title: Makra sterowania złożonego
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331514"
---
# <a name="composite-control-macros"></a>Makra sterowania złożonego

Te makra definiują mapy i wpisy pochłaniania zdarzeń.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Oznacza początek mapy ujścia zdarzeń dla formantu złożonego.|
|[END_SINK_MAP](#end_sink_map)|Oznacza koniec mapy ujścia zdarzeń dla formantu złożonego.|
|[SINK_ENTRY](#sink_entry)|Wejście do mapy ujścia zdarzeń.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Wejście do mapy ujścia zdarzeń z dodatkowym parametrem.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobne do SINK_ENTRY_EX z tą różnicą, że trwa wskaźnik do iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Wejście do mapy ujścia zdarzeń z ręcznie dostarczonymi informacjami o typie do użytku z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobne do SINK_ENTRY_INFO z tą różnicą, że trwa wskaźnik do iid.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

Deklaruje początek mapy ujścia zdarzeń dla formantu złożonego.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[w] Określa formant.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

Deklaruje koniec mapy ujścia zdarzeń dla formantu złożonego.

```
END_SINK_MAP()
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

Deklaruje funkcję obsługi (*fn*) dla określonego zdarzenia (*dispid*), formantu identyfikowanego przez *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikuje formant.

*Dispid*<br/>
[w] Identyfikuje określone zdarzenie.

*Fn*<br/>
[w] Nazwa funkcji obsługi zdarzeń. Ta funkcja musi `_stdcall` używać konwencji wywołującej i mieć odpowiedni podpis w stylu dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX i SINK_ENTRY_EX_P

Deklaruje funkcję obsługi (*fn*) dla określonego zdarzenia (*dispid*), interfejsu wysyłki (*iid*), dla formantu zidentyfikowanego przez *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikuje formant.

*Iid*<br/>
[w] Identyfikuje interfejs wysyłki.

*piid*<br/>
[w] Wskaźnik do interfejsu wysyłki.

*Dispid*<br/>
[w] Identyfikuje określone zdarzenie.

*Fn*<br/>
[w] Nazwa funkcji obsługi zdarzeń. Ta funkcja musi `_stdcall` używać konwencji wywołującej i mieć odpowiedni podpis w stylu dispinterface.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Uwagi

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO i SINK_ENTRY_INFO_P

Użyj makra SINK_ENTRY_INFO w mapie ujścia zdarzeń, aby zapewnić informacje potrzebne przez [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) do kierowania zdarzeń do odpowiedniej funkcji obsługi.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Niepodpisana liczba całkowita identyfikujący źródło zdarzenia. Ta wartość musi być zgodna z parametrem szablonu *nID* używanym w powiązanej klasie podstawowej [IDispEventSimpleImpl.](../../atl/reference/idispeventsimpleimpl-class.md)

*Iid*<br/>
[w] Identyfikator identyfikujący interfejs wysyłki.

*piid*<br/>
[w] Wskaźnik do identyfikatora, który identyfikuje interfejs wysyłki.

*Dispid*<br/>
[w] DISPID identyfikujący określone zdarzenie.

*Fn*<br/>
[w] Nazwa funkcji obsługi zdarzeń. Ta funkcja musi `_stdcall` używać konwencji wywołującej i mieć odpowiedni podpis w stylu dispinterface.

*Informacji*<br/>
[w] Wpisz informacje dla funkcji obsługi zdarzeń. Informacje o typie są dostarczane w `_ATL_FUNC_INFO` postaci wskaźnika do struktury. CC_CDECL jest jedyną opcją obsługiwaną w systemie Windows CE dla `_ATL_FUNC_INFO` pola CALLCONV struktury. Każda inna wartość nie jest podparta w ten sposób jego zachowanie niezdefiniowane.

### <a name="remarks"></a>Uwagi

Pierwsze cztery parametry makr są takie same jak dla [makra SINK_ENTRY_EX.](#sink_entry_ex) Parametr końcowy zawiera informacje o typie zdarzenia. Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne sterowania kompozytowymi](../../atl/reference/composite-control-global-functions.md)
