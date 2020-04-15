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
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329855"
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
Twoja klasa, pochodząca od `IConnectionPointImpl`.

*piid*<br/>
Wskaźnik do identyfikatora interfejsu reprezentowanego przez obiekt punktu połączenia.

*Cdv*<br/>
Klasa, która zarządza połączeniami. Wartością domyślną jest [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), która pozwala na nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointImpl::Doradzić](#advise)|Ustanawia połączenie między punktem połączenia a zatoniem.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Tworzy wyliczacz do iteracji za pośrednictwem połączeń dla punktu połączenia.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Pobiera identyfikator interfejsu reprezentowanego przez punkt połączenia.|
|[IConnectionPointImpl::GetConnectionPointKontainer](#getconnectionpointcontainer)|Pobiera wskaźnik interfejsu do obiektu podłączanego.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Kończy połączenie wcześniej nawiązane `Advise`za pośrednictwem .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Zarządza połączeniami dla punktu połączenia.|

## <a name="remarks"></a>Uwagi

`IConnectionPointImpl`implementuje punkt połączenia, który umożliwia obiektowi udostępnienie klienta interfejsu wychodzącego. Klient implementuje ten interfejs na obiekcie o nazwie sink.

ATL używa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) do zaimplementowania obiektu podłączanego. Każdy punkt połączenia w obrębie obiektu podłączonego reprezentuje interfejs wychodzący, identyfikowany przez *piid*. Klasa *CDV* zarządza połączeniami między punktem połączenia a obiektem sink. Każde połączenie jest jednoznacznie identyfikowane przez "plik cookie".

Aby uzyskać więcej informacji na temat korzystania z punktów połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointImpl::Doradzić

Ustanawia połączenie między punktem połączenia a zatoniem.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Uwagi

Użyj [Unadvise,](#unadvise) aby zakończyć wywołanie połączenia.

Zobacz [IConnectionPoint::Doradztwo](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) w programie Windows SDK.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Tworzy wyliczacz do iteracji za pośrednictwem połączeń dla punktu połączenia.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint::EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) w windows SDK.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface

Pobiera identyfikator interfejsu reprezentowanego przez punkt połączenia.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint::GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) w windows SDK.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointKontainer

Pobiera wskaźnik interfejsu do obiektu podłączanego.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint::GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) w windows SDK.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointImpl::m_vec

Zarządza połączeniami między obiektem punktu połączenia a obiektem sink.

```
CDV m_vec;
```

### <a name="remarks"></a>Uwagi

Domyślnie `m_vec` jest typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointImpl::Unadvise

Kończy połączenie wcześniej nawiązane za pośrednictwem [advise](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Uwagi

Zobacz [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Iconnectionpoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
