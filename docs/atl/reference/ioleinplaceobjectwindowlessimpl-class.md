---
title: Klasa IOleInPlaceObjectWindowlessImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f455172723be4f46751b45d244e74dda5fcacae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Klasa IOleInPlaceObjectWindowlessImpl
Ta klasa implementuje **IUnknown** i dostarcza metod umożliwiających formantem bez okien do odbierania komunikatów okien i uczestniczyć w operacji przeciągania i upuszczania.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IOleInPlaceObjectWindowlessImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomoc kontekstową. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Dostaw `IDropTarget` interfejs dla obiekt w miejscu aktywne, bez okien, który obsługuje przeciągania i upuszczania. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Pobiera uchwytu okna.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Dezaktywuje aktywny formant w miejscu.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Wysyła wiadomość z kontenera z formantem bez okien, który jest aktywny w miejscu.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Uaktywnia ponownie wcześniej wyłączone formantu. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Wskazuje, jaka część kontroli w miejscu jest widoczny.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Dezaktywuje i usuwa interfejs użytkownika, który obsługuje aktywacji w miejscu.|  
  
## <a name="remarks"></a>Uwagi  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfejsu zarządza ponownej aktywacji i dezaktywacji w miejscu kontrolki oraz określa, ile formantu powinny być widoczne. [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfejs umożliwia kontrolce bezokienkowej do odbierania komunikatów okien i uczestniczyć w operacji przeciągania i upuszczania. Klasa `IOleInPlaceObjectWindowlessImpl` udostępnia domyślną implementację elementu `IOleInPlaceObject` i `IOleInPlaceObjectWindowless` i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 Zwraca **E_NOTIMPL**.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) w systemie Windows SDK.  
  
##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Zwraca **E_NOTIMPL**.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) w systemie Windows SDK.  
  
##  <a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow  
 Kontener wywołuje tej funkcji można pobrać uchwytu okna formantu.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Uwagi  
 Niektóre kontenery nie będzie działać z formantem został bez okien, nawet jeśli jest ona obecnie okna. W implementacji firmy ATL Jeśli element członkowski danych klasy formantu `m_bWasOnceWindowless` jest **TRUE**, funkcja zwraca **E_FAIL**. W przeciwnym razie, jeśli *phwnd* nie jest **NULL**, `GetWindow` ustawia \* *phwnd* na element członkowski danych klasy formantu `m_hWnd` i zwraca `S_OK`.  
  
 Zobacz [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) w systemie Windows SDK.  
  
##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Metoda wywoływana przez kontener, aby zdezaktywować w miejscu aktywny formant.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wykonuje pełnej lub częściowej dezaktywacji w zależności od stanu formantu. W razie potrzeby formantu interfejsu użytkownika jest dezaktywowana i formantu okna, jeśli istnieje, zostanie zniszczony. Kontener jest powiadamiany o to, że formant nie jest już aktywny w miejscu. **IOleInPlaceUIWindow** interfejs używany przez kontener do negocjowania menu i obramowania miejsca zostanie zwolniony.  
  
 Zobacz [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) w systemie Windows SDK.  
  
##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 Wysyła wiadomość z kontenera z formantem bez okien, który jest aktywny w miejscu.  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) w systemie Windows SDK.  
  
##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Zwraca **E_NOTIMPL**.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) w systemie Windows SDK.  
  
##  <a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 Metoda wywoływana przez kontener, aby poinformować formant, który zmienił jego rozmiaru i/lub pozycji.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje formantu `m_rcPos` element członkowski danych i wyświetlanie formantu. Wyświetlane jest tylko część formant, który przecina obszar przycinania. Jeśli wcześniej została obcięta wyświetlanie formantu, ale wycinka został usunięty, tę funkcję można wywołać ponowne pełnego widoku formantu.  
  
 Zobacz [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) w systemie Windows SDK.  
  
##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Dezaktywuje i usuwa formantu interfejsu użytkownika, który obsługuje aktywacji w miejscu.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia element członkowski danych klasy formantu `m_bUIActive` do **FALSE**. Implementacja ATL funkcji zawsze zwraca `S_OK`.  
  
 Zobacz [IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
