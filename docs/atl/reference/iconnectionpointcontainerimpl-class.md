---
title: Klasa IConnectionPointContainerImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: 06baa4dac3248d783648b8ce37e51250e0de2498
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269308"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Klasa IConnectionPointContainerImpl

Ta klasa implementuje kontener punktu połączenia, aby zarządzać kolekcją [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) obiektów.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IConnectionPointContainerImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Tworzy moduł wyliczający do iteracji przez punkty połączenia obsługiwane przez obiekt składnika.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Pobiera wskaźnik do punktu połączenia, który obsługuje określonego identyfikatora IID interfejsu.|

## <a name="remarks"></a>Uwagi

`IConnectionPointContainerImpl` implementuje kontener punktu połączenia, aby zarządzać kolekcją [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) obiektów. `IConnectionPointContainerImpl` udostępnia dwie metody, które klienta można wywołać, aby pobrać więcej informacji o obiekcie składnika:

- `EnumConnectionPoints` umożliwia klientowi określenie, które wychodzące interfejsy obsługuje obiektu.

- `FindConnectionPoint` umożliwia klientowi określenie, czy obiekt obsługuje określony interfejs wychodzących.

Aby dowiedzieć się, jak za pomocą punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

Tworzy moduł wyliczający do iteracji przez punkty połączenia obsługiwane przez obiekt składnika.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer::EnumConnectionPoints](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) w Windows SDK.

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

Pobiera wskaźnik do punktu połączenia, który obsługuje określonego identyfikatora IID interfejsu.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
