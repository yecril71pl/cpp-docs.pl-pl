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
ms.openlocfilehash: 1578518b8918f59b1da54f474e82cf899f3c76f6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285545"
---
# <a name="idispeventsimpleimpl-class"></a>Klasa IDispEventSimpleImpl

Ta klasa zawiera implementacje `IDispatch` metody bez pobierania informacji o typie z biblioteki typów.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*nID*<br/>
Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventSimpleImpl` jest klasą bazową dla kontrolki złożonej, skorzystaj z zasobów żądaną kontrolki zawartej dla tego parametru. W innych przypadkach należy użyć dowolną dodatnią liczbą całkowitą.

*T*<br/>
Klasa użytkownika, która jest pochodną `IDispEventSimpleImpl`.

*pdiid*<br/>
Wskaźnik do identyfikatora IID z Interfejs rozdzielania zdarzeń, zaimplementowane przez tę klasę.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Ustanawia połączenie z domyślnego źródła zdarzeń.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Nawiązuje połączenie ze źródłem zdarzeń.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Przerywa połączenie ze źródłem zdarzeń.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Returns E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Returns E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Returns E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Wywołania procedur obsługi zdarzeń w zdarzeniu wymienione mapy ujścia.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Przerywa połączenie z domyślnego źródła zdarzeń.|

## <a name="remarks"></a>Uwagi

`IDispEventSimpleImpl` zapewnia sposób implementowania Interfejs rozdzielania zdarzeń bez konieczności podać kod implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventSimpleImpl` zawiera implementacje `IDispatch` metody. Musisz podać implementacje dla zdarzenia wybrane w obsłudze.

`IDispEventSimpleImpl` działa w połączeniu z mapą obiekt sink zdarzenia w klasie do kierowanie zdarzeń do funkcji odpowiedni program obsługi. Aby użyć tej klasy:

