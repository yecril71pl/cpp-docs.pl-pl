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
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329865"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Klasa IConnectionPointContainerImpl

Ta klasa implementuje kontener punktu połączenia do zarządzania kolekcją obiektów [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IConnectionPointContainerImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Tworzy wyliczacz do iteracji za pośrednictwem punktów połączenia obsługiwanych w obiekcie, który można połączyć.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Pobiera wskaźnik interfejsu do punktu połączenia, który obsługuje określony identyfikator.|

## <a name="remarks"></a>Uwagi

`IConnectionPointContainerImpl`implementuje kontener punktu połączenia do zarządzania kolekcją obiektów [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `IConnectionPointContainerImpl`zawiera dwie metody, które klient może wywołać, aby pobrać więcej informacji o obiekcie, który można połączyć:

- `EnumConnectionPoints`umożliwia klientowi określenie, które interfejsy wychodzące obsługuje obiekt.

- `FindConnectionPoint`umożliwia klientowi określenie, czy obiekt obsługuje określony interfejs wychodzący.

Aby uzyskać informacje na temat korzystania z punktów połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Tworzy wyliczacz do iteracji za pośrednictwem punktów połączenia obsługiwanych w obiekcie, który można połączyć.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer::EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) w programie Windows SDK.

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

Pobiera wskaźnik interfejsu do punktu połączenia, który obsługuje określony identyfikator.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) w programie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Iconnectionpointcontainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
