---
title: Klasa IOleInPlaceActiveObjectImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326587"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Klasa IOleInPlaceActiveObjectImpl

Ta klasa zawiera metody wspomagania komunikacji między formantem w miejscu a jego kontenerem.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IOleInPlaceActiveObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomoc kontekstową. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Włącza niemodowe okna dialogowe. Implementacja ATL zwraca S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Pobiera dojście do okna.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Powiadamia formant, gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane. Implementacja ATL zwraca S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Powiadamia formant, gdy okno ramki najwyższego poziomu kontenera jest aktywowane lub dezaktywowane. Implementacja ATL powraca|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informuje formant, że musi zmienić rozmiar jego obramowania. Implementacja ATL zwraca S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza komunikaty akceleratora menu z kontenera. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejs [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) pomaga w komunikacji między formantem w miejscu a jego kontenerem; na przykład komunikowanie aktywnego stanu formantu i kontenera i informowanie formantu, który musi zmienić rozmiar. Klasa `IOleInPlaceActiveObjectImpl` zapewnia domyślną `IOleInPlaceActiveObject` implementację i obsługuje, `IUnknown` wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Umożliwia pomoc kontekstową.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) w windows SDK.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless

Włącza niemodowe okna dialogowe.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) w windows SDK.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow

Kontener wywołuje tę funkcję, aby uzyskać dojście okna formantu.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Niektóre kontenery nie będzie działać z formantem, który został bez okien, nawet jeśli jest obecnie windowed. W implementacji ATL, `CComControl::m_bWasOnceWindowless` jeśli element członkowski danych jest TRUE, funkcja zwraca E_FAIL. W przeciwnym \* razie jeśli *phwnd* nie ma wartości NULL, `GetWindow` przypisuje `m_hWnd` *phwnd* do elementu członkowskiego danych klasy kontrolnej i zwraca S_OK.

Zobacz [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) w windows SDK.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Powiadamia formant, gdy okno dokumentu kontenera jest aktywowane lub dezaktywowane.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) w usłudze Windows SDK.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Powiadamia formant, gdy okno ramki najwyższego poziomu kontenera jest aktywowane lub dezaktywowane.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) w usłudze Windows SDK.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder

Informuje formant, że musi zmienić rozmiar jego obramowania.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) w windows SDK.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator

Przetwarza komunikaty akceleratora menu z kontenera.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda obsługuje następujące wartości zwracane:

S_OK, jeśli wiadomość została pomyślnie przetłumaczona.

S_FALSE, jeśli wiadomość nie została przetłumaczona.

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy sterowania ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
