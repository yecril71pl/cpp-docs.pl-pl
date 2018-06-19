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
ms.openlocfilehash: 5a54067f53e83d78f063ae5f3694460452e24b26
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361801"
---
# <a name="iolecontrolimpl-class"></a>Klasa IOleControlImpl
Ta klasa udostępnia domyślną implementację **IOleControl** interfejsu i implementuje **IUnknown**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IOleControlImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Wskazuje, czy kontener ignoruje lub akceptuje zdarzeń z formantu.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Wypełnia informacji dotyczących zachowania klawiatury formantu. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o formantu przynajmniej jedna z właściwości otaczających kontenera została zmieniona. Zwraca implementację ATL `S_OK`.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o formantu że użytkownik nacisnął określonego naciśnięcie klawisza. Zwraca implementację ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `IOleControlImpl` udostępnia domyślną implementację elementu [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 W implementacji firmy ATL `FreezeEvents` zwiększa klasy formantu `m_nFreezeEvents` element członkowski danych Jeśli `bFreeze` jest **TRUE**i zmniejsza `m_nFreezeEvents` Jeśli `bFreeze` jest **FALSE**.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Uwagi  
 `FreezeEvents` Zwraca `S_OK`.  
  
 Zobacz [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) w systemie Windows SDK.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Wypełnia informacji dotyczących zachowania klawiatury formantu.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Informuje o formantu przynajmniej jedna z właściwości otaczających kontenera została zmieniona.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) w systemie Windows SDK.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informuje o formantu że użytkownik nacisnął określonego naciśnięcie klawisza.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)   
 [Interfejsy formantów ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Przegląd klas](../../atl/atl-class-overview.md)
