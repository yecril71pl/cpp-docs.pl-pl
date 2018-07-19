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
ms.openlocfilehash: 1339f41a0764e44f46bed7ad24181ce406998c22
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885604"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Klasa IOleInPlaceActiveObjectImpl
Ta klasa dostarcza metody obsługi komunikacji między formantem w miejscu, a jego kontenera.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomocy kontekstowej. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Umożliwia Niemodalne okna dialogowe. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Pobiera uchwyt okna.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Powiadamia kontrolkę gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Powiadamia kontrolkę gdy okno ramek najwyższego poziomu kontenera jest aktywowane lub dezaktywowane. Zwraca implementację ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informuje o kontrolki, potrzebne do zmiany rozmiaru jego obramowania. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza wiadomości klawisza skrótu menu z kontenera. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
  
  
## <a name="remarks"></a>Uwagi  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfejsu pomaga komunikacji między formantem w miejscu, a jego kontenera; na przykład komunikacji stanu aktywnego sterowania i kontenerów oraz informowanie kontrolki potrzeba zmiany rozmiaru samego siebie. Klasa `IOleInPlaceActiveObjectImpl` udostępnia domyślną implementację elementu `IOleInPlaceActiveObject` i obsługuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Umożliwia pomocy kontekstowej.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) w Windows SDK.  
  
##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless  
 Umożliwia Niemodalne okna dialogowe.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) w Windows SDK.  
  
##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow  
 Kontener wywoła tę funkcję, aby pobrać uchwytu okna kontrolki.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Uwagi  
 Niektóre kontenery nie będzie działać z formant, który został niepowiązanej z oknami, nawet jeśli jest on obecnie okna. W implementacji ATL Jeśli `CComControl::m_bWasOnceWindowless` element członkowski danych ma wartość PRAWDA, funkcja zwraca E_FAIL. W przeciwnym razie, jeśli \* *phwnd* nie ma wartości NULL, `GetWindow` przypisuje *phwnd* do klasy formantu element członkowski danych `m_hWnd` i zwraca wartość S_OK.  
  
 Zobacz [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) w Windows SDK.  
  
##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Powiadamia kontrolkę gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) w Windows SDK.  
  
##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Powiadamia kontrolkę gdy okno ramek najwyższego poziomu kontenera jest aktywowane lub dezaktywowane.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) w Windows SDK.  
  
##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder  
 Informuje o kontrolki, potrzebne do zmiany rozmiaru jego obramowania.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) w Windows SDK.  
  
##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Przetwarza wiadomości klawisza skrótu menu z kontenera.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda obsługuje zwraca następujące wartości:  
  
 S_OK, jeśli komunikat został przetłumaczony pomyślnie.  
  
 S_FALSE, jeśli wiadomość nie została przekonwertowana.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)  
 [Interfejsy kontrolki ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
