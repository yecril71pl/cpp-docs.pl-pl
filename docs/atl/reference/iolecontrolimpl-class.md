---
title: Klasa IOleControlImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34bdb0af5965b300e77a02858af3708c90fa63d0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879286"
---
# <a name="iolecontrolimpl-class"></a>Klasa IOleControlImpl
Ta klasa udostępnia domyślną implementację elementu `IOleControl` interfejsu i implementuje `IUnknown`.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IOleControlImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Wskazuje, czy kontener ignoruje lub akceptuje zdarzeń formantu.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Kopiuje informacje o zachowanie klawiatury formantu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o kontrolce przynajmniej jedna z właściwości otoczenia kontenera został zmieniony. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o kontrolki użytkownik naciśnie określony naciśnięcia klawisza. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `IOleControlImpl` udostępnia domyślną implementację elementu [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 W implementacji ATL `FreezeEvents` zwiększa Twojej klasy kontrolki `m_nFreezeEvents` element członkowski danych Jeśli `bFreeze` jest PRAWDA, a także zmniejsza `m_nFreezeEvents` Jeśli `bFreeze` ma wartość FALSE.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Uwagi  
 `FreezeEvents` następnie zwraca wartość S_OK.  
  
 Zobacz [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) w Windows SDK.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Kopiuje informacje o zachowanie klawiatury formantu.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) w Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Informuje o kontrolce przynajmniej jedna z właściwości otoczenia kontenera został zmieniony.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) w Windows SDK.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informuje o kontrolki użytkownik naciśnie określony naciśnięcia klawisza.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)   
 [Interfejsy kontrolki ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
