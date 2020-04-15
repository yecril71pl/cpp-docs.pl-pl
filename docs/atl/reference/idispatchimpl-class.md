---
title: Klasa IDispatchImpl
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329788"
---
# <a name="idispatchimpl-class"></a>Klasa IDispatchImpl

Zapewnia domyślną implementację `IDispatch` dla części interfejsu podwójnego.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
[w] Podwójny interfejs.

*piid*<br/>
[w] Wskaźnik do identyfikatora *T*.

*plibid ( plibid )*<br/>
[w] Wskaźnik do libid biblioteki typów, który zawiera informacje o interfejsie. Domyślnie biblioteka typów na poziomie serwera jest przekazywana.

*wMajor*<br/>
[w] Główna wersja biblioteki typów. Domyślnie wartość wynosi 1.

*wMinor*<br/>
[w] Wersja pomocnicza biblioteki typów. Domyślnie wartość wynosi 0.

*tihclass (klasa tihclass)*<br/>
[w] Klasa używana do zarządzania informacjami o typie *dla T*. Domyślnie wartość to `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor. Wywołuje `AddRef` chroniona zmienna elementu członkowskiego, która zarządza informacjami o typie dla podwójnego interfejsu. Destruktor wywołuje `Release`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie dla podwójnego interfejsu.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Określa, czy dostępne są informacje o typie dla interfejsu podwójnego.|
|[IDispatchImpl::Wywołaj](#invoke)|Zapewnia dostęp do metod i właściwości udostępnianych przez podwójny interfejs.|

## <a name="remarks"></a>Uwagi

`IDispatchImpl`zapewnia domyślną implementację dla `IDispatch` części dowolnego interfejsu podwójnego obiektu. Podwójny interfejs pochodzi `IDispatch` z i używa tylko typy zgodne z automatyzacją. Podobnie jak dispinterface, podwójny interfejs obsługuje wczesne wiązanie i późne wiązanie; jednak podwójny interfejs obsługuje również wiązanie vtable.

W poniższym przykładzie `IDispatchImpl`przedstawiono typową implementację .

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Domyślnie klasa `IDispatchImpl` wyszukuje informacje o typie *T* w rejestrze. Aby zaimplementować niezarejestrowany interfejs, można użyć `IDispatchImpl` klasy bez uzyskiwania dostępu do rejestru przy użyciu wstępnie zdefiniowanego numeru wersji. Jeśli `IDispatchImpl` utworzysz obiekt, który ma 0xFFFF jako wartość dla *wMajor* i 0xFFFF jako wartość dla *wMinor*, `IDispatchImpl` klasa pobiera bibliotekę typów z pliku .dll zamiast rejestru.

`IDispatchImpl`zawiera statyczny element `CComTypeInfoHolder` członkowski typu, który zarządza informacjami o typie dla podwójnego interfejsu. Jeśli masz wiele obiektów, które implementują ten `CComTypeInfoHolder` sam interfejs podwójny, używane jest tylko jedno wystąpienie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames

Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.

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

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo

Pobiera informacje o typie dla podwójnego interfejsu.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w usłudze Windows SDK.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

Określa, czy dostępne są informacje o typie dla interfejsu podwójnego.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz `IDispatch::GetTypeInfoCount` w windows SDK.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

Konstruktor. Wywołuje `AddRef` chroniona zmienna elementu członkowskiego, która zarządza informacjami o typie dla podwójnego interfejsu. Destruktor wywołuje `Release`.

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Wywołaj

Zapewnia dostęp do metod i właściwości udostępnianych przez podwójny interfejs.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::Wywołaj](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) w usłudze Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
