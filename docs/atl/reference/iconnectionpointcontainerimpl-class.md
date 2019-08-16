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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496025"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Klasa IConnectionPointContainerImpl

Ta klasa implementuje kontener punktu połączenia w celu zarządzania kolekcją obiektów [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IConnectionPointContainerImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Tworzy moduł wyliczający do iteracji przez punkty połączenia obsługiwane w obiekcie, który można połączyć.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Pobiera wskaźnik interfejsu do punktu połączenia, który obsługuje określony identyfikator IID.|

## <a name="remarks"></a>Uwagi

`IConnectionPointContainerImpl`implementuje kontener punktu połączenia w celu zarządzania kolekcją obiektów [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `IConnectionPointContainerImpl`Program udostępnia dwie metody, które klient może wywołać, aby uzyskać więcej informacji na temat połączonego obiektu:

- `EnumConnectionPoints`umożliwia klientowi określenie, które interfejsy wychodzące obsługuje obiekt.

- `FindConnectionPoint`umożliwia klientowi określenie, czy obiekt obsługuje określony interfejs wychodzący.

Informacje o korzystaniu z punktów połączenia w ATL można znaleźć w temacie [punkty połączenia](../../atl/atl-connection-points.md)w artykule.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Tworzy moduł wyliczający do iteracji przez punkty połączenia obsługiwane w obiekcie, który można połączyć.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) w Windows SDK.

##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

Pobiera wskaźnik interfejsu do punktu połączenia, który obsługuje określony identyfikator IID.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
