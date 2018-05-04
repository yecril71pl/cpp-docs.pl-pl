---
title: Klasa CFirePropNotifyEvent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 728f4e973a7ef74dcdbb44150375df235e0d990e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cfirepropnotifyevent-class"></a>Klasa CFirePropNotifyEvent
Ta klasa dostarcza metody do powiadamiania zbiornika kontenera dotyczące zmiany właściwości formantu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statyczny) Powiadamia zbiornika kontenera, który zmieniono właściwość formantu.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statyczny) Powiadamia zbiornika kontenera, który ma zmienić właściwości formantu.|  
  
## <a name="remarks"></a>Uwagi  
 `CFirePropNotifyEvent` ma dwie metody, które powiadamiają o zbiornika kontenera, który właściwości formantu został zmieniony lub ma zostać zmieniona.  
  
 Jeśli jest pochodną klasy Implementowanie formantu `IPropertyNotifySink`, `CFirePropNotifyEvent` metody są wywoływane podczas wywoływania `FireOnRequestEdit` lub `FireOnChanged`. Jeśli nie jest pochodną klasy formantu `IPropertyNotifySink`, zwracany wywołania funkcji `S_OK`.  
  
 Aby uzyskać więcej informacji o tworzeniu formantów, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged  
 Powiadamia wszystkie połączone [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejsów (na każdym punkcie połączenia obiektu), które właściwości określonego obiektu został zmieniony.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** obiektu wysyłania powiadomienia.  
  
 *dispID*  
 [in] Identyfikator właściwości, która została zmieniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest bezpiecznie wywołać nawet wtedy, gdy formant nie obsługuje punkty połączenia.  
  
##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit  
 Powiadamia wszystkie połączone [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejsów (na każdym punkcie połączenia obiektu), które właściwości określony obiekt ma zostać zmieniona.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** obiektu wysyłania powiadomienia.  
  
 *dispID*  
 [in] Identyfikator właściwości zostać zmieniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest bezpiecznie wywołać nawet wtedy, gdy formant nie obsługuje punkty połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
