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
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326486"
---
# <a name="ipersistpropertybagimpl-class"></a>Klasa IPersistPropertyBagImpl

Ta klasa `IUnknown` implementuje i umożliwia obiektowi zapisanie jego właściwości w torbie właściwości dostarczonej przez klienta.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPersistPropertyBagImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt. Implementacja ATL zwraca S_OK.|
|[IPersistPropertyBagImpl::Załaduj](#load)|Ładuje właściwości obiektu z worka właściwości dostarczonych przez klienta.|
|[IPersistPropertyBagImpl::Zapisz](#save)|Zapisuje właściwości obiektu w torbie właściwości dostarczonej przez klienta.|

## <a name="remarks"></a>Uwagi

[Interfejs IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) umożliwia obiektowi zapisanie jego właściwości w torbie właściwości dostarczonej przez klienta. Klasa `IPersistPropertyBagImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

`IPersistPropertyBag`działa w połączeniu z [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) i [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Te dwa ostatnie interfejsy muszą być zaimplementowane przez klienta. Za `IPropertyBag`pośrednictwem klienta zapisuje i ładuje poszczególne właściwości obiektu. Through `IErrorLog`, zarówno obiekt, jak i klient mogą zgłaszać wszelkie napotkane błędy.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w windows SDK.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) w windows SDK.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersistPropertyBagImpl::Załaduj

Ładuje właściwości obiektu z worka właściwości dostarczonych przez klienta.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do pobierania tych informacji.

Zobacz [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) w windows SDK.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersistPropertyBagImpl::Zapisz

Zapisuje właściwości obiektu w torbie właściwości dostarczonej przez klienta.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do przechowywania tych informacji. Domyślnie ta metoda zapisuje wszystkie właściwości, niezależnie od wartości *właściwości fSaveAllProperties*.

Zobacz [IPersistPropertyBag::Zapisz](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) w windows SDK.

## <a name="see-also"></a>Zobacz też

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
