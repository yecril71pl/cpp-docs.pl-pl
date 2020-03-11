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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864755"
---
# <a name="idispeventsimpleimpl-class"></a>Klasa IDispEventSimpleImpl

Ta klasa udostępnia implementacje metod `IDispatch` bez uzyskiwania informacji o typie z biblioteki typów.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*nID*<br/>
Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventSimpleImpl` jest klasą bazową dla kontrolki złożonej, użyj identyfikatora zasobu odpowiedniej kontrolki dla tego parametru. W innych przypadkach Użyj dowolnej dodatniej liczby całkowitej.

*&*<br/>
Klasa użytkownika, która jest pochodną `IDispEventSimpleImpl`.

*pdiid*<br/>
Wskaźnik do IID zdarzenia dispinterface zaimplementowane przez tę klasę.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventSimpleImpl:: Advise](#advise)|Ustanawia połączenie z domyślnym źródłem zdarzenia.|
|[IDispEventSimpleImpl::D ispEventAdvise](#dispeventadvise)|Nawiązuje połączenie ze źródłem zdarzenia.|
|[IDispEventSimpleImpl::D ispEventUnadvise](#dispeventunadvise)|Przerywa połączenie ze źródłem zdarzenia.|
|[IDispEventSimpleImpl:: GetIDsOfNames](#getidsofnames)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl::](#gettypeinfo)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Zwraca E_NOTIMPL.|
|[IDispEventSimpleImpl:: Invoke](#invoke)|Wywołuje programy obsługi zdarzeń wymienione na mapie ujścia zdarzeń.|
|[IDispEventSimpleImpl:: Unadvise](#unadvise)|Przerywa połączenie z domyślnym źródłem zdarzenia.|

## <a name="remarks"></a>Uwagi

`IDispEventSimpleImpl` zapewnia sposób implementacji usługi Event dispinterface bez konieczności podawania kodu implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventSimpleImpl` udostępnia implementacje metod `IDispatch`. Musisz podać tylko implementacje dla zdarzeń, które chcesz obsłużyć.

`IDispEventSimpleImpl` działa w połączeniu z mapą ujścia zdarzeń w klasie w celu kierowania zdarzeń do odpowiedniej funkcji obsługi. Aby użyć tej klasy:

- Dodaj makro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) do mapy ujścia zdarzeń dla każdego zdarzenia na każdym obiekcie, który ma być obsługiwany.

- Podaj informacje o typie dla każdego zdarzenia, przekazując wskaźnik do struktury [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) jako parametr do każdego wpisu. Na platformie x86 wartość `_ATL_FUNC_INFO.cc` musi być CC_CDECL przy użyciu funkcji wywołania zwrotnego metody __stdcall.

