---
title: Klasa IQuickActivateImpl
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 2169686ebbf756c5caf9232f5031532c62ac8265
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495510"
---
# <a name="iquickactivateimpl-class"></a>Klasa IQuickActivateImpl

Ta klasa łączy inicjalizację kontenera kontenerów z pojedynczym wywołaniem.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IQuickActivateImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Pobiera bieżący rozmiar ekranu dla działającej kontrolki.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Wykonuje szybkie inicjowanie załadowanej kontroli.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o tym, ile miejsca wyświetlania kontener przypisano do niego.|

## <a name="remarks"></a>Uwagi

Interfejs [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) ułatwia kontenery, unikając opóźnień podczas ładowania formantów przez połączenie inicjalizacji w pojedynczym wywołaniu. Metoda umożliwia kontenerowi przekazanie wskaźnika do struktury QACONTAINER, która zawiera wskaźniki do wszystkich interfejsów, których wymaga kontrola. [](/windows/win32/api/ocidl/ns-ocidl-qacontainer) `QuickActivate` Po powrocie formant przekazuje wskaźnik do struktury [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) , która zawiera wskaźniki do własnych interfejsów, które są używane przez kontener. Klasa `IQuickActivateImpl` udostępnia domyślną `IQuickActivate` implementację i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Pobiera bieżący rozmiar ekranu dla działającej kontrolki.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar służy do pełnego renderowania kontrolki i jest określony w jednostkach HIMETRIC.

Zobacz [IQuickActivate:: GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) w Windows SDK.

##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Wykonuje szybkie inicjowanie załadowanej kontroli.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Uwagi

Struktura zawiera wskaźniki do interfejsów wymaganych przez formant oraz wartości niektórych właściwości otoczenia. Po powrocie formant przekazuje wskaźnik do struktury [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) , która zawiera wskaźniki do własnych interfejsów wymaganych przez kontener, oraz dodatkowe informacje o stanie.

Zobacz [IQuickActivate:: QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) w Windows SDK.

##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informuje o tym, ile miejsca wyświetlania kontener przypisano do niego.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest określony w jednostkach HIMETRIC.

Zobacz [IQuickActivate:: SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
