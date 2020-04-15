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
ms.openlocfilehash: 10b1d35c331df6563d09be0bea3c97c73e89acaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375089"
---
# <a name="cmfcribbonminitoolbar-class"></a>Klasa CMFCRibbonMiniToolBar

Implementuje kontekstowy pasek narzędzi wyskakujących.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Domyślny konstruktor.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Przesłania `CMFCPopupMenu::IsRibbonMiniToolBar`).|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Ustawia listę poleceń, które mają być wyświetlane na pasku narzędzi.|
|[CMFCRibbonMiniToolBar::Pokaż](#show)|Wyświetla minipasek narzędzi na określonych współrzędnych ekranu.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Wyświetla mini pasek narzędzi wraz z menu kontekstowym.|

## <a name="remarks"></a>Uwagi

Minipasek narzędzi jest zazwyczaj wyświetlany po wybraniu obiektu przez użytkownika w dokumencie. Na przykład po wybraniu przez użytkownika bloku tekstu w programie do przetwarzania tekstu aplikacja wyświetli mini pasek narzędzi zawierający polecenia formatowania tekstu.

Minipasek narzędzi staje się przezroczysty, gdy wskaźnik myszy znajduje się poza granicami mini paska narzędzi.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd (CMiniFrameWnd)](../../mfc/reference/cminiframewnd-class.md)

[Cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands

Ustawia listę poleceń, które mają być wyświetlane na pasku narzędzi.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parametry

*pRibbonBar (pRibbonBar)*<br/>
[w] Pasek wstążki, który mini pasek narzędzi wyszukuje przyciski do wyświetlenia.

*lstCommands ( lstCommands )*<br/>
[w] Lista poleceń wyświetlanych na mini pasku narzędzi. Przeszukiwane są wszystkie kategorie wstążki w celu znalezienia skojarzonych przycisków.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do ustawiania listy poleceń wyświetlanych na mini pasku narzędzi.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `SetCommands` metody `CMFCRibbonMiniToolBar` klasy. Ten fragment kodu jest częścią [przykładu demo pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Pokaż

Wyświetla minipasek narzędzi na określonych współrzędnych ekranu.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Określa poziome położenie minipaska narzędzi we współrzędnych ekranu.

*Y*<br/>
[w] Określa położenie w pionie minipaska narzędzi we współrzędnych ekranu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli mini pasek narzędzi został wyświetlony pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu

Wyświetla mini pasek narzędzi wraz z menu kontekstowym.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Określa poziome położenie menu kontekstowego we współrzędnych ekranu.

*Y*<br/>
[w] Określa pionowe położenie menu kontekstowego we współrzędnych ekranu.

*interfejs użytkownika uiMenuResID*<br/>
[w] Określa identyfikator zasobu menu kontekstowego do wyświetlenia.

*pWndOwner*<br/>
[w] Identyfikuje okno, które odbiera wiadomości z menu kontekstowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli menu kontekstowe zostało wyświetlone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do wyświetlania mini paska narzędzi z menu kontekstowym. Menu kontekstowe znajduje się 15 pikseli poniżej mini paska narzędzi.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
