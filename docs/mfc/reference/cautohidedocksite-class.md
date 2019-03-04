---
title: CAutoHideDockSite Class
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
ms.openlocfilehash: f24827e2dc1f4d1131f5b63aebeb0e2b09bc2281
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302965"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite Class

`CAutoHideDockSite` Rozszerza [klasa CDockSite](../../mfc/reference/cdocksite-class.md) do wdrożenia automatycznie ukrywanego zadokowanego okienka.

## <a name="syntax"></a>Składnia

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::CAutoHideDockSite`|Konstruuje `CAutoHideDockSite` obiektu.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Wskazuje, czy `CAutoHideDockSite` jest wyświetlany w menu okienka.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Określa, czy obiekt podstawowy okienko jest tworzony na podstawie [klasa CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockSite::DockPane](#dockpane)|Stacje dokujące okienko tej `CAuotHideDockSite` obiektu.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Pobiera informacje o rozmiarze witryny dokowania we współrzędnych ekranu.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Ponownie rysuje zawartość okienka na `CAutoHideDockSite` z globalnego marginesy i odstęp.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Ustawia margines po lewej stronie pasek dokowania.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Ustawia margines po prawej stronie paska dokowania.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Wywołania [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów `CAutoHideDockSite`.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Określa rozmiar odstęp między paski narzędzi i krawędzi pasek dokowania. Ta przestrzeń jest mierzony od lewej krawędzi lub górnej krawędzi, w zależności od tego, wyrównanie miejsce dokowania.|

## <a name="remarks"></a>Uwagi

Gdy wywołujesz [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), szablon automatycznie tworzy `CAutoHideDockSite` obiektu. W większości przypadków nie trzeba utworzyć wystąpienia lub używać tej klasy bezpośrednio.

Pasek dokowania jest lukę między po lewej stronie okienka dokowania, a po lewej stronie [klasa CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać `CAutoHideDockSite` obiektu z `CMFCAutoHideBar` obiektu i jak ustawić marginesy lewy i Prawy pasek dokowania.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxautohidedocksite.h

##  <a name="canacceptpane"></a>  CAutoHideDockSite::CanAcceptPane

Określa, czy jest podstawowy okienko [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiektu lub pochodzić od `CMFCAutoHideBar`.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pBar*|[in] Okienko podstawowa struktura testów.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *pBar* jest tworzony na podstawie `CMFCAutoHideBar`; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli obiekt podstawowy okienko jest tworzony na podstawie `CMFCAutoHideBar`, może on zawierać `CAutoHideDockSite`.

##  <a name="dockpane"></a>  CAutoHideDockSite::DockPane

Stacje dokujące okienko tej [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) obiektu.

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
|*pWnd*|[in] Okienko w którym dokowane platformę.|
|*dockMethod*|[in] Dokowanie opcje okienka.|
|*lpRect*|[in] Prostokąt, który określa granice zadokowanego okienka.|

### <a name="remarks"></a>Uwagi

Domyślna implementacja parametr nie *dockMethod*, które jest dostarczane do użytku w przyszłości.

Jeśli *lprect —* ma wartość NULL, struktura umieszcza okienka w lokalizacji domyślnej na witryny dokowania. Jeśli witryny dokowania jest poziomy, domyślna lokalizacja to lewej strony witryny dokowania. W przeciwnym razie domyślna lokalizacja to w górnej części witryny dokowania.

##  <a name="getalignrect"></a>  CAutoHideDockSite::GetAlignRect

Pobiera informacje o rozmiarze witryny dokowania we współrzędnych ekranu.

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Rect*|[in] Odwołanie do prostokąta. Metoda przechowuje rozmiar witryny dokowania w prostokąta.|

### <a name="remarks"></a>Uwagi

Prostokąt jest ustawione marginesy przesunięcia, tak, aby nie są uwzględniane.

##  <a name="m_nextraspace"></a>  CAutoHideDockSite::m_nExtraSpace

Rozmiar odstęp między krawędziami [klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i [klasa CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiektów.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Uwagi

Gdy `CMFCAutoHideBar` jest zadokowany w `CAutoHideDockSite`, nie będzie zajmować witryny całego dokowania. Ta zmienna globalna Określa dodatkowy odstęp między lewą lub górną krawędzią elementu `CMFCAutoHideBar` i odpowiedni `CAutoHideDockSite` krawędzi. Czy jest używany górnej lub lewej krawędzi zależy od bieżącego wyrównania.

##  <a name="setoffsetleft"></a>  CAutoHideDockSite::SetOffsetLeft

Ustawia margines po lewej stronie pasek dokowania.

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
[in] Przesunięcie nowe.

### <a name="remarks"></a>Uwagi

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są pozycjonowane statycznie na `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik ręcznie nie można zmienić lokalizację `CMFCAutoHideBar` obiektów. `SetOffsetLeft` Metody Określa odstępy między po lewej stronie skrajnej lewej `CMFCAutoHideBar` i po lewej stronie `CAutoHideDockSite`.

##  <a name="setoffsetright"></a>  CAutoHideDockSite::SetOffsetRight

Ustawia margines po prawej stronie paska dokowania.

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
[in] Przesunięcie nowe.

### <a name="remarks"></a>Uwagi

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są pozycjonowane statycznie na `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik ręcznie nie można zmienić lokalizację `CMFCAutoHideBar` obiektów. `SetOffsetRight` Metody Określa odstępy między po prawej stronie najdalej z prawej strony `CMFCAutoHideBar` i po prawej stronie `CAutoHideDockSite`.

##  <a name="repositionpanes"></a>  CAutoHideDockSite::RepositionPanes

Odrysowuje okienka na [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*rectNewClientArea*|[in] Zastrzeżonej wartości.|

### <a name="remarks"></a>Uwagi

Domyślna implementacja używa *rectNewClientArea*. Jego odrysowuje okienek z marginesy paska narzędzi globalne i odstępy przycisku.

##  <a name="unsetautohidemode"></a>  CAutoHideDockSite::UnSetAutoHideMode

Wywołania [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów witryny dokowania.

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pAutoHideToolbar*|[in] Wskaźnik do [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) okienko obiektów znajdujących się na `CAutoHideDockSite`.|

### <a name="remarks"></a>Uwagi

Metoda ta wyszukuje dla wiersza, który zawiera *pAutoHideToolbar*. Wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` dla wszystkich `CMFCAutoHideBar` obiektów w tym wierszu. Jeśli *pAutoHideToolbar* nie można odnaleźć lub ma wartość NULL, ta metoda wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` dla wszystkich `CMFCAutoHideBar` obiektów na `CAutoHideDockSite`.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockSite](../../mfc/reference/cdocksite-class.md)
