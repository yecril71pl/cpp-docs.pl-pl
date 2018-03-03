---
title: Klasa IQuickActivateImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6f5bc1798bc8ec40fb6f6d9d22f48c06b19745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iquickactivateimpl-class"></a>Klasa IQuickActivateImpl
Ta klasa łączy inicjowania formantu kontenery w pojedynczym wywołaniu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IQuickActivateImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Wykonuje szybkiego inicjowania formantów ładowany.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o sterowania ile miejsca jest przypisywana kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interfejsu pomaga uniknąć opóźnienia podczas ładowania kontrolki łącząc inicjowania w pojedynczym wywołaniu kontenerów. `QuickActivate` Metoda pozwala kontener, aby przekazać wskaźnika do [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) strukturę, która przechowuje wskaźników do wszystkich interfejsów formantu wymaga. Przy powrocie, formantu odsyła wskaźnik do [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) strukturę, która przechowuje wskaźników do jego własnej interfejsów, które są używane przez kontener. Klasa `IQuickActivateImpl` udostępnia domyślną implementację elementu **IQuickActivate** i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar jest pełna renderowania formantu i jest określony w HIMETRIC jednostki.  
  
 Zobacz [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) w systemie Windows SDK.  
  
##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 Wykonuje szybkiego inicjowania formantów ładowany.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura zawiera wskaźniki do interfejsów wymaganych przez formant i wartości niektórych właściwości otoczenia. Po powrocie, formantu przekazuje wskaźnik do [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) strukturę, która zawiera łącza do własnej interfejsów, które wymaga kontenera i dodatkowe informacje.  
  
 Zobacz [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) w systemie Windows SDK.  
  
##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 Informuje o sterowania ile miejsca jest przypisywana kontenera.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar ten określa się w jednostkach HIMETRIC.  
  
 Zobacz [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
