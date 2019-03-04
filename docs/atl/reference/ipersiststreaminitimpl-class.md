---
title: IPersistStreamInitImpl Class
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: b5ab433ed08b150e6c344d65657a910542856e77
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290051"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl Class

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPersistStreamInitImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.|
|[IPersistStreamInitImpl::Load](#load)|Ładuje właściwości obiektu z określonego strumienia.|
|[IPersistStreamInitImpl::Save](#save)|Zapisuje właściwości obiektu do określonego strumienia.|

## <a name="remarks"></a>Uwagi

[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejs umożliwia klientowi żądanie czy obiekt ładuje i zapisuje jego trwałych danych na jednym strumień. Klasa `IPersistStreamInitImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::GetSizeMax](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) w Windows SDK.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::InitNew](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) w Windows SDK.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::IsDirty](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) w Windows SDK.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Ładuje właściwości obiektu z określonego strumienia.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Uwagi

ATL używa map właściwości obiektu do pobrania tych informacji.

Zobacz [IPersistStreamInit::Load](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-load) w Windows SDK.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Zapisuje właściwości obiektu do określonego strumienia.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Uwagi

ATL używa map właściwości obiektu do przechowywania tych informacji.

Zobacz [IPersistStreamInit::Save](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-save) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Kontenery i strumienie](/windows/desktop/Stg/storages-and-streams)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
