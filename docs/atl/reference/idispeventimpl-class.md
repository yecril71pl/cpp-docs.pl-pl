---
title: Klasa IDispEventImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329758"
---
# <a name="idispeventimpl-class"></a>Klasa IDispEventImpl

Ta klasa zawiera implementacje `IDispatch` metod.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parametry

*Nid*<br/>
Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventImpl` jest klasą podstawową dla formantu złożonego, należy użyć identyfikatora zasobu żądanego formantu zawartego dla tego parametru. W innych przypadkach należy użyć dowolnej dodatniej liczby całkowitej.

*T*<br/>
Klasa użytkownika, która pochodzi od `IDispEventImpl`.

*pdiid*<br/>
Wskaźnik do IID dispinterface zdarzenia zaimplementowane przez tę klasę. Ten interfejs musi być zdefiniowany w bibliotece typów oznaczonych przez *plibid*, *wMajor*i *wMinor*.

*plibid ( plibid )*<br/>
Wskaźnik do biblioteki typów definiujący interfejs wysyłki wskazywanie przez *pdiid*. Jeśli **&GUID_NULL,** biblioteka typów zostanie załadowana z obiektu zaopatrującego się w zdarzenia.

*wMajor*<br/>
Główna wersja biblioteki typów. Wartość domyślna to 0.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass (klasa tihclass)*<br/>
Klasa używana do zarządzania informacjami o typie *dla T*. Wartość domyślna to klasa `CComTypeInfoHolder`typu; można jednak zastąpić ten parametr szablonu, podając klasę `CComTypeInfoHolder`typu innego niż .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Klasa używana do zarządzania informacjami o typie. Domyślnie `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Lokalizuje indeks funkcji dla określonego identyfikatora wysyłki.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje pojedynczy element członkowski i opcjonalny zestaw nazw argumentów do odpowiedniego zestawu identyfikatorów DISPIDów całkowitych.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie obiektu.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę interfejsów informacji o typie.|
|[IDispEventImpl::GetUserDefdefedType](#getuserdefinedtype)|Pobiera podstawowy typ typu zdefiniowanego przez użytkownika.|

## <a name="remarks"></a>Uwagi

`IDispEventImpl`zapewnia sposób implementacji dispinterface zdarzenia bez konieczności dostarczania kodu implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventImpl`zapewnia implementacje `IDispatch` metod. Wystarczy tylko podać implementacje dla zdarzeń, które są zainteresowane obsługą.

`IDispEventImpl`działa w połączeniu z mapą ujścia zdarzeń w klasie, aby kierować zdarzenia do odpowiedniej funkcji obsługi. Aby użyć tej klasy:

Dodaj [makro SINK_ENTRY](composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) do mapy ujścia zdarzeń dla każdego zdarzenia na każdym obiekcie, który ma być obsługiwany. Korzystając `IDispEventImpl` jako klasa podstawowa formantu złożonego, można wywołać [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) ustanowić i przerwać połączenie ze źródłami zdarzeń dla wszystkich wpisów na mapie ujścia zdarzeń. W innych przypadkach lub dla większej kontroli wywołać [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) ustanowić połączenie między obiektem źródłowym i klasy podstawowej. Wywołanie [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) wobec łamać ten połączenie.

Należy wyprowadzić `IDispEventImpl` z (przy użyciu unikatowej wartości dla *nID)* dla każdego obiektu, dla którego należy obsługiwać zdarzenia. Klasy podstawowej można ponownie użyć, nienadzorując względem jednego obiektu źródłowego, a następnie doradzając przeciwko innemu obiektowi źródłnemu, ale maksymalna `IDispEventImpl` liczba obiektów źródłowych, które mogą być obsługiwane przez pojedynczy obiekt w tym samym czasie, jest ograniczona przez liczbę klas podstawowych.

`IDispEventImpl`zapewnia taką samą funkcjonalność jak [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), z tą różnicą, że pobiera informacje o typie interfejsu z biblioteki typów, a nie o to jako wskaźnik do struktury [_ATL_FUNC_INFO.](../../atl/reference/atl-func-info-structure.md) Użyj, `IDispEventSimpleImpl` gdy nie masz biblioteki typów opisujące interfejs zdarzeń lub chcesz uniknąć narzutu związanego z przy użyciu biblioteki typów.

> [!NOTE]
> `IDispEventImpl`i `IDispEventSimpleImpl` zapewnić własną `IUnknown::QueryInterface` implementację `IDispEventImpl` umożliwiając `IDispEventSimpleImpl` każdej i klasy podstawowej do działania jako oddzielne tożsamości COM, a jednocześnie umożliwia bezpośredni dostęp do członków klasy w głównym obiekcie COM.

Implementacja CE ATL pochłaniaczy zdarzeń ActiveX obsługuje tylko zwracane wartości typu HRESULT lub void z metod obsługi zdarzeń; każda inna wartość zwracana jest nieobsługiwała, a jej zachowanie jest niezdefiniowane.

Aby uzyskać więcej informacji, zobacz [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_IDispEvent`

`_IDispEventLocator`

[Idispeventsimpleimpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId

Lokalizuje indeks funkcji dla określonego identyfikatora wysyłki.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Odwołanie do identyfikatora funkcji.

*dispidMember*<br/>
[w] Identyfikator wysyłki funkcji.

*lcid*<br/>
[w] Kontekst ustawień regionalnych identyfikatora funkcji.

*Informacji*<br/>
[w] Struktura wskazująca, jak funkcja jest wywoływana.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames

Mapuje pojedynczy element członkowski i opcjonalny zestaw nazw argumentów do odpowiedniego zestawu identyfikatorów DISPI, które mogą być używane w kolejnych wywołaniach [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) w usłudze Windows SDK.

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo

Pobiera informacje o typie dla obiektu, których następnie można użyć do uzyskania informacji o typie interfejsu.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount

Pobiera informację o liczbie typów interfejsów, jakie zawiera obiekt (0 lub 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w usłudze Windows SDK.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefdefedType

Pobiera podstawowy typ typu zdefiniowanego przez użytkownika.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parametry

*Pti*<br/>
[w] Wskaźnik do interfejsu [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) zawierający typ zdefiniowany przez użytkownika.

*Htz*<br/>
[w] Dojście do opisu typu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Typ wariantu.

### <a name="remarks"></a>Uwagi

Zobacz [ITypeInfo::GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl

Konstruktor. Przechowuje wartości parametrów szablonu klasy *plibid*, *pdiid*, *wMajor*i *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

Ten typedef jest wystąpieniem parametru szablonu klasy *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Uwagi

Domyślnie klasą `CComTypeInfoHolder`jest . `CComTypeInfoHolder`zarządza informacjami o typie dla klasy.

## <a name="see-also"></a>Zobacz też

[Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
