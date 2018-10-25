---
title: Klasa CMFCColorPopupMenu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bcb8a6781c9563f1017060dcfca64841a15f69
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079173"
---
# <a name="cmfccolorpopupmenu-class"></a>Klasa CMFCColorPopupMenu

Reprezentuje menu podręczne, które użytkownicy Użyj, aby wybrać kolory w dokumencie lub aplikacji.

## <a name="syntax"></a>Składnia

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Konstruuje `CMFCColorPopupMenu` obiektu.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Tworzy dokowalne odrywania pasek koloru. (Przesłania [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , jest osadzony w menu podręcznym. (Przesłania [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Ustawia obiekt formantu siatki właściwości Embedded `CMFCColorBar` obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`m_bEnabledInCustomizeMode`|Wartość logiczna określająca, czy ma być wyświetlana na pasku kolorów.|
|`m_wndColorBar`|`CMFCColorBar` Obiekt, który zapewnia wybór koloru.|

### <a name="remarks"></a>Uwagi

Ta klasa dziedziczy funkcje menu podręcznego `CMFCPopupMenu` klasy i zarządza nimi `CMFCColorBar` obiekt, który zapewnia wybór koloru. Gdy framework narzędzi jest w trybie dostosowywania i `m_bEnabledInCustomizeMode` element członkowski jest ustawiany na wartość FALSE, obiekt paska kolorów nie jest wyświetlany. Aby uzyskać więcej informacji na temat trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Aby uzyskać więcej informacji na temat `CMFCColorBar`, zobacz [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorpopupmenu.h

##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu

Konstruuje `CMFCColorPopupMenu` obiektu.

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
[in] Tablica kolorów wyświetlanych w menu podręcznym.

*Kolor*<br/>
[in] Kolor domyślnie wybrana.

*lpszAutoColor*<br/>
[in] Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne) lub wartość NULL.

Standardowa etykieta przycisku automatycznego **automatyczne**.

*lpszOtherColor*<br/>
[in] Etykieta tekstowa elementu *innych* przycisk wyświetlający więcej opcji koloru, lub wartość NULL.

Standardowa etykieta dla innych przycisku **więcej kolorów...** .

*lpszDocColors*<br/>
[in] Etykieta tekstowa przycisku kolory dokumentu. Paleta kolorów dokumentu zawiera listę kolorów używanych obecnie dokumentu.

*lstDocColors*<br/>
[in] Lista kolorów, które są obecnie używane.

*nColumns*<br/>
[in] Liczba kolumn, które zawiera tablicę kolorów.

*nHorzDockRows*<br/>
[in] Liczba wierszy, które ma pasek koloru, gdy jest zadokowany w poziomie.

*nVertDockColumns*<br/>
[in] Liczba kolumn, które ma pasek koloru, gdy jest zadokowany w pionie.

*colorAutomatic*<br/>
[in] Domyślny kolor struktura ma zastosowanie, gdy klikniesz przycisk Automatyczny.

*uiCommandID*<br/>
[in] Identyfikator polecenia sterowania paska kolorów.

*bStdColorDlg*<br/>
[in] Wartość logiczna wskazująca, czy mają być wyświetlane okno dialogowe kolorów standardowych systemowych lub [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe.

*pParentBtn*<br/>
[in] Wskaźnik do przycisku nadrzędnej.

*nID*<br/>
[in] Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Każdego przeciążonego konstruktora zestawy `m_bEnabledInCustomizeMode` elementu członkowskiego na wartość FALSE.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCColorPopupMenu` obiektu.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar

Tworzy dokowalne odrywania pasek koloru.

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
|*pWndMain*|[in] Wskaźnik do okna nadrzędnego z paskiem oderwania.|
|*uiID*|[in] Identyfikator polecenia paskiem oderwania.|
|*lpszName*|[in] Tekst okna paskiem oderwania.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego obiektu pasek sterowania odrywania.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu i rzutuje je na [klasa CPane](../../mfc/reference/cpane-class.md) wskaźnika. Można rzutować tę wartość do [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) wskaźnik przy użyciu jednej z makr rzutowania opisanego w [typu rzutowania z obiektów klas MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar

Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , jest osadzony w menu podręcznym.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do osadzonego `CMFCPopupMenuBar`.

### <a name="remarks"></a>Uwagi

Menu podręczne kolorów ma osadzony [klasa CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) obiektu. Przesłonić tę metodę w klasie pochodnej, jeśli aplikacja korzysta z innego typu osadzonego.

##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList

Ustawia obiekt formantu siatki właściwości Embedded `CMFCColorBar` obiektu.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

*pWndList*<br/>
[in] Wskaźnik do obiektu formantu siatki właściwości.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
