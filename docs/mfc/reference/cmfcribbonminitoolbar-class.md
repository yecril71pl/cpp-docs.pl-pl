---
title: Klasa CMFCRibbonMiniToolBar
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 394182aa0f9c967524ed0db510d0b9cc0739118e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777158"
---
# <a name="cmfcribbonminitoolbar-class"></a>Klasa CMFCRibbonMiniToolBar

Implementuje kontekstowy podręczny pasek narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Domyślny konstruktor.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Przesłania `CMFCPopupMenu::IsRibbonMiniToolBar`).|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Ustawia listę poleceń, które mają być wyświetlane na pasku narzędzi.|
|[CMFCRibbonMiniToolBar::Show](#show)|Wyświetla podręczny pasek narzędzi na współrzędne ekranu.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Wyświetla podręczny pasek narzędzi wraz z menu kontekstowego.|

## <a name="remarks"></a>Uwagi

Podręczny pasek narzędzi jest zwykle wyświetlany po użytkownik wybierze obiekt w dokumencie. Na przykład po użytkownik wybiera blok tekstu w edytorze tekstu, aplikacja wyświetla podręczny pasek narzędzi, który zawiera polecenia służące do formatowania tekstu.

Podręczny pasek narzędzi staje się przezroczyste, gdy wskaźnik myszy znajduje się poza granicami podręczny pasek narzędzi.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Wymagania

**Header:** afxRibbonMiniToolBar.h

##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands

Ustawia listę poleceń, które mają być wyświetlane na pasku narzędzi.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parametry

*pRibbonBar*<br/>
[in] Paska wstążki, paska wyszukiwania przyciski, aby wyświetlić program.

*lstCommands*<br/>
[in] Lista poleceń, który będzie wyświetlany w podręczny pasek narzędzi. Wszystkie kategorie wstążki są przeszukiwane w celu skojarzone przycisk Znajdź.

### <a name="remarks"></a>Uwagi

Aby ustawić listę poleceń, które mają być wyświetlane w podręczny pasek narzędzi, należy użyć tej funkcji.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `SetCommands` metody `CMFCRibbonMiniToolBar` klasy. Ten fragment kodu jest częścią [próbka MS Office 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show

Wyświetla podręczny pasek narzędzi na współrzędne ekranu.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Określa położenie w poziomie podręczny pasek narzędzi w współrzędne ekranu.

*t*<br/>
[in] Określa położenie w pionie podręczny pasek narzędzi w współrzędne ekranu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie; zobrazilo podręczny pasek narzędzi w przeciwnym razie wartość FALSE.

##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu

Wyświetla podręczny pasek narzędzi wraz z menu kontekstowego.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Określa położenie menu kontekstowego w poziomie w współrzędne ekranu.

*t*<br/>
[in] Określa położenie menu kontekstowego w pionie w współrzędne ekranu.

*uiMenuResID*<br/>
[in] Określa identyfikator zasobu menu kontekstowe do wyświetlania.

*pWndOwner*<br/>
[in] Identyfikuje okna, która odbiera komunikaty z menu kontekstowego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie; zobrazilo menu kontekstowe w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia wyświetlenie mini pasek narzędzi, który ma menu kontekstowego. Menu kontekstowe jest określonym położeniem 15 pikseli poniżej podręczny pasek narzędzi.

##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
