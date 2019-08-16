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
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495931"
---
# <a name="idispeventimpl-class"></a>Klasa IDispEventImpl

Ta klasa udostępnia implementacje `IDispatch` metod.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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

*nID*<br/>
Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventImpl` jest klasą bazową dla kontrolki złożonej, użyj identyfikatora zasobu odpowiedniej kontrolki dla tego parametru. W innych przypadkach Użyj dowolnej dodatniej liczby całkowitej.

*T*<br/>
Klasa użytkownika, która pochodzi od `IDispEventImpl`.

*pdiid*<br/>
Wskaźnik do IID zdarzenia dispinterface zaimplementowane przez tę klasę. Ten interfejs musi być zdefiniowany w bibliotece typów, zgodnie z *plibid*, *wMajor*i *wMinor*.

*plibid*<br/>
Wskaźnik do biblioteki typów, który definiuje interfejs wysyłania wskazywany przez *pdiid*. Jeśli **&AMP; GUID_NULL**, biblioteka typów zostanie załadowana z obiektu, który pozyskuje zdarzenia.

*wMajor*<br/>
Główna wersja biblioteki typów. Wartość domyślna to 0.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass*<br/>
Klasa używana do zarządzania informacjami o typie dla *T*. Wartość domyślna to Klasa typu `CComTypeInfoHolder`; można jednak zastąpić ten parametr szablonu, dostarczając klasę typu innego niż. `CComTypeInfoHolder`

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl:: _tihclass](../../atl/reference/idispeventimpl-class.md)|Klasa używana do zarządzania informacjami o typie. Domyślnie `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl:: IDispEventImpl](#idispeventimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispEventImpl:: GetFuncInfoFromId](#getfuncinfofromid)|Lokalizuje indeks funkcji dla określonego identyfikatora wysyłania.|
|[IDispEventImpl:: GetIDsOfNames](#getidsofnames)|Mapuje pojedynczy element członkowski i opcjonalny zestaw nazw argumentów na odpowiedni zestaw całkowitych identyfikatorów SPID.|
|[IDispEventImpl::](#gettypeinfo)|Pobiera informacje o typie dla obiektu.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę interfejsów informacji o typie.|
|[IDispEventImpl:: GetUserDefinedType](#getuserdefinedtype)|Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.|

## <a name="remarks"></a>Uwagi

`IDispEventImpl`zapewnia sposób implementacji usługi Event dispinterface bez konieczności podawania kodu implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventImpl`zapewnia implementacje `IDispatch` metod. Musisz podać tylko implementacje dla zdarzeń, które chcesz obsłużyć.

`IDispEventImpl`działa w połączeniu z mapą ujścia zdarzeń w klasie w celu kierowania zdarzeń do odpowiedniej funkcji obsługi. Aby użyć tej klasy:

Dodaj makro [SINK_ENTRY](composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) do mapy ujścia zdarzeń dla każdego zdarzenia na każdym obiekcie, który ma być obsługiwany. Jeśli używasz `IDispEventImpl` jako klasy bazowej kontrolki złożonej, możesz wywołać [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) , aby ustanowić i przerwać połączenie ze źródłami zdarzeń dla wszystkich wpisów na mapie ujścia zdarzeń. W innych przypadkach lub w celu uzyskania większej kontroli należy wywołać [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) , aby ustanowić połączenie między obiektem źródłowym a klasą bazową. Wywołaj [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) , aby przerwać połączenie.

Należy utworzyć pochodną `IDispEventImpl` (przy użyciu unikatowej wartości dla *NID*) dla każdego obiektu, dla którego należy obsługiwać zdarzenia. Klasy bazowej można użyć ponownie, nie doradzając względem jednego obiektu źródłowego, a następnie doradzasz przed innym obiektem źródłowym, ale Maksymalna liczba obiektów źródłowych, które mogą być obsługiwane przez pojedynczy obiekt jednocześnie, jest ograniczona przez liczbę `IDispEventImpl` klas bazowych.

`IDispEventImpl`zapewnia te same funkcje co [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), z tą różnicą, że pobiera informacje o interfejsie z biblioteki typów, a nie podano jako wskaźnik do struktury [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) . Użyj `IDispEventSimpleImpl` , jeśli nie masz biblioteki typów opisującej interfejs zdarzenia lub chcesz uniknąć narzutu związanego z korzystaniem z biblioteki typów.

> [!NOTE]
> `IDispEventImpl`i `IDispEventSimpleImpl` zapewnić własną `IUnknown::QueryInterface` implementację, która umożliwia `IDispEventImpl` każdej `IDispEventSimpleImpl` klasie i klasy podstawowej działanie jako oddzielną tożsamość com, jednocześnie zapewniając bezpośredni dostęp do elementów członkowskich klasy w głównym obiekcie com.

Implementacja elementu "xmlatl" obiektów przepustek zdarzeń ActiveX obsługuje tylko wartości zwracane typu HRESULT lub void z metod obsługi zdarzeń; jakakolwiek inna wartość zwracana jest nieobsługiwana i jego zachowanie jest niezdefiniowane.

Aby uzyskać więcej informacji, zobacz temat [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getfuncinfofromid"></a>IDispEventImpl:: GetFuncInfoFromId

Lokalizuje indeks funkcji dla określonego identyfikatora wysyłania.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Odwołanie do identyfikatora funkcji.

*dispidMember*<br/>
podczas Identyfikator wysyłania funkcji.

*lcid*<br/>
podczas Kontekst ustawień funkcji.

*informacje*<br/>
podczas Struktura wskazująca, jak funkcja jest wywoływana.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="getidsofnames"></a>IDispEventImpl:: GetIDsOfNames

Mapuje pojedynczy element członkowski i opcjonalny zestaw nazw argumentów na odpowiedni zestaw całkowitych identyfikatorów SPID, które mogą być używane podczas kolejnych wywołań do elementu [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.

##  <a name="gettypeinfo"></a>IDispEventImpl::

Pobiera informacje o typie dla obiektu, których następnie można użyć do uzyskania informacji o typie interfejsu.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

##  <a name="gettypeinfocount"></a>IDispEventImpl:: GetTypeInfoCount

Pobiera informację o liczbie typów interfejsów, jakie zawiera obiekt (0 lub 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w Windows SDK.

##  <a name="getuserdefinedtype"></a>IDispEventImpl:: GetUserDefinedType

Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parametry

*pTI*<br/>
podczas Wskaźnik do interfejsu [Metoda ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) zawierającego typ zdefiniowany przez użytkownika.

*hrt*<br/>
podczas Dojście do opisu typu, który ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Typ Variant.

### <a name="remarks"></a>Uwagi

Zobacz [Metoda ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

##  <a name="idispeventimpl"></a>IDispEventImpl:: IDispEventImpl

Konstruktor. Przechowuje wartości parametrów szablonu klasy *plibid*, *pdiid*, *wMajor*i *wMinor*.

```
IDispEventImpl();
```

##  <a name="tihclass"></a>IDispEventImpl:: tihclass

Ten element typedef jest wystąpieniem parametru szablonu klasy *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Uwagi

Domyślnie Klasa to `CComTypeInfoHolder`. `CComTypeInfoHolder`zarządza informacjami o typie dla klasy.

## <a name="see-also"></a>Zobacz także

[Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
