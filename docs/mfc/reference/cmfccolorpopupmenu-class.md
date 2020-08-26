---
title: Klasa CMFCColorPopupMenu
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: 2964f250b25ad6c77c70e8f10cd92cca0c7d11da
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844564"
---
# <a name="cmfccolorpopupmenu-class"></a>Klasa CMFCColorPopupMenu

Reprezentuje menu podręczne, którego użytkownicy używają do wybierania kolorów w dokumencie lub aplikacji.

## <a name="syntax"></a>Składnia

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Konstruuje `CMFCColorPopupMenu` obiekt.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Tworzy pasek koloru odrywania było dokować. (Przesłania [CMFCPopupMenu:: CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu:: getmenubar](#getmenubar)|Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) osadzony w menu podręcznym. (Przesłania [CMFCPopupMenu:: getmenubar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)).|
|`CMFCColorPopupMenu::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Ustawia obiekt kontrolny siatki właściwości obiektu osadzonego `CMFCColorBar` .|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|`m_bEnabledInCustomizeMode`|Wartość logiczna określająca, czy ma być pokazywany pasek koloru.|
|`m_wndColorBar`|`CMFCColorBar`Obiekt, który zapewnia wybór koloru.|

### <a name="remarks"></a>Uwagi

Ta klasa dziedziczy funkcje menu podręcznego `CMFCPopupMenu` klasy i zarządza `CMFCColorBar` obiektem, który zapewnia wybór koloru. Gdy struktura paska narzędzi jest w trybie dostosowywania, a `m_bEnabledInCustomizeMode` element członkowski ma wartość FAŁSZ, obiekt paska koloru nie jest pokazywany. Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar:: Isdostosowywaniemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Aby uzyskać więcej informacji na temat `CMFCColorBar` , zobacz [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorpopupmenu. h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a> CMFCColorPopupMenu::CMFCColorPopupMenu

Konstruuje `CMFCColorPopupMenu` obiekt.

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*świat*<br/>
podczas Tablica kolorów, które są wyświetlane w strukturze w menu podręcznym.

*Kolor*<br/>
podczas Domyślny wybrany kolor.

*lpszAutoColor*<br/>
podczas Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub wartość null.

Standardowa etykieta przycisku automatycznego jest **Automatyczna**.

*lpszOtherColor*<br/>
podczas Etykieta tekstowa *drugiego* przycisku, która wyświetla więcej opcji kolorów lub wartość null.

Standardowa etykieta dla drugiego przycisku ma **więcej kolorów..**.

*lpszDocColors*<br/>
podczas Etykieta tekstowa przycisku kolory dokumentu. W palecie kolory dokumentu są wyświetlane wszystkie kolory, których aktualnie używa dokument.

*lstDocColors*<br/>
podczas Lista kolorów używanych obecnie przez dokument.

*nColumns*<br/>
podczas Liczba kolumn, które ma Tablica kolorów.

*nHorzDockRows*<br/>
podczas Liczba wierszy, po których pasek koloru jest zadokowany w poziomie.

*nVertDockColumns*<br/>
podczas Liczba kolumn, które znajdują się na pasku kolorów, gdy jest zadokowany w pionie.

*colorAutomatic*<br/>
podczas Domyślny kolor stosowany przez platformę po kliknięciu przycisku automatyczne.

*uiCommandID*<br/>
podczas Identyfikator polecenia kontrolki paska kolorów.

*bStdColorDlg*<br/>
podczas Wartość logiczna wskazująca, czy ma być wyświetlane okno dialogowe standardowy kolor systemu czy okno dialogowe [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) .

*pParentBtn*<br/>
podczas Wskaźnik do przycisku nadrzędnego.

*nID*<br/>
podczas Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Każdy przeciążony Konstruktor ustawia `m_bEnabledInCustomizeMode` element członkowski na wartość false.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCColorPopupMenu` obiektu.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a> CMFCColorPopupMenu::CreateTearOffBar

Tworzy pasek koloru odrywania było dokować.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*pWndMain*\
podczas Wskaźnik do okna nadrzędnego paska odrywania.

*uiID*\
podczas Identyfikator polecenia paska odrywania.

*lpszName*\
podczas Tekst okna paska odrywania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego obiektu paska kontroli odrywania.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy obiekt [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) i rzutuje go na wskaźnik [klasy CPane](../../mfc/reference/cpane-class.md) . Można rzutować tę wartość z powrotem na wskaźnik [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) przy użyciu jednego z makr rzutowania opisanych w obszarze [rzutowania obiektów klas MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a> CMFCColorPopupMenu:: getmenubar

Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) osadzony w menu podręcznym.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do osadzonej `CMFCPopupMenuBar` .

### <a name="remarks"></a>Uwagi

Menu rozwijane kolor zawiera osadzony obiekt [klasy CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) . Zastąp tę metodę w klasie pochodnej, jeśli aplikacja używa innego typu osadzonego.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a> CMFCColorPopupMenu::SetPropList

Ustawia obiekt kontrolny siatki właściwości obiektu osadzonego `CMFCColorBar` .

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

*pWndList*<br/>
podczas Wskaźnik do obiektu kontrolki siatki właściwości.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
