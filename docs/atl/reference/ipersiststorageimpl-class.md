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
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326466"
---
# <a name="ipersiststorageimpl-class"></a>Klasa IPersistStorageImpl

Ta klasa implementuje interfejs [IPersistStorage.](/windows/win32/api/objidl/nn-objidl-ipersiststorage)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPersistStorageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Nakazuje obiektowi zwolnić wszystkie obiekty magazynu i przejść do trybu HandsOff. Implementacja ATL zwraca S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicjuje nowy magazyn.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Sprawdza, czy dane obiektu uległy zmianie od czasu jego ostatniego zapisania.|
|[IPersistStorageImpl::Obciążenie](#load)|Ładuje właściwości obiektu z określonego magazynu.|
|[IPersistStorageImpl::Zapisz](#save)|Zapisuje właściwości obiektu w określonym magazynie.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Powiadamia obiekt, który może powrócić do trybu normalnego, aby zapisać do jego obiektu magazynu. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

`IPersistStorageImpl`implementuje interfejs [IPersistStorage,](/windows/win32/api/objidl/nn-objidl-ipersiststorage) który umożliwia klientowi żądanie załadowania obiektu i zapisanie jego trwałych danych przy użyciu magazynu.

Implementacja tej klasy `T` wymaga klasy, aby `IPersistStreamInit` implementacja `QueryInterface`interfejsu dostępna za pośrednictwem . Zazwyczaj oznacza to, `T` że klasa powinna pochodzić z [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), podać wpis w `IPersistStreamInit` mapie [COM](com-map-macros.md)i użyć mapy [właściwości](property-map-macros.md) do opisania danych trwałych klasy.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>IPersistStorageImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w windows SDK.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Nakazuje obiektowi zwolnić wszystkie obiekty magazynu i przejść do trybu HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage::HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) w windows SDK.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>IPersistStorageImpl::InitNew

Inicjuje nowy magazyn.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Zobacz [IPersistStorage:InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) w windows SDK.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>IPersistStorageImpl::IsDirty

Sprawdza, czy dane obiektu uległy zmianie od czasu jego ostatniego zapisania.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Zobacz [IPersistStorage:IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) w windows SDK.

## <a name="ipersiststorageimplload"></a><a name="load"></a>IPersistStorageImpl::Obciążenie

Ładuje właściwości obiektu z określonego magazynu.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) `Load`używa strumienia o nazwie "Zawartość", aby pobrać dane obiektu. Save [Save](#save) Metoda pierwotnie tworzy ten strumień.

Zobacz [IPersistStorage:Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) w windows SDK.

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersistStorageImpl::Zapisz

Zapisuje właściwości obiektu w określonym magazynie.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Uwagi

Implementacja ATL deleguje do interfejsu [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) Po `Save` pierwszym wywołaniu tworzy strumień o nazwie "Zawartość" w określonym magazynie. Ten strumień jest następnie używany `Save` w późniejszych wywołaniach do i w wywołaniach [załadować](#load).

Zobacz [IPersistStorage:Zapisz](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) w windows SDK.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Powiadamia obiekt, który może powrócić do trybu normalnego, aby zapisać do jego obiektu magazynu.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStorage:SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Magazyny i strumienie](/windows/win32/Stg/storages-and-streams)<br/>
[Klasa IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Klasa IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
