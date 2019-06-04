---
title: IPersistPropertyBagImpl Class
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
ms.openlocfilehash: 569a24fd08801de952e998f772afbc3478096628
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503150"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl Class

Ta klasa implementuje `IUnknown` i zezwala na obiekt zapisać właściwości zbioru właściwości dostarczonych przez klienta.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPersistPropertyBagImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.|
|[IPersistPropertyBagImpl::Save](#save)|Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.|

## <a name="remarks"></a>Uwagi

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) interfejs umożliwia obiekt zapisać właściwości zbioru właściwości dostarczonych przez klienta. Klasa `IPersistPropertyBagImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

`IPersistPropertyBag` działa w połączeniu z [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) i [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Te ostatnie dwa interfejsy muszą być zaimplementowane przez klienta. Za pomocą `IPropertyBag`, klient zapisuje i ładuje poszczególne właściwości obiektu. Za pomocą `IErrorLog`, zarówno klienta, jak i obiekt zgłosić wszystkich wykrytych błędów.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) w Windows SDK.

##  <a name="load"></a>  IPersistPropertyBagImpl::Load

Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Uwagi

ATL używa map właściwości obiektu do pobrania tych informacji.

Zobacz [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) w Windows SDK.

##  <a name="save"></a>  IPersistPropertyBagImpl::Save

Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Uwagi

ATL używa map właściwości obiektu do przechowywania tych informacji. Domyślnie ta metoda zapisuje wszystkie właściwości, bez względu na wartość *fSaveAllProperties*.

Zobacz [IPersistPropertyBag::Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
