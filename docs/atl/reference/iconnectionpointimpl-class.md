---
title: Klasa IConnectionPointImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c49057153a23f0e17d09032df8781b64cef8677
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iconnectionpointimpl-class"></a>Klasa IConnectionPointImpl
Ta klasa implementuje punkt połączenia.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IConnectionPointImpl`.  
  
 `piid`  
 Wskaźnik do identyfikatora IID interfejsu reprezentowanych przez obiekt punktu połączenia.  
  
 `CDV`  
 Klasa, która zarządza połączenia. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), dzięki czemu nieograniczoną liczbę połączeń. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Ustanawia połączenie między punktem połączenia i odbioru.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Tworzy moduł wyliczający do iteracji połączenia punktu połączenia.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Pobiera identyfikator IID interfejsu reprezentowany przez punkt połączenia.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Pobiera wskaźnika interfejsu do obiektu składnika.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Przerywa połączenie wcześniej ustanowione za pośrednictwem `Advise`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Zarządza połączeniami punktu połączenia.|  
  
## <a name="remarks"></a>Uwagi  
 `IConnectionPointImpl`implementuje punkt połączenia, dzięki czemu obiektu do udostępnienia interfejsu wychodzącego do klienta. Klient implementuje ten interfejs dla obiektu o nazwie zbiorniku.  
  
 ATL używa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) do zaimplementowania obiektu składnika. Każdy punkt połączenia w obiekcie składnika reprezentuje interfejs wychodzących, identyfikowane przez `piid`. Klasa *kor* zarządza połączeniami między punktem połączenia i odbioru. Każde połączenie jest unikatowo identyfikowana przez "plik cookie".  
  
 Aby uzyskać więcej informacji o używaniu punkty połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="advise"></a>IConnectionPointImpl::Advise  
 Ustanawia połączenie między punktem połączenia i odbioru.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [Unadvise](#unadvise) zakończenie wywołania połączenia.  
  
 Zobacz [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) w systemie Windows SDK.  
  
##  <a name="enumconnections"></a>IConnectionPointImpl::EnumConnections  
 Tworzy moduł wyliczający do iteracji połączenia punktu połączenia.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) w systemie Windows SDK.  
  
##  <a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface  
 Pobiera identyfikator IID interfejsu reprezentowany przez punkt połączenia.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) w systemie Windows SDK.  
  
##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer  
 Pobiera wskaźnika interfejsu do obiektu składnika.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) w systemie Windows SDK.  
  
##  <a name="m_vec"></a>IConnectionPointImpl::m_vec  
 Zarządza połączeń między obiektu punktu połączenia i odbioru.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `m_vec` jest typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>IConnectionPointImpl::Unadvise  
 Przerywa połączenie wcześniej ustanowione za pośrednictwem [Porada](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Przegląd klas](../../atl/atl-class-overview.md)
