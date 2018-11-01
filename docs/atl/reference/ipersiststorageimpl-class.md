---
title: Klasa IPersistStorageImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: 320ef54c6148adf5354a6a7b1860a84e118dc6de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668991"
---
# <a name="ipersiststorageimpl-class"></a>Klasa IPersistStorageImpl

Ta klasa implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPersistStorageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Powoduje, że obiekt, aby zwolnić wszystkie obiekty magazynu i tryb HandsOff. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicjuje nowy magazyn.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.|
|[IPersistStorageImpl::Load](#load)|Ładuje właściwości obiektu z określonej usługi storage.|
|[IPersistStorageImpl::Save](#save)|Zapisuje właściwości obiektu do określonego magazynu.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Powiadamia obiekt, który może zwrócić do trybu normalnego do zapisu do jego obiektu magazynu. Implementacja biblioteki ATL, zwraca wartość S_OK.|

## <a name="remarks"></a>Uwagi

`IPersistStorageImpl` implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfejsu, co pozwala klientowi na żądanie, które obciążenia obiektu, a następnie zapisz jego trwałe dane przy użyciu magazynu.

Implementacja tej klasy wymaga klasy `T` się implementację `IPersistStreamInit` dostępne za pośrednictwem interfejsu `QueryInterface`. Zwykle oznacza to, że klasa `T` powinien pochodzić od [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), podaj wpis dla `IPersistStreamInit` w [mapy interfejsu COM](com-map-macros.md)i użyj [map właściwości](property-map-macros.md) do opisania klasy trwałych danych.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Powoduje, że obiekt, aby zwolnić wszystkie obiekty magazynu i tryb HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) w Windows SDK.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Inicjuje nowy magazyn.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Uwagi

Implementacja biblioteki ATL deleguje do [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu.

Zobacz [IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) w Windows SDK.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Uwagi

Implementacja biblioteki ATL deleguje do [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu.

Zobacz [IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) w Windows SDK.

##  <a name="load"></a>  IPersistStorageImpl::Load

Ładuje właściwości obiektu z określonej usługi storage.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Uwagi

Implementacja biblioteki ATL deleguje do [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu. `Load` używa strumienia o nazwie "Zawartość" można pobrać danych obiektu. [Zapisz](#save) metoda tworzy pierwotnie tego strumienia.

Zobacz [IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) w Windows SDK.

##  <a name="save"></a>  IPersistStorageImpl::Save

Zapisuje właściwości obiektu do określonego magazynu.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Uwagi

Implementacja biblioteki ATL deleguje do [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu. Gdy `Save` jest pierwszym wywołaniu tworzy strumień o nazwie "Zawartość" na wybrany magazyn. Ten strumień jest następnie używany w późniejszym wywołania `Save` i w wywołaniach [obciążenia](#load).

Zobacz [IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) w Windows SDK.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Powiadamia obiekt, który może zwrócić do trybu normalnego do zapisu do jego obiektu magazynu.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Kontenery i strumienie](/windows/desktop/Stg/storages-and-streams)<br/>
[Klasa IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Klasa IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
