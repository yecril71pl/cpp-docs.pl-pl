---
title: Klasa IPointerInactiveImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs: C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe45700a941a8a59439b816124728f43e5f54f44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ipointerinactiveimpl-class"></a>Klasa IPointerInactiveImpl
Ta klasa implementuje **IUnknown** i [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) metod interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPointerInactiveImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Pobiera bieżące zasady aktywacji dla obiekt. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Powiadamia obiektu przeniesionej wskaźnik myszy nad nim, wskazując obiekt mogą wyzwalać zdarzeń myszy. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Ustawia kursor dla obiekt nieaktywne. Zwraca implementację ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Uwagi  
 Nieaktywne obiekt jest taki, który jest po prostu załadowany lub jest uruchomiony. W przeciwieństwie do aktywnego obiektu nieaktywnym obiektem nie może otrzymywać komunikatów myszy i klawiatury systemu Windows. W związku z tym obiektów nieaktywnych wykorzystuje mniej zasobów i są zazwyczaj bardziej wydajne.  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) interfejs umożliwiający obiektu do obsługi minimalny poziom interakcji z myszą zachowując nieaktywne. Ta funkcja jest szczególnie przydatne dla formantów.  
  
 Klasa `IPointerInactiveImpl` implementuje `IPointerInactive` metody po prostu zwracając **E_NOTIMPL**. Jednak implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 Pobiera bieżące zasady aktywacji dla obiekt.  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) w systemie Windows SDK.  
  
##  <a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 Powiadamia obiektu przeniesionej wskaźnik myszy nad nim, wskazując obiekt mogą wyzwalać zdarzeń myszy.  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) w systemie Windows SDK.  
  
##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 Ustawia kursor dla obiekt nieaktywne.  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
