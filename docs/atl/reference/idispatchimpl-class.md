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
ms.openlocfilehash: bf6b416337c58f5e9b8a62dda841615412573666
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275350"
---
# <a name="idispatchimpl-class"></a>Klasa IDispatchImpl

Udostępnia domyślną implementację dla `IDispatch` wchodzi w skład podwójnego interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
[in] Podwójnego interfejsu.

*piid*<br/>
[in] Wskaźnik do identyfikatora IID z *T*.

*plibid*<br/>
[in] Wskaźnik do identyfikatora LIBID biblioteki typów, który zawiera informacje o interfejsie. Domyślnie jest przekazywany biblioteki typów na poziomie serwera.

*wMajor*<br/>
[in] Wersja główna biblioteki typów. Domyślna wartość to 1.

*wMinor*<br/>
[in] Wersja pomocnicza biblioteki typów. Domyślna wartość wynosi 0.

*tihclass*<br/>
[in] Klasa używana do zarządzania informacji o typie *T*. Domyślna wartość to `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor. Wywołania `AddRef` na zmiennej chroniony element członkowski, który zarządza informacji o typie dla podwójnego interfejsu. Wywołania destruktora `Release`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie dla podwójnego interfejsu.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Określa, czy jest informacji o typie podwójnego interfejsu.|
|[IDispatchImpl::Invoke](#invoke)|Zapewnia dostęp do metod i właściwości udostępniane przez podwójnego interfejsu.|

## <a name="remarks"></a>Uwagi

`IDispatchImpl` udostępnia domyślną implementację dla `IDispatch` wchodzi w skład dowolnej podwójnego interfejsu w obiekcie. Pochodzi od klasy podwójnego interfejsu `IDispatch` i używa tylko typy automatyzacji. Podobnie jak dispinterface podwójnego interfejsu obsługuje wczesnego i późnego wiązania; podwójnego interfejsu obsługuje również powiązania vtable.

W poniższym przykładzie pokazano Typowa implementacja metody `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Domyślnie `IDispatchImpl` klasy odwołuje się do informacji o typie *T* w rejestrze. Aby zaimplementować interfejs wyrejestrowany, można użyć `IDispatchImpl` klasy bez dostępu do rejestru przy użyciu numeru wersji wstępnie zdefiniowane. Jeśli tworzysz `IDispatchImpl` obiekt, który ma 0xFFFF jako wartość pozycji *wMajor* i 0xFFFF jako wartość pozycji *wMinor*, `IDispatchImpl` klasy pobranie biblioteki typów z pliku .dll zamiast rejestr.

`IDispatchImpl` zawiera statyczny element członkowski typu `CComTypeInfoHolder` który zarządza informacji o typie dla podwójnego interfejsu. Jeśli masz wiele obiektów, które implementują takie same podwójnego interfejsu, tylko jedno wystąpienie `CComTypeInfoHolder` jest używany.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

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

Zobacz [IDispatch::GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Pobiera informacje o typie dla podwójnego interfejsu.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) w Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Określa, czy jest informacji o typie podwójnego interfejsu.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz `IDispatch::GetTypeInfoCount` w Windows SDK.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

Konstruktor. Wywołania `AddRef` na zmiennej chroniony element członkowski, który zarządza informacji o typie dla podwójnego interfejsu. Wywołania destruktora `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

Zapewnia dostęp do metod i właściwości udostępniane przez podwójnego interfejsu.

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

Zobacz [uwzględniając](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
