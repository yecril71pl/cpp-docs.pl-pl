---
title: Klasa IConnectionPointImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: bd88fd5d00df0347c0bd2161129b8cfa3ca35406
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496082"
---
# <a name="iconnectionpointimpl-class"></a>Klasa IConnectionPointImpl

Ta klasa implementuje punkt połączenia.

## <a name="syntax"></a>Składnia

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IConnectionPointImpl`.

*piid*<br/>
Wskaźnik do IID interfejsu reprezentowanego przez obiekt punktu połączenia.

*CDV*<br/>
Klasa, która zarządza połączeniami. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), która umożliwia nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointImpl:: Advise](#advise)|Ustanawia połączenie między punktem połączenia a ujściam.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Tworzy moduł wyliczający do iteracji połączeń dla punktu połączenia.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Pobiera identyfikator IID interfejsu reprezentowanego przez punkt połączenia.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Pobiera wskaźnik interfejsu do połączonego obiektu.|
|[IConnectionPointImpl:: Unadvise](#unadvise)|Kończy połączenie wcześniej ustanowione przez `Advise`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Zarządza połączeniami punktu połączenia.|

## <a name="remarks"></a>Uwagi

`IConnectionPointImpl`implementuje punkt połączenia, który umożliwia obiektowi uwidocznienie interfejsu wychodzącego dla klienta. Klient implementuje ten interfejs na obiekcie o nazwie ujścia.

ATL używa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) do implementowania połączonego obiektu. Każdy punkt połączenia w połączonym obiekcie reprezentuje interfejs wychodzący identyfikowany przez *piid*. Klasa *CDV* zarządza połączeniami między punktem połączenia a ujściam. Każde połączenie jest jednoznacznie identyfikowane przez "plik cookie".

Aby uzyskać więcej informacji na temat używania punktów połączenia w ATL, zobacz [punkty połączenia](../../atl/atl-connection-points.md)w artykule.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="advise"></a>IConnectionPointImpl:: Advise

Ustanawia połączenie między punktem połączenia a ujściam.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Uwagi

Użyj [](#unadvise) funkcji Unadvise, aby przerwać połączenie połączenia.

Zobacz [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) w Windows SDK.

##  <a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Tworzy moduł wyliczający do iteracji połączeń dla punktu połączenia.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) w Windows SDK.

##  <a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface

Pobiera identyfikator IID interfejsu reprezentowanego przez punkt połączenia.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) w Windows SDK.

##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer

Pobiera wskaźnik interfejsu do połączonego obiektu.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) w Windows SDK.

##  <a name="m_vec"></a>IConnectionPointImpl::m_vec

Zarządza połączeniami między obiektem punktu połączenia i ujściam.

```
CDV m_vec;
```

### <a name="remarks"></a>Uwagi

Domyślnie `m_vec` jest to typ [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

##  <a name="unadvise"></a>IConnectionPointImpl:: Unadvise

Kończy połączenie wcześniej ustanowione przy użyciu [porady](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
