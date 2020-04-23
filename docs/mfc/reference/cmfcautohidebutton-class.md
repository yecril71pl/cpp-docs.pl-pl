---
title: Klasa CMFCAutoHideButton
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751670"
---
# <a name="cmfcautohidebutton-class"></a>Klasa CMFCAutoHideButton

Przycisk, który wyświetla lub ukrywa [CDockablePane Klasy,](../../mfc/reference/cdockablepane-class.md) który jest skonfigurowany do ukrycia.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Utwórz](#create)|Tworzy i inicjuje przycisk automatycznego ukrywania.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Pobiera wyrównanie przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Zwraca obiekt [CDockablePane](../../mfc/reference/cdockablepane-class.md) skojarzony z przyciskiem automatycznego ukrywania.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Określa rozmiar przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Zwraca rozmiar etykiety tekstowej przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Przycisk automatycznego ukrywania podświetla.|
|[CMFCAutoHideButton::IsActive](#isactive)|Wskazuje, czy przycisk automatycznego ukrywania jest aktywny.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Zwraca stan podświetlenia przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Określa, czy przycisk automatycznego ukrywania jest poziomy czy pionowy.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|Wskazuje, czy przycisk jest widoczny.|
|[CMFCAutoHideButton::Przenieś](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|Struktura wywołuje tę metodę, gdy rysuje przycisk automatycznego ukrywania.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Struktura wywołuje tę metodę, gdy rysuje obramowanie przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Struktura wywołuje tę metodę, gdy wypełnia tło przycisku automatycznego ukrywania.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Pokazuje lub ukrywa skojarzoną [klasę CDockablePane](../../mfc/reference/cdockablepane-class.md).|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Pokazuje lub ukrywa przycisk automatycznego ukrywania.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Uwagi

Podczas tworzenia `CMFCAutoHideButton` obiekt jest dołączony do [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md). Obiekt `CDockablePane` jest ukryty lub wyświetlany, gdy użytkownik `CMFCAutoHideButton` wchodzi w interakcję z obiektem.

Domyślnie struktura automatycznie `CMFCAutoHideButton` tworzy, gdy użytkownik włącza automatyczne ukrywanie. Ramach można utworzyć element niestandardowej klasy interfejsu użytkownika `CMFCAutoHideButton` zamiast klasy. Aby określić, która niestandardowa klasa interfejsu użytkownika powinna `CMFCAutoHideBar::m_pAutoHideButtonRTS` być używana, należy ustawić statyczną zmienną elementów członkowskich równą niestandardowej klasie interfejsu użytkownika. Domyślnie ta zmienna `CMFCAutoHideButton`jest ustawiona na .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCAutoHideButton` `CMFCAutoHideButton` obiekt i używać różnych metod w klasie. W przykładzie pokazano, `CMFCAutoHideButton` jak zainicjować `Create` obiekt przy użyciu `CDockablePane` jego metody, pokazać skojarzoną klasę i pokazać przycisk automatycznego ukrywania.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFCAutoHideButton::BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFCAutoHideButton::Utwórz

Tworzy i inicjuje przycisk automatycznego ukrywania.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pParentBar (Bar)*<br/>
[w] Wskaźnik do nadrzędnego paska narzędzi.

*pAutoHideWnd*<br/>
[w] Wskaźnik do obiektu [CDockablePane.](../../mfc/reference/cdockablepane-class.md) Ten przycisk automatycznego ukrywania `CDockablePane`i pokazuje, że .

*dwZładna*<br/>
[w] Wartość określająca wyrównanie przycisku do okna ramki głównej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podczas tworzenia `CMFCAutoHideButton` obiektu należy skojarzyć przycisk automatycznego `CDockablePane`ukrywania z określonym . Użytkownik może użyć przycisku automatycznego ukrywania, `CDockablePane`aby ukryć i pokazać skojarzony plik .

Parametr *dwAlignment wskazuje,* gdzie znajduje się przycisk automatycznego ukrywania w aplikacji. Parametr może być jedną z następujących wartości:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFCAutoHideButton::GetAlignment

Pobiera wyrównanie przycisku automatycznego ukrywania.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawierająca bieżące wyrównanie przycisku automatycznego ukrywania.

### <a name="remarks"></a>Uwagi

Wyrównanie przycisku automatycznego ukrywania wskazuje, gdzie znajduje się przycisk w aplikacji. Może to być jedna z następujących wartości:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow

Zwraca obiekt [CDockablePane](../../mfc/reference/cdockablepane-class.md) skojarzony z przyciskiem automatycznego ukrywania.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do skojarzonego `CDockablePane` obiektu.

### <a name="remarks"></a>Uwagi

Aby skojarzyć przycisk automatycznego ukrywania z `CDockablePane`, przekazać `CDockablePane` jako parametr do [CMFCAutoHideButton::Create](#create) metody.

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFCAutoHideButton::GetSize

Określa rozmiar przycisku automatycznego ukrywania.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CSize` który zawiera rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Obliczony rozmiar obejmuje rozmiar obramowania przycisku automatycznego ukrywania.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize

Zwraca rozmiar etykiety tekstowej przycisku automatycznego ukrywania.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) zawierający rozmiar tekstu przycisku automatycznego ukrywania.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFCAutoHideButton::IsActive

Wskazuje, czy przycisk automatycznego ukrywania jest aktywny.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk automatycznego ukrywania jest aktywny; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Przycisk automatycznego ukrywania jest aktywny, gdy wyświetlane jest skojarzone okno [CDockablePane Class.](../../mfc/reference/cdockablepane-class.md)

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal

Określa, czy przycisk automatycznego ukrywania jest poziomy czy pionowy.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk jest poziomy; 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Struktura ustawia orientację [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektu podczas tworzenia go.  Orientację można kontrolować za pomocą parametru *dwAlignment* w [metodzie CMFCAutoHideButton::Create.](#create)

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFCAutoHideButton::IsVisible

Wskazuje, czy przycisk automatycznego ukrywania jest widoczny.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk jest widoczny; FAŁSZ inaczej.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFCAutoHideButton::OnDraw

Struktura wywołuje tę metodę, gdy rysuje przycisk automatycznego ukrywania.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Jeśli chcesz dostosować wygląd przycisków automatycznego ukrywania w aplikacji, utwórz `CMFCAutoHideButton`nową klasę pochodzącą z programu . W klasie pochodnej należy zastąpić tę metodę.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder

Struktura wywołuje tę metodę, gdy rysuje obramowanie przycisku automatycznego ukrywania.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectBounds (Obfity)*<br/>
[w] Prostokąt ograniczający przycisk automatycznego ukrywania.

*rozmiar rectBorderSize*<br/>
[w] Grubość obramowania dla każdej strony przycisku automatycznego ukrywania.

### <a name="remarks"></a>Uwagi

Jeśli chcesz dostosować obramowanie każdego przycisku automatycznego ukrywania w aplikacji, `CMFCAutoHideButton`utwórz nową klasę wywodzącą się z pliku . W klasie pochodnej należy zastąpić tę metodę.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground

Struktura wywołuje tę metodę, gdy wypełnia tło przycisku automatycznego ukrywania.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający przycisk automatycznego ukrywania.

### <a name="remarks"></a>Uwagi

Jeśli chcesz dostosować tło dla przycisków automatycznego ukrywania w aplikacji, utwórz nową klasę pochodzącą `CMFCAutoHideButton`z programu . W klasie pochodnej należy zastąpić tę metodę.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow

Pokazuje lub ukrywa skojarzoną [klasę CDockablePane](../../mfc/reference/cdockablepane-class.md).

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] Wartość logiczna określająca, czy ta `CDockablePane`metoda pokazuje dołączony plik .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFCAutoHideButton::ShowButton

Pokazuje lub ukrywa przycisk automatycznego ukrywania.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] Wartość logiczna określająca, czy przycisk automatycznego ukrywania ma być pokazywał.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFCAutoHideButton::Przenieś

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Parametry

[w] *nStawa*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFCAutoHideButton::ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

[w] *pNowyBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode

Wyłącz tryb automatycznego ukrywania.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Parametry

*pFirstBarInGroup (Grupa pFirstBarInGroup)*<br/>
[w] Wskaźnik do pierwszego paska w grupie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton

Podświetla przycisk automatycznego ukrywania.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bWyświetlenie*<br/>
Określa nowy stan przycisku automatycznego ukrywania. PRAWDA wskazuje, że przycisk jest podświetlony, FALSE wskazuje, że przycisk nie jest podświetlony.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFCAutoHideButton::IsHighlighted

Zwraca stan podświetlenia przycisku automatycznego ukrywania.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wyróżniony jest przycisk automatycznego ukrywania; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[Klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