- Wywołaj [DispEventAdvise](#dispeventadvise) , aby nawiązać połączenie między obiektem źródłowym a klasą bazową.

- Wywołaj [DispEventUnadvise](#dispeventunadvise) , aby przerwać połączenie.

Należy utworzyć od `IDispEventSimpleImpl` (przy użyciu unikatowej wartości dla *NID*) dla każdego obiektu, dla którego należy obsługiwać zdarzenia. Klasy bazowej można użyć ponownie, nie doradzając z jednym obiektem źródłowym, a następnie doradzasz względem innego obiektu źródłowego, ale Maksymalna liczba obiektów źródłowych, które mogą być obsługiwane przez pojedynczy obiekt w jednym czasie, jest ograniczona przez liczbę `IDispEventSimpleImpl` klas podstawowych.

`IDispEventSimplImpl` zapewnia te same funkcje co [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), z wyjątkiem tego, że nie pobiera on informacji o interfejsie z biblioteki typów. Kreatorzy generują kod na podstawie `IDispEventImpl`, ale można użyć `IDispEventSimpleImpl`, dodając kod ręcznie. Użyj `IDispEventSimpleImpl`, jeśli nie masz biblioteki typów opisującej interfejs zdarzenia lub chcesz uniknąć narzutu związanego z korzystaniem z biblioteki typów.

> [!NOTE]
> `IDispEventImpl` i `IDispEventSimpleImpl` zapewniają własną implementację `IUnknown::QueryInterface` włączania każdej `IDispEventImpl` lub `IDispEventSimpleImpl` klasę bazową, aby działała jako oddzielna tożsamość COM, jednocześnie zapewniając bezpośredni dostęp do elementów członkowskich klasy w głównym obiekcie COM.

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

Aby uzyskać więcej informacji, zobacz temat [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="advise"></a>IDispEventSimpleImpl:: Advise

Wywołaj tę metodę, aby nawiązać połączenie ze źródłem zdarzenia reprezentowanego przez *punkt*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do interfejsu `IUnknown` obiektu źródła zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub jakakolwiek wartość HRESULT błędu.

### <a name="remarks"></a>Uwagi

Po nawiązaniu połączenia zdarzenia wywoływane z obszaru *punktowego* są kierowane do programów obsługi w klasie w formie mapy ujścia zdarzeń.

> [!NOTE]
>  Jeśli klasa pochodzi z wielu klas `IDispEventSimpleImpl`, należy rozróżnić wywołania tej metody przez przeznaczanie wywołania z konkretną klasą bazową, która Cię interesuje.

`Advise` nawiązuje połączenie z domyślnym źródłem zdarzeń, pobiera identyfikator IID domyślnego źródła zdarzeń obiektu określonego przez [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::D ispEventAdvise

Wywołaj tę metodę, aby nawiązać połączenie ze źródłem zdarzenia reprezentowanego przez *punkt*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do interfejsu `IUnknown` obiektu źródła zdarzenia.

*piid*<br/>
Wskaźnik do IID obiektu źródła zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub jakakolwiek wartość HRESULT błędu.

### <a name="remarks"></a>Uwagi

Następnie zdarzenia wywoływane z obszaru *punktowego* są kierowane do programów obsługi w klasie w formie mapy ujścia zdarzeń.

> [!NOTE]
>  Jeśli klasa pochodzi z wielu klas `IDispEventSimpleImpl`, należy rozróżnić wywołania tej metody przez przeznaczanie wywołania z konkretną klasą bazową, która Cię interesuje.

`DispEventAdvise` nawiązuje połączenie ze źródłem zdarzenia określonym w `pdiid`.

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::D ispEventUnadvise

Przerywa połączenie ze źródłem zdarzenia reprezentowanego przez *punkt*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do interfejsu `IUnknown` obiektu źródła zdarzenia.

*piid*<br/>
Wskaźnik do IID obiektu źródła zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub jakakolwiek wartość HRESULT błędu.

### <a name="remarks"></a>Uwagi

Po zerwaniu połączenia zdarzenia nie będą już kierowane do funkcji obsługi wymienionych na mapie ujścia zdarzeń.

> [!NOTE]
>  Jeśli klasa pochodzi z wielu klas `IDispEventSimpleImpl`, należy rozróżnić wywołania tej metody przez przeznaczanie wywołania z konkretną klasą bazową, która Cię interesuje.

`DispEventAdvise` przerywa połączenie, które zostało nawiązane ze źródłem zdarzenia określonym w `pdiid`.

##  <a name="getidsofnames"></a>IDispEventSimpleImpl:: GetIDsOfNames

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

Zobacz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.

##  <a name="gettypeinfo"></a>IDispEventSimpleImpl::

Ta implementacja `IDispatch::GetTypeInfo` zwraca E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w Windows SDK.

##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Ta implementacja `IDispatch::GetTypeInfoCount` zwraca E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w Windows SDK.

##  <a name="invoke"></a>IDispEventSimpleImpl:: Invoke

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

Zobacz [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>IDispEventSimpleImpl:: Unadvise

Przerywa połączenie ze źródłem zdarzenia reprezentowanego przez *punkt*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do interfejsu `IUnknown` obiektu źródła zdarzenia.

### <a name="return-value"></a>Wartość zwracana

S_OK lub jakakolwiek wartość HRESULT błędu.

### <a name="remarks"></a>Uwagi

Po zerwaniu połączenia zdarzenia nie będą już kierowane do funkcji obsługi wymienionych na mapie ujścia zdarzeń.

> [!NOTE]
>  Jeśli klasa pochodzi z wielu klas `IDispEventSimpleImpl`, należy rozróżnić wywołania tej metody przez przeznaczanie wywołania z konkretną klasą bazową, która Cię interesuje.

`Unadvise` przerywa połączenie, które zostało nawiązane z domyślnym źródłem zdarzenia określonym w `pdiid`.

`Unavise` przerywa połączenie z domyślnym źródłem zdarzeń, pobiera identyfikator IID domyślnego źródła zdarzeń obiektu określonego przez [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Zobacz także

[Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Klasa IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
