---
title: Klasa IDispEventSimpleImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329739"
---
# <a name="idispeventsimpleimpl-class"></a>Klasa IDispEventSimpleImpl

Ta klasa zawiera implementacje `IDispatch` metod, bez uzyskiwania informacji o typie z biblioteki typów.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*Nid*<br/>
Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventSimpleImpl` jest klasą podstawową dla formantu złożonego, należy użyć identyfikatora zasobu żądanego formantu zawartego dla tego parametru. W innych przypadkach należy użyć dowolnej dodatniej liczby całkowitej.

*T*<br/>
Klasa użytkownika, która pochodzi od `IDispEventSimpleImpl`.

*pdiid*<br/>
Wskaźnik do IID dispinterface zdarzenia zaimplementowane przez tę klasę.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventSimpleImpl::Doradzić](#advise)|Ustanawia połączenie z domyślnym źródłem zdarzeń.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Ustanawia połączenie ze źródłem zdarzenia.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Przerywa połączenie ze źródłem zdarzenia.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl::Wywołaj](#invoke)|Wywołuje programy obsługi zdarzeń wymienione na mapie ujścia zdarzeń.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Przerywa połączenie z domyślnym źródłem zdarzeń.|

## <a name="remarks"></a>Uwagi

`IDispEventSimpleImpl`zapewnia sposób implementacji dispinterface zdarzenia bez konieczności dostarczania kodu implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventSimpleImpl`zapewnia implementacje `IDispatch` metod. Wystarczy tylko podać implementacje dla zdarzeń, które są zainteresowane obsługą.

`IDispEventSimpleImpl`działa w połączeniu z mapą ujścia zdarzeń w klasie, aby kierować zdarzenia do odpowiedniej funkcji obsługi. Aby użyć tej klasy:

- Dodaj [makro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) do mapy ujścia zdarzeń dla każdego zdarzenia na każdym obiekcie, który chcesz obsłużyć.

- Informacje o typie zasilania dla każdego zdarzenia, przekazując wskaźnik do struktury [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) jako parametr do każdego wpisu. Na platformie x86 `_ATL_FUNC_INFO.cc` wartość musi być CC_CDECL z funkcją wywołania zwrotnego wywołaną metodą __stdcall.

