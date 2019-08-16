---
title: Klasa IPersistStreamInitImpl
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
ms.openlocfilehash: 7a350a4349cb825795a18dd860a2482952b04dcb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496151"
---
# <a name="ipersiststreaminitimpl-class"></a>Klasa IPersistStreamInitImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IPersistStreamInitImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Pobiera rozmiar strumienia wymaganego do zapisania danych obiektu. Implementacja ATL zwraca E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Sprawdza, czy dane obiektu zostały zmienione od czasu ostatniego zapisywania.|
|[IPersistStreamInitImpl::Load](#load)|Ładuje właściwości obiektu z określonego strumienia.|
|[IPersistStreamInitImpl::Save](#save)|Zapisuje właściwości obiektu do określonego strumienia.|

## <a name="remarks"></a>Uwagi

Interfejs [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) umożliwia klientowi żądanie załadowania obiektu i zapisanie jego trwałych danych w jednym strumieniu. Klasa `IPersistStreamInitImpl` zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getclassid"></a>IPersistStreamInitImpl:: GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.

##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Pobiera rozmiar strumienia wymaganego do zapisania danych obiektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) w Windows SDK.

##  <a name="initnew"></a>IPersistStreamInitImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) w Windows SDK.

##  <a name="isdirty"></a>IPersistStreamInitImpl:: IsDirty

Sprawdza, czy dane obiektu zostały zmienione od czasu ostatniego zapisywania.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) IsDirty w Windows SDK.

##  <a name="load"></a>IPersistStreamInitImpl:: Load

Ładuje właściwości obiektu z określonego strumienia.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu, aby pobrać te informacje.

Zobacz [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) w Windows SDK.

##  <a name="save"></a>IPersistStreamInitImpl:: Save

Zapisuje właściwości obiektu do określonego strumienia.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do przechowywania tych informacji.

Zobacz [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Magazyny i strumienie](/windows/win32/Stg/storages-and-streams)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
