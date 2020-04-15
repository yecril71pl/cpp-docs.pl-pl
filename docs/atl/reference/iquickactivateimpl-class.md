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
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329554"
---
# <a name="iquickactivateimpl-class"></a>Klasa IQuickActivateImpl

Ta klasa łączy inicjowanie kontroli kontenerów w jednym wywołaniu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IQuickActivateImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Pobiera bieżący rozmiar wyświetlania dla uruchomionego formantu.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Wykonuje szybkie inicjowanie ładowanych formantów.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje formant o tym, ile miejsca na wyświetlaczu kontener został przypisany do niego.|

## <a name="remarks"></a>Uwagi

[Interfejs IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) pomaga kontenerom uniknąć opóźnień podczas ładowania formantów przez połączenie inicjowania w jednym wywołaniu. Metoda `QuickActivate` umożliwia kontenera przekazać wskaźnik do [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) struktury, która przechowuje wskaźniki do wszystkich interfejsów wymaga kontroli. Po powrocie formant przekazuje z powrotem wskaźnik do [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) struktury, która przechowuje wskaźniki do własnych interfejsów, które są używane przez kontener. Klasa `IQuickActivateImpl` zapewnia domyślną `IQuickActivate` implementację `IUnknown` i implementuje, wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Pobiera bieżący rozmiar wyświetlania dla uruchomionego formantu.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest dla pełnego renderowania formantu i jest określony w jednostkach HIMETRIC.

Zobacz [IQuickActivate::GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) w usłudze Windows SDK.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Wykonuje szybkie inicjowanie ładowanych formantów.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Uwagi

Struktura zawiera wskaźniki do interfejsów wymaganych przez formant i wartości niektórych właściwości otoczenia. Po powrocie formant przekazuje wskaźnik do [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) struktury, która zawiera wskaźniki do własnych interfejsów, które wymaga kontenera i dodatkowe informacje o stanie.

Zobacz [IQuickActivate::QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) w usłudze Windows SDK.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informuje formant o tym, ile miejsca na wyświetlaczu kontener został przypisany do niego.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest określony w jednostkach HIMETRIC.

Zobacz [IQuickActivate::SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