- Wywołanie [DispEventAdvise](#dispeventadvise) ustanowić połączenie między obiektem źródłowym i klasy podstawowej.

- Wywołanie [DispEventUnadvise](#dispeventunadvise) wobec łamać ten połączenie.

Należy wyprowadzić `IDispEventSimpleImpl` z (przy użyciu unikatowej wartości dla *nID)* dla każdego obiektu, dla którego należy obsługiwać zdarzenia. Klasy podstawowej można ponownie użyć, nienadzorując względem jednego obiektu źródłowego, a następnie doradzając przeciwko innemu obiektowi źródłnemu, ale maksymalna `IDispEventSimpleImpl` liczba obiektów źródłowych, które mogą być obsługiwane przez pojedynczy obiekt w tym samym czasie, jest ograniczona przez liczbę klas podstawowych.

`IDispEventSimplImpl`zapewnia taką samą funkcjonalność jak [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), z tą różnicą, że nie otrzymuje informacji o typie interfejsu z biblioteki typów. Kreatorzy generują kod tylko `IDispEventImpl`na podstawie `IDispEventSimpleImpl` programu , ale można ich użyć, dodając kod ręcznie. Użyj, `IDispEventSimpleImpl` gdy nie masz biblioteki typów opisujące interfejs zdarzeń lub chcesz uniknąć narzutu związanego z przy użyciu biblioteki typów.

> [!NOTE]
> `IDispEventImpl`i `IDispEventSimpleImpl` zapewnić własną `IUnknown::QueryInterface` implementację `IDispEventImpl` umożliwiając `IDispEventSimpleImpl` każdej lub podstawowej klasy do działania jako oddzielne tożsamości COM, a jednocześnie umożliwia bezpośredni dostęp do członków klasy w głównym obiekcie COM.

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

Aby uzyskać więcej informacji, zobacz [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Doradzić

Wywołanie tej metody, aby ustanowić połączenie ze źródłem zdarzeń reprezentowane przez *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu źródłowego zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub awarię wartości HRESULT.

### <a name="remarks"></a>Uwagi

Po nawiązaniu połączenia zdarzenia uruchamiane z *pUnk* zostaną przekierowane do programów obsługi w klasie za pomocą mapy ujścia zdarzeń.

> [!NOTE]
> Jeśli klasa pochodzi z `IDispEventSimpleImpl` wielu klas, należy rozróżniać wywołania tej metody przez określanie zakresu wywołania z określonej klasy podstawowej, które są interesujące.

`Advise`ustanawia połączenie z domyślnym źródłem zdarzeń, pobiera identyfikator domyślnego źródła zdarzeń obiektu, zgodnie z ustaleniami [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise

Wywołanie tej metody, aby ustanowić połączenie ze źródłem zdarzeń reprezentowane przez *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu źródłowego zdarzenia.

*piid*<br/>
Wskaźnik do identyfikatora obiektu źródłowego zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub awarię wartości HRESULT.

### <a name="remarks"></a>Uwagi

Następnie zdarzenia uruchamiane z *pUnk* będą kierowane do programów obsługi w klasie za pomocą mapy ujścia zdarzeń.

> [!NOTE]
> Jeśli klasa pochodzi z `IDispEventSimpleImpl` wielu klas, należy rozróżniać wywołania tej metody przez określanie zakresu wywołania z określonej klasy podstawowej, które są interesujące.

`DispEventAdvise`ustanawia połączenie ze źródłem zdarzeń `pdiid`określonym w .

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise

Przerywa połączenie ze źródłem zdarzenia reprezentowanym przez *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu źródłowego zdarzenia.

*piid*<br/>
Wskaźnik do identyfikatora obiektu źródłowego zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub awarię wartości HRESULT.

### <a name="remarks"></a>Uwagi

Po przerwaniu połączenia zdarzenia nie będą już kierowane do funkcji obsługi wymienionych na mapie ujścia zdarzeń.

> [!NOTE]
> Jeśli klasa pochodzi z `IDispEventSimpleImpl` wielu klas, należy rozróżniać wywołania tej metody przez określanie zakresu wywołania z określonej klasy podstawowej, które są interesujące.

`DispEventAdvise`przerywa połączenie, które zostało nawiązane `pdiid`ze źródłem zdarzeń określonym w .

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames

Ta implementacja E_NOTIMPL powrotów. `IDispatch::GetIDsOfNames`

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) w usłudze Windows SDK.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo

Ta implementacja E_NOTIMPL powrotów. `IDispatch::GetTypeInfo`

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w usłudze Windows SDK.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Ta implementacja E_NOTIMPL powrotów. `IDispatch::GetTypeInfoCount`

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w usłudze Windows SDK.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Wywołaj

Ta implementacja `IDispatch::Invoke` wywołuje programy obsługi zdarzeń wymienione na mapie ujścia zdarzeń.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise

Przerywa połączenie ze źródłem zdarzenia reprezentowanym przez *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu źródłowego zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub awarię wartości HRESULT.

### <a name="remarks"></a>Uwagi

Po przerwaniu połączenia zdarzenia nie będą już kierowane do funkcji obsługi wymienionych na mapie ujścia zdarzeń.

> [!NOTE]
> Jeśli klasa pochodzi z `IDispEventSimpleImpl` wielu klas, należy rozróżniać wywołania tej metody przez określanie zakresu wywołania z określonej klasy podstawowej, które są interesujące.

`Unadvise`przerywa połączenie, które zostało nawiązane z `pdiid`domyślnym źródłem zdarzeń określonym w .

`Unavise`przerywa połączenie z domyślnym źródłem zdarzeń, pobiera identyfikator domyślnego źródła zdarzeń obiektu określonego przez [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Zobacz też

[Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Klasa IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
