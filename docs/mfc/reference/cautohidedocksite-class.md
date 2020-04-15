---
title: Klasa CAutoHideDockSite
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 3a4593ac17f0af26517144edb7b01a9ca4203b1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352980"
---
# <a name="cautohidedocksite-class"></a>Klasa CAutoHideDockSite

Rozszerza `CAutoHideDockSite` [CDockSite Klasy](../../mfc/reference/cdocksite-class.md) do zaimplementowania automatycznego ukrywania okienek dokowania.

## <a name="syntax"></a>Składnia

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::CAutoHideDockSite`|Konstruuje `CAutoHideDockSite` obiekt.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Wskazuje, `CAutoHideDockSite` czy jest wyświetlany w menu okienka.|
|[CAutoHideDockWitastęp::CanAcceptPane](#canacceptpane)|Określa, czy obiekt okienka podstawowego jest pochodną [klasy CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockWitasz::DockPane](#dockpane)|Dokuje okienko `CAuotHideDockSite` do tego obiektu.|
|[CAutoHideDockWitasz::GetAlignRect](#getalignrect)|Pobiera rozmiar lokacji stacji dokującej we współrzędnych ekranu.|
|[CAutoHideDockWitite::RepositionPanes](#repositionpanes)|Ponownie rysuje okienko `CAutoHideDockSite` z marginesami globalnymi i odstępami między przyciskami.|
|[CAutoHideDockWitastęp::SetOffsetLeft](#setoffsetleft)|Ustawia margines po lewej stronie paska dokowania.|
|[CAutoHideDockWitatka::SetOffsetRight](#setoffsetright)|Ustawia margines po prawej stronie paska dokowania.|
|[CAutoHideDockWitasz::UnSetAutoHideMode](#unsetautohidemode)|Wywołuje [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla `CAutoHideDockSite`obiektów w .|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|[CAutoHideDockWitatka::m_nExtraSpace](#m_nextraspace)|Określa rozmiar spacji między paskami narzędzi a krawędzią paska dokowania. Ta przestrzeń jest mierzona od lewej krawędzi lub górnej krawędzi, w zależności od wyrównania miejsca w stacji dokującej.|

## <a name="remarks"></a>Uwagi

Po wywołaniu [CFrameWndEx::EnableAutoHidePanes,](../../mfc/reference/cframewndex-class.md#enableautohidepanes)struktura automatycznie `CAutoHideDockSite` tworzy obiekt. W większości przypadków nie należy mieć do wystąpienia lub używać tej klasy bezpośrednio.

Pasek dokowania jest odstęp między lewą stroną okienka dokowania i po lewej stronie [CMFCAutoHideButton Klasy](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[CdockSite (cdocksite)](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CAutoHideDockSite` jak `CMFCAutoHideBar` pobrać obiekt z obiektu i jak ustawić lewy i prawy margines paska dokowania.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDockWitastęp::CanAcceptPane

Określa, czy okienko bazowe jest obiektem [CMFCAutoHideBar,](../../mfc/reference/cmfcautohidebar-class.md) czy też pochodzi od pliku `CMFCAutoHideBar`.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pBar*|[w] Okienko podstawowe, które testuje framework.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *pBar* `CMFCAutoHideBar`pochodzi od ; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Jeśli obiekt okienka podstawowego `CMFCAutoHideBar`pochodzi od obiektu `CAutoHideDockSite`, może on zawierać plik .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDockWitasz::DockPane

Dokuje okienko do tego obiektu [CAutoHideDockSite.](../../mfc/reference/cautohidedocksite-class.md)

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pwnd*|[w] Okienko, do które dokuje framework.|
|*dokMetoda*|[w] Opcje dokowania okienka.|
|*Lprect*|[w] Prostokąt określający granice zadokowanego okienka.|

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie używa parametru *dockMethod*, który jest przewidziany do wykorzystania w przyszłości.

Jeśli *lpRect* jest NULL, struktura umieszcza okienko w domyślnej lokalizacji w lokacji dokowania. Jeśli lokacja stacji dokującej jest pozioma, domyślna lokalizacja znajduje się po lewej stronie lokacji stacji dokującej. W przeciwnym razie domyślna lokalizacja znajduje się w górnej części lokacji dokującej.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDockWitasz::GetAlignRect

Pobiera rozmiar lokacji stacji dokującej we współrzędnych ekranu.

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Rect*|[w] Odwołanie do prostokąta. Metoda przechowuje rozmiar lokacji dokowania w tym prostokącie.|

### <a name="remarks"></a>Uwagi

Prostokąt jest korygowany dla marginesów odsunięcia, tak aby nie zostały uwzględnione.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDockWitatka::m_nExtraSpace

Rozmiar odstępu między krawędziami [CAutoHideDockSite klasy](../../mfc/reference/cautohidedocksite-class.md) i [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md) obiektów.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Uwagi

Gdy `CMFCAutoHideBar` a jest zadokowany w `CAutoHideDockSite`, nie powinien zajmować całe miejsce dokowania. Ta zmienna globalna steruje dodatkową przestrzenią `CMFCAutoHideBar` między `CAutoHideDockSite` lewą lub górną krawędzią i odpowiednią krawędzią. To, czy używana jest górna czy lewa krawędź, zależy od bieżącego wyrównania.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDockWitastęp::SetOffsetLeft

Ustawia margines po lewej stronie paska dokowania.

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parametry

*nStawa*<br/>
[w] Nowe przesunięcie.

### <a name="remarks"></a>Uwagi

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są umieszczone statycznie na `CAutoHideDockSite` obiekcie. Oznacza to, że użytkownik nie może `CMFCAutoHideBar` ręcznie zmienić lokalizacji obiektów. Metoda `SetOffsetLeft` steruje odstępami między lewą stroną `CMFCAutoHideBar` lewej i lewej `CAutoHideDockSite`strony .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDockWitatka::SetOffsetRight

Ustawia margines po prawej stronie paska dokowania.

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parametry

*nStawa*<br/>
[w] Nowe przesunięcie.

### <a name="remarks"></a>Uwagi

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są umieszczone statycznie na `CAutoHideDockSite` obiekcie. Oznacza to, że użytkownik nie może `CMFCAutoHideBar` ręcznie zmienić lokalizacji obiektów. Metoda `SetOffsetRight` steruje odstępami między prawą stroną `CMFCAutoHideBar` prawej i prawej `CAutoHideDockSite`strony .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDockWitite::RepositionPanes

Ponownie rysuje okienka na [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*reectNewClientArea*|[w] Wartość zarezerwowana.|

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie używa *rectNewClientArea*. Ponownie rysuje okienka z globalnymi marginesami paska narzędzi i odstępami między przyciskami.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDockWitasz::UnSetAutoHideMode

Wywołuje [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów w witrynie dokowania.

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pAutoHideToolbar*|[w] Wskaźnik do okienka obiektu [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) `CAutoHideDockSite`znajdującego się na pliku .|

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje wiersz zawierający *pAutoHideToolbar*. Wymaga `CMFCAutoHideBar.UnSetAutoHideMode` wszystkich obiektów `CMFCAutoHideBar` w tym wierszu. Jeśli *pAutoHideToolbar* nie zostanie znaleziony lub jest `CMFCAutoHideBar.UnSetAutoHideMode` null, `CMFCAutoHideBar` ta `CAutoHideDockSite`metoda wywołuje dla wszystkich obiektów na .

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockSite](../../mfc/reference/cdocksite-class.md)
