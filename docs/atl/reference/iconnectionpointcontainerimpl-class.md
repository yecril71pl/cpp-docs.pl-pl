---
title: Klasa IConnectionPointContainerImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs: C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f5e3a6ee6790c4fa0e93fe312d6a6b840b754a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iconnectionpointcontainerimpl-class"></a>Klasa IConnectionPointContainerImpl
Ta klasa implementuje kontener punktu połączenia, aby zarządzanie kolekcją [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IConnectionPointContainerImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Tworzy moduł wyliczający do iteracji punkty połączenia obsługiwane w obiekcie składnika.|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Pobiera wskaźnika interfejsu do obsługującą określony identyfikator IID punktu połączenia.|  
  
## <a name="remarks"></a>Uwagi  
 `IConnectionPointContainerImpl`implementuje kontener punktu połączenia, aby zarządzanie kolekcją [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) obiektów. `IConnectionPointContainerImpl`udostępnia dwie metody, które klient może wywoływać można pobrać więcej informacji na temat obiektu składnika:  
  
- `EnumConnectionPoints`Umożliwia klienta w celu określenia, które wychodzące interfejsy obsługuje obiektu.  
  
- `FindConnectionPoint`Umożliwia klienta w celu określenia, czy obiekt obsługuje określony interfejs wychodzących.  
  
 Aby dowiedzieć się, jak za pomocą punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints  
 Tworzy moduł wyliczający do iteracji punkty połączenia obsługiwane w obiekcie składnika.  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) w systemie Windows SDK.  
  
##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint  
 Pobiera wskaźnika interfejsu do obsługującą określony identyfikator IID punktu połączenia.  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Przegląd klas](../../atl/atl-class-overview.md)
