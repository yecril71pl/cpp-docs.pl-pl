---
title: IOleInPlaCeObjectWindowlessImpl Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326576"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaCeObjectWindowlessImpl Klasa

Ta klasa `IUnknown` implementuje i udostępnia metody, które umożliwiają formant bez okien do odbierania komunikatów okna i do udziału w operacjach przeciągania i upuszczania.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleInPlaCeObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomoc kontekstową. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaCeObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Dostarcza `IDropTarget` interfejs dla obiektu aktywnego w miejscu, bez okien, który obsługuje przeciąganie i upuszczanie. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaCeObjectWindowlessImpl::GetWindow](#getwindow)|Pobiera dojście do okna.|
|[IOleInPlaCeObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Dezaktywuje aktywną kontrolę w miejscu.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Wysyła wiadomość z kontenera do formantu bez okien, który jest aktywny w miejscu.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Ponownie aktywuje wcześniej dezaktywowany formant. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaCeObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Wskazuje, jaka część formantu w miejscu jest widoczna.|
|[IOleInPlaCeObjectWindowlessImpl::UIDeactivate](#uideactivate)|Dezaktywuje i usuwa interfejs użytkownika obsługujący aktywację w miejscu.|

## <a name="remarks"></a>Uwagi

Interfejs [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) zarządza reaktywacją i dezaktywacją formantów w miejscu i określa, jaka część formantu powinna być widoczna. Interfejs [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) umożliwia formant bez okien do odbierania komunikatów okna i do udziału w operacjach przeciągania i upuszczania. Klasa `IOleInPlaceObjectWindowlessImpl` zapewnia domyślną `IOleInPlaceObject` `IOleInPlaceObjectWindowless` implementację `IUnknown` i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaCeObjectWindowlessImpl::ContextSensitiveHelp

Zwraca E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) w windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaCeObjectWindowlessImpl::GetDropTarget

Zwraca E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless::GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) w windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaCeObjectWindowlessImpl::GetWindow

Kontener wywołuje tę funkcję, aby uzyskać dojście okna formantu.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Niektóre kontenery nie będzie działać z formantem, który został bez okien, nawet jeśli jest obecnie windowed. W implementacji ATL, jeśli element członkowski `m_bWasOnceWindowless` danych klasy kontrolnej ma wartość TRUE, funkcja zwraca E_FAIL. W przeciwnym razie jeśli *phwnd* nie `GetWindow` jest null, ustawia \* *phwnd* do elementu członkowskiego `m_hWnd` danych klasy kontrolnej i zwraca S_OK.

Zobacz [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) w windows SDK.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaCeObjectWindowlessImpl::InPlaceDeactivate

Wywoływane przez kontener, aby dezaktywować formant aktywny w miejscu.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje pełną lub częściową dezaktywację w zależności od stanu formantu. W razie potrzeby interfejs użytkownika formantu jest dezaktywowany, a okno formantu, jeśli istnieje, zostanie zniszczone. Kontener jest powiadamiany, że formant nie jest już aktywny w miejscu. Interfejs `IOleInPlaceUIWindow` używany przez kontener do negocjowania menu i miejsca na granicy jest zwolniony.

Zobacz [IOleInPlaceObject::InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) w usłudze Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Wysyła wiadomość z kontenera do formantu bez okien, który jest aktywny w miejscu.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) w windows SDK.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Zwraca E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObject::ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) w windows SDK.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaCeObjectWindowlessImpl::SetObjectRects

Wywoływany przez kontener, aby poinformować formant, że jego rozmiar i/lub położenie uległy zmianie.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Uwagi

Aktualizuje element `m_rcPos` członkowski danych formantu i wyświetlacz sterowania. Wyświetlana jest tylko część formantu przecina, która przecina obszar klipu. Jeśli ekran formantu został wcześniej przycięty, ale przycinanie zostało usunięte, tę funkcję można wywołać, aby ponownie wyrywać pełny widok formantu.

Zobacz [IOleInPlaceObject::SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) w zestawie Windows SDK.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaCeObjectWindowlessImpl::UIDeactivate

Dezaktywuje i usuwa interfejs użytkownika formantu, który obsługuje aktywację w miejscu.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski `m_bUIActive` danych klasy kontrolnej na FAŁSZ. Implementacja atl tej funkcji zawsze zwraca S_OK.

Zobacz [IOleInPlaceObject::UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) w usłudze Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
