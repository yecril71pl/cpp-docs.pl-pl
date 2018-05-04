---
title: Klasa IOleInPlaceActiveObjectImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d98b8dd082a09de461452b43b70ddeb9431abe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Klasa IOleInPlaceActiveObjectImpl
Ta klasa dostarcza metody do wspomagania komunikacji między formantem w miejscu, a jego kontenera.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomoc kontekstową. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Umożliwia Niemodalne okna dialogowe. Zwraca implementację ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Pobiera uchwytu okna.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Powiadamia kontrolkę, gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane. Zwraca implementację ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Powiadamia kontrolkę, gdy kontenera okna ramowego najwyższego poziomu jest aktywowane lub dezaktywowane. Zwraca implementację ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Należy zmienić rozmiar obramowania informuje o formantu. Zwraca implementację ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza wiadomości klawisz skrótu menu z kontenera. Zwraca implementację ATL **E_NOTIMPL**.|  
  
  
## <a name="remarks"></a>Uwagi  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfejsu pomaga komunikacji między formantem w miejscu, a jego kontenera; na przykład komunikuje stanu aktywnego sterowania i kontener i informowanie formantu konieczne zmiany rozmiaru samego siebie. Klasa `IOleInPlaceActiveObjectImpl` udostępnia domyślną implementację elementu `IOleInPlaceActiveObject` i obsługuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Umożliwia pomoc kontekstową.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) w systemie Windows SDK.  
  
##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless  
 Umożliwia Niemodalne okna dialogowe.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) w systemie Windows SDK.  
  
##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow  
 Kontener wywołuje tej funkcji można pobrać uchwytu okna formantu.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Uwagi  
 Niektóre kontenery nie będzie działać z formantem został bez okien, nawet jeśli jest ona obecnie okna. W implementacji firmy ATL Jeśli **CComControl::m_bWasOnceWindowless** elementu członkowskiego danych jest **TRUE**, funkcja zwraca **E_FAIL**. W przeciwnym razie, jeśli \* *phwnd* nie jest **NULL**, `GetWindow` przypisuje *phwnd* na element członkowski danych klasy formantu `m_hWnd` i zwraca `S_OK`.  
  
 Zobacz [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) w systemie Windows SDK.  
  
##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Powiadamia kontrolkę, gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) w systemie Windows SDK.  
  
##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Powiadamia kontrolkę, gdy kontenera okna ramowego najwyższego poziomu jest aktywowane lub dezaktywowane.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) w systemie Windows SDK.  
  
##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder  
 Należy zmienić rozmiar obramowania informuje o formantu.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) w systemie Windows SDK.  
  
##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Przetwarza wiadomości klawisz skrótu menu z kontenera.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda obsługuje zwraca następujące wartości:  
  
 `S_OK` Jeśli komunikat przetłumaczony pomyślnie.  
  
 **Wartości S_FALSE** Jeśli wiadomość nie została przekonwertowana.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)  
 [Interfejsy formantów ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Przegląd klas](../../atl/atl-class-overview.md)
