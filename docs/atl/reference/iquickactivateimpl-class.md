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
ms.openlocfilehash: 2a2b11746249b6ee4f6ddd578717aacc374d53bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198152"
---
# <a name="iquickactivateimpl-class"></a>Klasa IQuickActivateImpl

Ta klasa łączy inicjowania kontroli kontenery w jednym wywołaniu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IQuickActivateImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Wykonuje szybkie inicjowanie kontrolki ładowany.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o kontroli ilości wykorzystanego miejsca wyświetlania kontener został przypisany do niego.|

## <a name="remarks"></a>Uwagi

[IQuickActivate](/windows/desktop/api/ocidl/nn-ocidl-iquickactivate) interfejsu pomaga uniknąć opóźnień, podczas ładowania formantów, łącząc inicjowania w pojedynczym wywołaniu kontenerów. `QuickActivate` Metoda umożliwia kontener, aby przekazać wskaźnik do [QACONTAINER](/windows/desktop/api/ocidl/ns-ocidl-tagqacontainer) musi strukturę, która przechowuje wskaźniki do wszystkich interfejsów kontrolki. Przy powrocie, kontrola przechodzi wstecz wskaźnik do [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) strukturę, która przechowuje wskaźniki do jego własnej interfejsów, które są używane przez kontener. Klasa `IQuickActivateImpl` udostępnia domyślną implementację elementu `IQuickActivate` i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent

Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest pełna renderowanie formantu i jest określony w jednostkach HIMETRIC.

Zobacz [IQuickActivate::GetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) w Windows SDK.

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

Wykonuje szybkie inicjowanie kontrolki ładowany.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Uwagi

Struktura zawiera wskaźniki do interfejsów, które wymagają kontroli i wartości niektórych właściwości otoczenia. Po powrocie, kontrola przechodzi wskaźnik do [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) strukturę, która zawiera wskaźniki do własnej interfejsy, które wymaga kontenera i informacje o stanie dodatkowe.

Zobacz [IQuickActivate::QuickActivate](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-quickactivate) w Windows SDK.

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

Informuje o kontroli ilości wykorzystanego miejsca wyświetlania kontener został przypisany do niego.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Uwagi

Rozmiar określa się w jednostkach HIMETRIC.

Zobacz [IQuickActivate::SetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
