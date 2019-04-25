---
title: IPerPropertyBrowsingImpl Class
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: 54c475e736425718e954b0e954ea2b327d938556
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274922"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl Class

Ta klasa implementuje `IUnknown` i umożliwia klientom dostęp do informacji na stronach właściwości obiektu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPerPropertyBrowsingImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Pobiera ciąg opisujący danej właściwości.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Pobiera tablicę ciągów, odpowiadającą wartości, które może akceptować danej właściwości.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Pobiera typ VARIANT zawierający wartość właściwości identyfikowane przez dany identyfikator DISPID. Identyfikator DISPID wiążą się nazwa ciągu pobierane `GetPredefinedStrings`. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Pobiera identyfikator CLSID strony właściwości skojarzone z danej właściwości.|

## <a name="remarks"></a>Uwagi

[IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing) interfejs umożliwia klientom dostęp do informacji na stronach właściwości obiektu. Klasa `IPerPropertyBrowsingImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

> [!NOTE]
>  Korzystania z programu Microsoft Access jako aplikacji kontenera musi pochodzić od klasy `IPerPropertyBrowsingImpl`. W przeciwnym razie dostęp nie zostanie załadowany formantu.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

Pobiera ciąg opisujący danej właściwości.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) w Windows SDK.

##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings

Wypełnia każdej macierzy z elementami, zerowego.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL [GetPredefinedValue](#getpredefinedvalue) zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPerPropertyBrowsing::GetPredefinedStrings](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) w Windows SDK.

##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue

Pobiera typ VARIANT zawierający wartość właściwości identyfikowane przez dany identyfikator DISPID. Identyfikator DISPID wiążą się nazwa ciągu pobierane `GetPredefinedStrings`.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Implementacja ATL [GetPredefinedStrings](#getpredefinedstrings) pobiera nie odpowiednich ciągów.

Zobacz [IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) w Windows SDK.

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

Pobiera identyfikator CLSID strony właściwości skojarzone z określoną właściwością.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Uwagi

ATL używa obiektu właściwości mapy, aby uzyskać te informacje.

Zobacz [IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
