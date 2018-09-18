---
title: Klasa IOleInPlaceObjectWindowlessImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 112700fffc3b4104599f68f80f00e8d3239788f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089570"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Klasa IOleInPlaceObjectWindowlessImpl

Ta klasa implementuje `IUnknown` i dostarcza metod, które umożliwiają kontrolce do odbierania komunikatów okien i uczestniczyć w operacji przeciągania i upuszczania.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umożliwia pomocy kontekstowej. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Dostarcza `IDropTarget` interfejs w miejscu aktywne, bez okien obiekt, który obsługuje przeciągania i upuszczania. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Pobiera uchwyt okna.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Dezaktywuje aktywny formant w miejscu.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Wysyła komunikat z kontenera do formantu bez okien, który jest aktywny w miejscu.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Ponownie uaktywnia te błędy kontroli wcześniej dezaktywowane. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Wskazuje, jaka część kontroli w miejscu jest widoczna.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Dezaktywuje i usuwa interfejs użytkownika, który obsługuje aktywacji w miejscu.|

## <a name="remarks"></a>Uwagi

[IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject) interfejsu zarządza ponowna aktywacja i dezaktywacja w miejscu kontroluje oraz określa, ile kontrolki powinny być widoczne. [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) interfejs umożliwia kontrolce do odbierania komunikatów okien i uczestniczyć w operacji przeciągania i upuszczania. Klasa `IOleInPlaceObjectWindowlessImpl` udostępnia domyślną implementację elementu `IOleInPlaceObject` i `IOleInPlaceObjectWindowless` i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Zwraca E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) w Windows SDK.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Zwraca E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless::GetDropTarget](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) w Windows SDK.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

Kontener wywoła tę funkcję, aby pobrać uchwytu okna kontrolki.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Niektóre kontenery nie będzie działać z formant, który został niepowiązanej z oknami, nawet jeśli jest on obecnie okna. W implementacji ATL Jeśli element członkowski danych Twojej klasy kontrolki `m_bWasOnceWindowless` ma wartość PRAWDA, funkcja zwraca E_FAIL. W przeciwnym razie, jeśli *phwnd* nie ma wartości NULL, `GetWindow` ustawia \* *phwnd* do klasy formantu element członkowski danych `m_hWnd` i zwraca wartość S_OK.

Zobacz [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) w Windows SDK.

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Metoda wywoływana przez kontener do dezaktywowania aktywny formant w miejscu.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Uwagi

Ta metoda przeprowadza pełnej lub częściowej dezaktywacji w zależności od stanu kontrolki. W razie potrzeby dezaktywacji kontrolki interfejsu użytkownika, a oknie kontrolki, zostanie zniszczony. Kontener zostanie powiadomiony, że kontrolka nie jest już aktywny w miejscu. `IOleInPlaceUIWindow` Udostępnieniu interfejsu używanego przez kontener do negocjowania menu i obramowanie miejsca.

Zobacz [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) w Windows SDK.

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Wysyła komunikat z kontenera do formantu bez okien, który jest aktywny w miejscu.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) w Windows SDK.

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Zwraca E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) w Windows SDK.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Metoda wywoływana przez kontener, aby poinformować formant, który zmienił jego rozmiaru i/lub położenia.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Uwagi

Aktualizuje formantu `m_rcPos` element członkowski danych i wyświetlania kontrolki. Jest wyświetlana tylko część formant, który przecina obszar przycinania. Jeśli wyświetlanie formantu wcześniej została obcięta, ale wycinka został usunięty, można wywołać tę funkcję, ponowne pełnego widoku formantu.

Zobacz [IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) w Windows SDK.

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

Dezaktywuje i usuwa kontrolki interfejsu użytkownika, który obsługuje aktywacji w miejscu.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski danych Twojej klasy kontrolki `m_bUIActive` na wartość FALSE. ATL wykonania ta funkcja zawsze zwraca wartość S_OK.

Zobacz [IOleInPlaceObject::UIDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
