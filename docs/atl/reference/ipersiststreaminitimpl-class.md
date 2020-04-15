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
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326458"
---
# <a name="ipersiststreaminitimpl-class"></a>Klasa IPersistStreamInitImpl

Ta klasa `IUnknown` implementuje i zapewnia domyślną implementację interfejsu [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPersistStreamInitImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Pobiera rozmiar strumienia potrzebne do zapisania danych obiektu. Implementacja ATL zwraca E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Sprawdza, czy dane obiektu uległy zmianie od czasu jego ostatniego zapisania.|
|[IPersistStreamInitImpl::Załaduj](#load)|Ładuje właściwości obiektu z określonego strumienia.|
|[IPersistStreamInitImpl::Zapisz](#save)|Zapisuje właściwości obiektu do określonego strumienia.|

## <a name="remarks"></a>Uwagi

Interfejs [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) umożliwia klientowi żądanie, że obiekt ładuje i zapisuje swoje trwałe dane do pojedynczego strumienia. Klasa `IPersistStreamInitImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID

Pobiera identyfikator CLSID obiektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) w windows SDK.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Pobiera rozmiar strumienia potrzebne do zapisania danych obiektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) w windows SDK.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNew

Inicjuje nowo utworzony obiekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) w windows SDK.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::IsDirty

Sprawdza, czy dane obiektu uległy zmianie od czasu jego ostatniego zapisania.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPersistStreamInit::IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) w windows SDK.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Załaduj

Ładuje właściwości obiektu z określonego strumienia.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do pobierania tych informacji.

Zobacz [IPersistStreamInit::Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) w windows SDK.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Zapisz

Zapisuje właściwości obiektu do określonego strumienia.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do przechowywania tych informacji.

Zobacz [IPersistStreamInit::Zapisz](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Magazyny i strumienie](/windows/win32/Stg/storages-and-streams)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
