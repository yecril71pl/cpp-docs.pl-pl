---
title: Klasa IQuickActivateImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9131a1cc1f8d0c66f2eb3616f4903db74ea4bdf0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881376"
---
# <a name="iquickactivateimpl-class"></a>Klasa IQuickActivateImpl
Ta klasa łączy inicjowania kontroli kontenery w jednym wywołaniu.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IQuickActivateImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Wykonuje szybkie inicjowanie kontrolki ładowany.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o kontroli ilości wykorzystanego miejsca wyświetlania kontener został przypisany do niego.|  
  
## <a name="remarks"></a>Uwagi  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interfejsu pomaga uniknąć opóźnień, podczas ładowania formantów, łącząc inicjowania w pojedynczym wywołaniu kontenerów. `QuickActivate` Metoda umożliwia kontener, aby przekazać wskaźnik do [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) musi strukturę, która przechowuje wskaźniki do wszystkich interfejsów kontrolki. Przy powrocie, kontrola przechodzi wstecz wskaźnik do [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) strukturę, która przechowuje wskaźniki do jego własnej interfejsów, które są używane przez kontener. Klasa `IQuickActivateImpl` udostępnia domyślną implementację elementu `IQuickActivate` i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 Pobiera bieżący rozmiar wyświetlania kontrolki uruchomione.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar jest pełna renderowanie formantu i jest określony w jednostkach HIMETRIC.  
  
 Zobacz [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) w Windows SDK.  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 Wykonuje szybkie inicjowanie kontrolki ładowany.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura zawiera wskaźniki do interfejsów, które wymagają kontroli i wartości niektórych właściwości otoczenia. Po powrocie, kontrola przechodzi wskaźnik do [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) strukturę, która zawiera wskaźniki do własnej interfejsy, które wymaga kontenera i informacje o stanie dodatkowe.  
  
 Zobacz [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) w Windows SDK.  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 Informuje o kontroli ilości wykorzystanego miejsca wyświetlania kontener został przypisany do niego.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar określa się w jednostkach HIMETRIC.  
  
 Zobacz [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
