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
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495688"
---
# <a name="ipersiststorageimpl-class"></a>Klasa IPersistStorageImpl

Ta klasa implementuje interfejs [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IPersistStorageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStorageImpl:: GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Powoduje, że obiekt zwalnia wszystkie obiekty magazynu i wprowadza tryb HandsOff. Implementacja ATL zwraca S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicjuje nowy magazyn.|
|[IPersistStorageImpl:: IsDirty](#isdirty)|Sprawdza, czy dane obiektu zostały zmienione od czasu ostatniego zapisywania.|
|[IPersistStorageImpl:: Load](#load)|Ładuje właściwości obiektu z określonego magazynu.|
|[IPersistStorageImpl:: Save](#save)|Zapisuje właściwości obiektu do określonego magazynu.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Powiadamia obiekt, że może powrócić do trybu normalnego, aby zapisać do jego obiektu magazynu. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

`IPersistStorageImpl`implementuje interfejs [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) , dzięki czemu klient może zażądać załadowania obiektu i zapisania jego trwałych danych przy użyciu magazynu.

Implementacja tej klasy wymaga, aby Klasa `T` była implementacją `IPersistStreamInit` interfejsu dostępnego za pośrednictwem `QueryInterface`. Zazwyczaj oznacza to, że `T` Klasa powinna pochodzić od [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), podać wpis dla `IPersistStreamInit` w [mapie com](com-map-macros.md)i używać [mapy właściwości](property-map-macros.md) do opisywania trwałych danych klasy.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getclassid"></a>IPersistStorageImpl:: GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Powoduje, że obiekt zwalnia wszystkie obiekty magazynu i wprowadza tryb HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) w Windows SDK.

##  <a name="initnew"></a>IPersistStorageImpl::InitNew

Inicjuje nowy magazyn.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Zobacz [IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) w Windows SDK.

##  <a name="isdirty"></a>IPersistStorageImpl:: IsDirty

Sprawdza, czy dane obiektu zostały zmienione od czasu ostatniego zapisywania.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Zobacz [IPersistStorage:](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) IsDirty w Windows SDK.

##  <a name="load"></a>IPersistStorageImpl:: Load

Ładuje właściwości obiektu z określonego magazynu.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . `Load`Pobiera dane obiektu za pomocą strumienia o nazwie "Contents". Metoda [Save](#save) tworzy pierwotnie ten strumień.

Zobacz [IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) w Windows SDK.

##  <a name="save"></a>IPersistStorageImpl:: Save

Zapisuje właściwości obiektu do określonego magazynu.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . Gdy `Save` jest wywoływana po raz pierwszy, tworzy strumień o nazwie "Contents" w określonym magazynie. Ten strumień jest następnie używany w późniejszych wywołaniach do `Save` i w wywołaniach do załadowania. [](#load)

Zobacz [IPersistStorage: Save](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) w Windows SDK.

##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Powiadamia obiekt, że może powrócić do trybu normalnego, aby zapisać do jego obiektu magazynu.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Magazyny i strumienie](/windows/win32/Stg/storages-and-streams)<br/>
[Klasa IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Klasa IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
