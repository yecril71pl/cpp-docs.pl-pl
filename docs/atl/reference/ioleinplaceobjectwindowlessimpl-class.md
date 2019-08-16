---
title: IOleInPlaceObjectWindowlessImpl Class
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
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495748"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl Class

Ta klasa implementuje `IUnknown` i udostępnia metody, które umożliwiają kontrolowanie bezokienkowe odbierania komunikatów okna i uczestnictwo w operacjach przeciągania i upuszczania.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Włącza pomoc kontekstową. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|`IDropTarget` Dostarcza interfejs dla aktywnego, bezokienkowego obiektu, który obsługuje przeciąganie i upuszczanie. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Pobiera uchwyt okna.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Dezaktywuje aktywny formant w miejscu.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Wysyła komunikat z kontenera do kontrolki bez okna, która jest aktywna.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Uaktywnia wcześniej zdezaktywowaną kontrolkę. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Wskazuje, która część kontrolki miejscowej jest widoczna.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Dezaktywuje i usuwa interfejs użytkownika obsługujący aktywację w miejscu.|

## <a name="remarks"></a>Uwagi

Interfejs [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) zarządza ponowną aktywacją i dezaktywacją kontrolek miejscowych i określa, jaka część kontrolki powinna być widoczna. Interfejs [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) umożliwia kontrolowanie bezokienkowe odbierania komunikatów okna i uczestnictwo w operacjach przeciągania i upuszczania. Klasa `IOleInPlaceObjectWindowlessImpl` udostępnia domyślną `IOleInPlaceObject` implementację i `IOleInPlaceObjectWindowless` i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Zwraca E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) w Windows SDK.

##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget

Zwraca E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) w Windows SDK.

##  <a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl:: GetWindow

Kontener wywołuje tę funkcję, aby uzyskać uchwyt okna kontrolki.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Niektóre kontenery nie będą współdziałać z kontrolką, która jest bez okna, nawet jeśli jest w tym oknie. W implementacji ATL, jeśli element członkowski `m_bWasOnceWindowless` danych klasy kontroli ma wartość true, funkcja zwraca wartość E_FAIL. W przeciwnym razie, jeśli *phwnd* nie ma `GetWindow` wartości \* null, ustawia *phwnd* dla elementu członkowskiego `m_hWnd` danych klasy kontrolki i zwraca S_OK.

Zobacz [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) w Windows SDK.

##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Wywoływane przez kontener, aby dezaktywować aktywny formant w miejscu.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Ta metoda przeprowadza pełną lub częściową dezaktywację w zależności od stanu formantu. W razie potrzeby interfejs użytkownika kontrolki jest dezaktywowany, a okno kontrolki, jeśli istnieje, jest niszczone. Kontener zostaje powiadomiony o tym, że formant nie jest już aktywny. `IOleInPlaceUIWindow` Interfejs używany przez kontener do negocjowania menu i miejsca obramowania jest publikowany.

Zobacz [IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) w Windows SDK.

##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Wysyła komunikat z kontenera do bezokienkowego formantu, który jest aktywny.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) w Windows SDK.

##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Zwraca E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) w Windows SDK.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Wywoływane przez kontener, aby poinformować formant o zmianie jego rozmiaru i/lub położenia.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Uwagi

Aktualizuje element członkowski `m_rcPos` danych kontrolki i kontrolkę wyświetlania. Wyświetlana jest tylko część kontrolki, która przecina się z regionem klipu. Jeśli ekran kontrolki został poprzednio przycięty, ale wycink został usunięty, ta funkcja może zostać wywołana w celu ponownego narysowania pełnego widoku formantu.

Zobacz [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) w Windows SDK.

##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate

Dezaktywuje i usuwa interfejs użytkownika kontrolki, który obsługuje aktywację w miejscu.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski `m_bUIActive` danych klasy kontrolki na wartość false. Implementacja ATL tej funkcji zawsze zwraca S_OK.

Zobacz [IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
