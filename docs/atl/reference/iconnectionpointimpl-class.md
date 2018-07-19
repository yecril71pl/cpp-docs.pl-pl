---
title: Klasa IConnectionPointImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf1f012067c3a3b85dd5168cf93521e4b2024e00
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884051"
---
# <a name="iconnectionpointimpl-class"></a>Klasa IConnectionPointImpl
Ta klasa implementuje punkt połączenia.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IConnectionPointImpl`.  
  
 *piid*  
 Wskaźnik do identyfikatora IID interfejsu, reprezentowane przez obiekt punktu połączenia.  
  
 *KOR*  
 Klasa, która zarządza połączeniami. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), co umożliwia nieograniczone połączenia. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), która określa stałą liczbę połączeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Ustanawia połączenie między punktem połączenia i ujścia.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Tworzy moduł wyliczający do iterowania po połączeń dla punktu połączenia.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Pobiera identyfikator IID interfejsu, reprezentowane przez punkt połączenia.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Pobiera wskaźnik interfejsu do składnika obiektu.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Przerywa połączenie wcześniej ustanowione przez `Advise`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Zarządza połączeniami dla punktu połączenia.|  
  
## <a name="remarks"></a>Uwagi  
 `IConnectionPointImpl` implementuje punkt połączenia, który umożliwia obiektu do udostępnienia interfejsu wychodzącego do klienta. Klient implementuje ten interfejs dla obiektu o nazwie do ujścia.  
  
 Używa ATL [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) implementacji obiektu składnika. Każdy punkt połączenia w ramach składnika obiektu reprezentuje interfejsu wychodzącego identyfikowane przez *piid*. Klasa *kor* zarządza połączeniami między punktem połączenia i ujścia. Każde połączenie jest unikatowo identyfikowana przez "plik cookie".  
  
 Aby uzyskać więcej informacji dotyczących używania punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="advise"></a>  IConnectionPointImpl::Advise  
 Ustanawia połączenie między punktem połączenia i ujścia.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [Unadvise](#unadvise) zakończenie wywołania połączenia.  
  
 Zobacz [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) w Windows SDK.  
  
##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections  
 Tworzy moduł wyliczający do iterowania po połączeń dla punktu połączenia.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) w Windows SDK.  
  
##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface  
 Pobiera identyfikator IID interfejsu, reprezentowane przez punkt połączenia.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) w Windows SDK.  
  
##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer  
 Pobiera wskaźnik interfejsu do składnika obiektu.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) w Windows SDK.  
  
##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec  
 Zarządza połączeniami między obiektu punktu połączenia i ujścia.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `m_vec` typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise  
 Przerywa połączenie wcześniej ustanowione przez [Porada](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
