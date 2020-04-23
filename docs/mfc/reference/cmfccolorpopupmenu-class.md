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
ms.openlocfilehash: 901a44c8f5fdecd1b277ebdecc995722a3afe9a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752495"
---
# <a name="cmfccolorpopupmenu-class"></a>Klasa CMFCColorPopupMenu

Reprezentuje wyskakujące menu używane przez użytkowników do wybierania kolorów w dokumencie lub aplikacji.

## <a name="syntax"></a>Składnia

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Konstruuje `CMFCColorPopupMenu` obiekt.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Tworzy dokowany pasek kolorów odrywany. (Zastępuje [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Zwraca [CMFCPopupMenuBar,](../../mfc/reference/cmfcpopupmenubar-class.md) który jest osadzony wewnątrz menu podręcznego. (Zastępuje [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Ustawia obiekt kontrolny siatki właściwości `CMFCColorBar` osadzonego obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`m_bEnabledInCustomizeMode`|Wartość logiczna określająca, czy pasek kolorów ma być pokazywał.|
|`m_wndColorBar`|Obiekt, `CMFCColorBar` który zapewnia wybór kolorów.|

### <a name="remarks"></a>Uwagi

Ta klasa dziedziczy funkcję menu podręcznego `CMFCPopupMenu` klasy i `CMFCColorBar` zarządza obiektem, który zapewnia wybór kolorów. Gdy struktura paska narzędzi jest w `m_bEnabledInCustomizeMode` trybie dostosowywania, a element członkowski jest ustawiony na FAŁSZ, obiekt paska kolorów nie jest wyświetlany. Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Aby uzyskać `CMFCColorBar`więcej informacji na temat , zobacz [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd (CMiniFrameWnd)](../../mfc/reference/cminiframewnd-class.md)

[Cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorpopupmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu

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

*Kolory*<br/>
[w] Tablica kolorów wyświetlanych w menu podręcznym.

*color*<br/>
[w] Domyślny wybrany kolor.

*lpszautoColor*<br/>
[w] Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub NULL.

Standardową etykietą przycisku automatycznego jest **Automatyczna**.

*lpszOtherColor*<br/>
[w] Etykieta tekstowa *drugiego* przycisku, który wyświetla więcej opcji kolorów lub NULL.

Standardową etykietą dla drugiego przycisku jest **Więcej kolorów...**.

*lpszDocKolory*<br/>
[w] Etykieta tekstowa przycisku kolory dokumentu. Paleta kolorów dokumentu zawiera listę wszystkich kolorów używanych obecnie przez dokument.

*lstDocKolory*<br/>
[w] Lista kolorów aktualnie używanych przez dokument.

*nKolumny*<br/>
[w] Liczba kolumn, które ma tablica kolorów.

*nHorzDockRows*<br/>
[w] Liczba wierszy, które pasek kolorów ma, gdy jest zadokowany poziomo.

*nVertDockKolumny*<br/>
[w] Liczba kolumn, które pasek kolorów ma, gdy jest zadokowany w pionie.

*kolorAutomatyczny*<br/>
[w] Domyślny kolor, który stosuje się po kliknięciu przycisku automatycznego.

*identyfikator uiCommandID*<br/>
[w] Identyfikator polecenia sterowania paska kolorów.

*bStdColorDlg*<br/>
[w] Wartość logiczna wskazująca, czy ma być wyświetlane okno dialogowe standardowy kolor systemu, czy okno dialogowe [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md)

*pParentBtn*<br/>
[w] Wskaźnik do przycisku nadrzędnego.

*Nid*<br/>
[w] Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Każdy przeciążony konstruktor `m_bEnabledInCustomizeMode` ustawia element członkowski na FAŁSZ.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCColorPopupMenu` obiekt.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar

Tworzy dokowany pasek kolorów odrywany.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pWndMain (Niem.*|[w] Wskaźnik do okna nadrzędnego paska odrywać.|
|*Uiid*|[w] Identyfikator polecenia paska odrywu.|
|*Lpszname*|[w] Tekst okna paska odrywu.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego obiektu paska sterowania odrywać.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) obiektu i rzutuje go do wskaźnika [klasy CPane.](../../mfc/reference/cpane-class.md) Tę wartość można oddać z powrotem do wskaźnika [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) przy użyciu jednego z makr rzutowania opisanych w [polu Rzutowanie typu obiektów klasy MFC.](../../mfc/reference/type-casting-of-mfc-class-objects.md)

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar

Zwraca [CMFCPopupMenuBar,](../../mfc/reference/cmfcpopupmenubar-class.md) który jest osadzony wewnątrz menu podręcznego.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do osadzonego `CMFCPopupMenuBar`.

### <a name="remarks"></a>Uwagi

Kolorowe menu podręczne ma osadzony obiekt [CMFCPopupMenuBar Class.](../../mfc/reference/cmfcpopupmenubar-class.md) Zastąpuj tę metodę w klasie pochodnej, jeśli aplikacja używa innego typu osadzonego.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList

Ustawia obiekt kontrolny siatki właściwości `CMFCColorBar` osadzonego obiektu.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

*pWndList (Lista pWnd)*<br/>
[w] Wskaźnik do obiektu sterującego siatką właściwości.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
