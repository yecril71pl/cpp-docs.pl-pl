---
title: Klasa IPropertyNotifySinkCP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa15ef6706010154151c696eca320d464cdfee6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ipropertynotifysinkcp-class"></a>Klasa IPropertyNotifySinkCP
Ta klasa przedstawia [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejs jako wychodzących interfejs dla obiektu składnika.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPropertyNotifySinkCP`.  
  
 `CDV`  
 Klasa, która zarządza połączeniami między punktem połączenia i jego sink. Wartość domyślna to [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), dzięki czemu nieograniczoną liczbę połączeń. Można również użyć [CComUnkArray](../../atl/reference/ccomunkarray-class.md), który określa stałą liczbę połączeń.  
  
## <a name="remarks"></a>Uwagi  
 `IPropertyNotifySinkCP`dziedziczy wszystkie metody, za pośrednictwem swojej klasy podstawowej [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejs umożliwiający obiekt sink otrzymywać powiadomienia o zmianach właściwości. Klasa `IPropertyNotifySinkCP` udostępnia tego interfejsu jako interfejsu wychodzącego składnika obiektu. Klient musi implementować `IPropertyNotifySink` metody dla obiekt sink.  
  
 Pochodzi z klasy `IPropertyNotifySinkCP` gdy chcesz utworzyć punkt połączenia reprezentującą `IPropertyNotifySink` interfejsu.  
  
 Aby uzyskać więcej informacji o używaniu punkty połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)   
 [Klasa IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
