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
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495951"
---
# <a name="idispatchimpl-class"></a>Klasa IDispatchImpl

Zapewnia implementację domyślną dla `IDispatch` części podwójnego interfejsu.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
podczas Interfejs podwójny.

*piid*<br/>
podczas Wskaźnik do IID elementu *T*.

*plibid*<br/>
podczas Wskaźnik do identyfikatora LIBID biblioteki typów, który zawiera informacje o interfejsie. Domyślnie jest przenoszona biblioteka typów na poziomie serwera.

*wMajor*<br/>
podczas Główna wersja biblioteki typów. Wartość domyślna to 1.

*wMinor*<br/>
podczas Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass*<br/>
podczas Klasa używana do zarządzania informacjami o typie dla *T*. Wartością domyślną jest `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor. Wywołuje `AddRef` dla zmiennej chronionej składowej, która zarządza informacjami o typie dla podwójnego interfejsu. Destruktor wywołuje `Release`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl:: GetIDsOfNames](#getidsofnames)|Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.|
|[IDispatchImpl::](#gettypeinfo)|Pobiera informacje o typie dla podwójnego interfejsu.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Określa, czy dostępne są informacje o typie dla podwójnego interfejsu.|
|[IDispatchImpl:: Invoke](#invoke)|Zapewnia dostęp do metod i właściwości udostępnianych przez podwójny interfejs.|

## <a name="remarks"></a>Uwagi

`IDispatchImpl`udostępnia implementację domyślną dla `IDispatch` części każdego podwójnego interfejsu w obiekcie. Podwójny interfejs pochodzi z `IDispatch` i używa tylko typów zgodnych z automatyzacją. Podobnie jak w przypadku dispinterface, podwójny interfejs obsługuje wczesne powiązania i późne wiązanie. jednak podwójny interfejs obsługuje również powiązanie tablic wirtualnych.

W poniższym przykładzie przedstawiono typową implementację `IDispatchImpl`programu.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Domyślnie `IDispatchImpl` Klasa wyszukuje informacje o typie dla *T* w rejestrze. Aby zaimplementować niezarejestrowany interfejs, można użyć `IDispatchImpl` klasy bez uzyskiwania dostępu do rejestru przy użyciu wstępnie zdefiniowanego numeru wersji. Jeśli utworzysz `IDispatchImpl` obiekt, który ma 0xFFFF jako wartość dla *wMajor* i 0xFFFF jako wartość `IDispatchImpl` dla *wMinor*, Klasa pobiera bibliotekę typów z pliku dll zamiast z rejestru.

`IDispatchImpl`zawiera statyczną składową typu `CComTypeInfoHolder` , która zarządza informacjami o typie dla podwójnego interfejsu. Jeśli masz wiele obiektów, które implementują ten sam podwójny interfejs, używane `CComTypeInfoHolder` jest tylko jedno wystąpienie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getidsofnames"></a>IDispatchImpl:: GetIDsOfNames

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

Zobacz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.

##  <a name="gettypeinfo"></a>IDispatchImpl::

Pobiera informacje o typie dla podwójnego interfejsu.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w Windows SDK.

##  <a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

Określa, czy dostępne są informacje o typie dla podwójnego interfejsu.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz `IDispatch::GetTypeInfoCount` w Windows SDK.

##  <a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

Konstruktor. Wywołuje `AddRef` dla zmiennej chronionej składowej, która zarządza informacjami o typie dla podwójnego interfejsu. Destruktor wywołuje `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>IDispatchImpl:: Invoke

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

Zobacz [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
