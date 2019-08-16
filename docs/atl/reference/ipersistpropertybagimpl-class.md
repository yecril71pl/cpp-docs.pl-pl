---
title: Klasa IPersistPropertyBagImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: 15b9c9738d921c4c6f7837f9280c6dd6b09392d6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495777"
---
# <a name="ipersistpropertybagimpl-class"></a>Klasa IPersistPropertyBagImpl

Ta klasa implementuje `IUnknown` i umożliwia obiektowi zapisanie jego właściwości w zbiorze właściwości dostarczanym przez klienta.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IPersistPropertyBagImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt. Implementacja ATL zwraca S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Ładuje właściwości obiektu z zbioru właściwości dostarczonego przez klienta.|
|[IPersistPropertyBagImpl::Save](#save)|Zapisuje właściwości obiektu w zbiorze właściwości dostarczanym przez klienta.|

## <a name="remarks"></a>Uwagi

Interfejs [IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) umożliwia obiektowi zapisanie jego właściwości w zbiorze właściwości dostarczanym przez klienta. Klasa `IPersistPropertyBagImpl` zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

`IPersistPropertyBag`działa w połączeniu z [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) i [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Te ostatnie dwa interfejsy muszą zostać zaimplementowane przez klienta. `IPropertyBag`W programie klient zapisuje i ładuje poszczególne właściwości obiektu. `IErrorLog`W programie zarówno obiekt, jak i klient mogą raportować wszystkie napotkane błędy.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getclassid"></a>IPersistPropertyBagImpl:: GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) w Windows SDK.

##  <a name="load"></a>IPersistPropertyBagImpl:: Load

Ładuje właściwości obiektu z zbioru właściwości dostarczonego przez klienta.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu, aby pobrać te informacje.

Zobacz [IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) w Windows SDK.

##  <a name="save"></a>IPersistPropertyBagImpl:: Save

Zapisuje właściwości obiektu w zbiorze właściwości dostarczanym przez klienta.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do przechowywania tych informacji. Domyślnie ta metoda zapisuje wszystkie właściwości, niezależnie od wartości *fSaveAllProperties*.

Zobacz [IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