- Dodaj [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makra do mapy obiektu sink zdarzenia dla każdego zdarzenia dla każdego obiektu, który chcesz obsługiwać.

- Podaj informacje o typie dla każdego zdarzenia, przekazując wskaźnik do [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) strukturę jako parametr do każdego wpisu. Na x86 platformy `_ATL_FUNC_INFO.cc` wartość musi być CC_CDECL za pomocą funkcji wywołania zwrotnego, wywołanie metody __stdcall.

- Wywołaj [DispEventAdvise](#dispeventadvise) do nawiązywania połączenia między obiektu źródłowego oraz klasy bazowej.

- Wywołaj [DispEventUnadvise](#dispeventunadvise) aby przerwać połączenie.

Muszą pochodzić od `IDispEventSimpleImpl` (przy użyciu unikatową wartość dla *nID*) dla każdego obiektu, dla których potrzebujesz do obsługi zdarzeń. Można ponownie użyć klasy bazowej przez unadvising względem obiektu jednego źródła, następnie wniosku względem obiektu innego źródła, ale maksymalna liczba obiektów źródłowej, które są obsługiwane przez pojedynczy obiekt w tym samym czasie, jest ograniczona przez liczbę `IDispEventSimpleImpl` klas bazowych.

`IDispEventSimplImpl` udostępnia taką samą funkcjonalność jak [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), z wyjątkiem nie uzyskać typ informacji na temat interfejsu z biblioteki typów. Kreatorzy wygenerowanie kodu opartego tylko na `IDispEventImpl`, ale można użyć `IDispEventSimpleImpl` , dodając kod ręcznie. Użyj `IDispEventSimpleImpl` po nie mają bibliotekę typów, opisujący interfejs zdarzenia lub aby uniknąć obciążenia związanego z używaniem biblioteki typów.

> [!NOTE]
> `IDispEventImpl` i `IDispEventSimpleImpl` zapewniali własną implementację programu `IUnknown::QueryInterface` włączania każdej `IDispEventImpl` lub `IDispEventSimpleImpl` klasy bazowej na działania jako osobne tożsamości COM wciąż zezwalając bezpośredni dostęp do elementów członkowskich klasy w głównym obiektu COM.

Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.

Aby uzyskać więcej informacji, zobacz [Obsługa interfejsu IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

Wywołaj tę metodę w celu nawiązania połączenia ze źródłem zdarzeń, reprezentowane przez *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` interfejs zdarzenia obiektu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Lub jakiekolwiek niepowodzenie wartość HRESULT S_OK.

### <a name="remarks"></a>Uwagi

Po nawiązaniu połączenia zdarzeń wyzwalanych z *pUnk* będą kierowane do obsługi w klasie za pomocą mapy obiektu sink zdarzenia.

> [!NOTE]
>  Jeśli klasa jest pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnić wywołania tej metody, zakresu wywołań za pomocą konkretnej klasy bazowej Cię interesuje.

`Advise` nawiązuje połączenie z domyślnego źródła zdarzeń, otrzymuje identyfikator IID źródła zdarzeń do domyślnego obiektu zgodnie z ustaleniami [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

Wywołaj tę metodę w celu nawiązania połączenia ze źródłem zdarzeń, reprezentowane przez *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` interfejs zdarzenia obiektu źródłowego.

*piid*<br/>
Wskaźnik do identyfikatora IID obiektu źródła zdarzeń.

### <a name="return-value"></a>Wartość zwracana

Lub jakiekolwiek niepowodzenie wartość HRESULT S_OK.

### <a name="remarks"></a>Uwagi

Następnie zdarzeń wyzwalanych z *pUnk* będą kierowane do obsługi w klasie za pomocą mapy obiektu sink zdarzenia.

> [!NOTE]
>  Jeśli klasa jest pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnić wywołania tej metody, zakresu wywołań za pomocą konkretnej klasy bazowej Cię interesuje.

`DispEventAdvise` nawiązuje połączenie ze źródłem zdarzeń określony w `pdiid`.

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

Przerywa połączenie ze źródłem zdarzeń, reprezentowane przez *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` interfejs zdarzenia obiektu źródłowego.

*piid*<br/>
Wskaźnik do identyfikatora IID obiektu źródła zdarzeń.

### <a name="return-value"></a>Wartość zwracana

Lub jakiekolwiek niepowodzenie wartość HRESULT S_OK.

### <a name="remarks"></a>Uwagi

Gdy połączenie zostanie przerwane, zdarzenia nie są już będą kierowane do funkcji obsługi wymienionych na mapie obiektu sink zdarzenia.

> [!NOTE]
>  Jeśli klasa jest pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnić wywołania tej metody, zakresu wywołań za pomocą konkretnej klasy bazowej Cię interesuje.

`DispEventAdvise` przerywa połączenie, który został ustanowiony ze źródłem zdarzeń określony w `pdiid`.

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

Ta implementacja `IDispatch::GetIDsOfNames` zwraca E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Ta implementacja `IDispatch::GetTypeInfo` zwraca E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Ta implementacja `IDispatch::GetTypeInfoCount` zwraca E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w Windows SDK.

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

Ta implementacja `IDispatch::Invoke` wywołania procedur obsługi zdarzeń wymienionych w zdarzeniu mapy ujścia.

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

Zobacz [uwzględniając](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

Przerywa połączenie ze źródłem zdarzeń, reprezentowane przez *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` interfejs zdarzenia obiektu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Lub jakiekolwiek niepowodzenie wartość HRESULT S_OK.

### <a name="remarks"></a>Uwagi

Gdy połączenie zostanie przerwane, zdarzenia nie są już będą kierowane do funkcji obsługi wymienionych na mapie obiektu sink zdarzenia.

> [!NOTE]
>  Jeśli klasa jest pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnić wywołania tej metody, zakresu wywołań za pomocą konkretnej klasy bazowej Cię interesuje.

`Unadvise` przerywa połączenie ustanowione za pomocą domyślnego źródła zdarzeń określony w `pdiid`.

`Unavise` podziały połączenia z domyślnego źródła zdarzeń, otrzymuje identyfikator IID źródła zdarzeń do domyślnego obiektu zgodnie z ustaleniami [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Zobacz także

[Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Klasa IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
