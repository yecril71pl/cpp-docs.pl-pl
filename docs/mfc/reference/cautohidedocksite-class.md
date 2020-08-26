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
ms.openlocfilehash: 14db8d93ea7706b3a4daad2ba751f8410974f6cb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841639"
---
# <a name="cautohidedocksite-class"></a>Klasa CAutoHideDockSite

`CAutoHideDockSite`Rozszerza [klasę CDockSite](../../mfc/reference/cdocksite-class.md) , aby zaimplementować Autoukrywanie okienek dokowania.

## <a name="syntax"></a>Składnia

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa | Opis |
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::CAutoHideDockSite`|Konstruuje `CAutoHideDockSite` obiekt.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

| Nazwa | Opis |
|-|-|
|Nazwa|Opis|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Wskazuje, czy `CAutoHideDockSite` jest wyświetlany w menu okienka.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Określa, czy obiekt okienka podstawowego jest pochodną [klasy CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockSite::D ockPane](#dockpane)|Dokowanie okienka do tego `CAuotHideDockSite` obiektu.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Pobiera rozmiar witryny Docker we współrzędnych ekranu.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Ponownie rysuje okienko przy `CAutoHideDockSite` użyciu marginesów globalnych i odstępów między przyciskami.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Ustawia margines po lewej stronie paska dokowania.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Ustawia margines po prawej stronie paska dokowania.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Wywołuje [CMFCAutoHideBar:: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów w `CAutoHideDockSite` .|

### <a name="data-members"></a>Elementy członkowskie danych

| Nazwa | Opis |
|-|-|
|Nazwa|Opis|
|[CAutoHideDockSite:: m_nExtraSpace](#m_nextraspace)|Określa rozmiar przestrzeni między paskami narzędzi i krawędzią paska dokowania. To miejsce jest mierzone od lewej krawędzi lub górnej krawędzi, w zależności od wyrównania dla obszaru dokowania.|

## <a name="remarks"></a>Uwagi

Gdy wywołasz [CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), struktura automatycznie tworzy `CAutoHideDockSite` obiekt. W większości przypadków nie trzeba tworzyć wystąpienia ani używać tej klasy bezpośrednio.

Pasek dokowania to przerwy między lewą krawędzią okienka Dock i lewej strony [klasy CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać `CAutoHideDockSite` obiekt z `CMFCAutoHideBar` obiektu i jak ustawić lewy i prawy margines paska dokowania.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxautohidedocksite. h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a> CAutoHideDockSite::CanAcceptPane

Określa, czy okienko podstawowe jest obiektem [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) , czy też pochodzi od elementu `CMFCAutoHideBar` .

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

*pBar*\
podczas Okienko podstawowe, które testuje struktura.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *pBar* jest pochodną `CMFCAutoHideBar` ; W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli obiektem podstawowym okienka jest pochodzący z `CMFCAutoHideBar` , może on zawierać `CAutoHideDockSite` .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a> CAutoHideDockSite::D ockPane

Dokowanie okienka do tego obiektu [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) .

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Okienko, które jest zadokowane przez platformę.

*dockMethod*\
podczas Opcje dokowania okienka.

*lpRect*\
podczas Prostokąt, który określa granice okienka zadokowanego.

### <a name="remarks"></a>Uwagi

Implementacja domyślna nie używa parametru *dockMethod*, który jest przeznaczony do użytku w przyszłości.

Jeśli *lpRect* ma wartość null, struktura umieszcza okienko w domyślnej lokalizacji w witrynie Docker. Jeśli witryna Dock jest w poziomie, domyślna lokalizacja znajduje się z lewej strony witryny Docker. W przeciwnym razie lokalizacja domyślna znajduje się w górnej części witryny Docker.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a> CAutoHideDockSite::GetAlignRect

Pobiera rozmiar witryny Docker we współrzędnych ekranu.

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*cinania*\
podczas Odwołanie do prostokąta. Metoda przechowuje rozmiar witryny Docker w tym prostokącie.

### <a name="remarks"></a>Uwagi

Prostokąt jest dostosowywany do marginesów przesunięcia, dzięki czemu nie są one uwzględniane.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a> CAutoHideDockSite:: m_nExtraSpace

Rozmiar przestrzeni między krawędziami [klasy CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i obiektów [klasy CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) .

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Uwagi

Gdy obiekt `CMFCAutoHideBar` jest zadokowany `CAutoHideDockSite` , nie powinien zajmować całej witryny Docker. Ta zmienna globalna kontroluje dodatkowe miejsce między lewą lub górną krawędzią `CMFCAutoHideBar` i odpowiednią `CAutoHideDockSite` krawędzią. Czy jest używana Górna lub lewa krawędź zależy od bieżącego wyrównania.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a> CAutoHideDockSite::SetOffsetLeft

Ustawia margines po lewej stronie paska dokowania.

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
podczas Nowe przesunięcie.

### <a name="remarks"></a>Uwagi

Obiekty [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) są pozycjonowane statycznie względem `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik nie może ręcznie zmienić lokalizacji `CMFCAutoHideBar` obiektów. `SetOffsetLeft`Metoda kontroluje odstępy między lewą krawędzią lewej strony `CMFCAutoHideBar` a lewej strony `CAutoHideDockSite` .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a> CAutoHideDockSite::SetOffsetRight

Ustawia margines po prawej stronie paska dokowania.

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
podczas Nowe przesunięcie.

### <a name="remarks"></a>Uwagi

Obiekty [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) są pozycjonowane statycznie względem `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik nie może ręcznie zmienić lokalizacji `CMFCAutoHideBar` obiektów. `SetOffsetRight`Metoda kontroluje odstępy między prawą krawędzią a prawej strony `CMFCAutoHideBar` `CAutoHideDockSite` .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a> CAutoHideDockSite::RepositionPanes

Ponownie rysuje okienka w [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

*rectNewClientArea*\
podczas Wartość zastrzeżona.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie używa *rectNewClientArea*. Ponownie rysuje okienka przy użyciu globalnych marginesów paska narzędzi i odstępów przycisku.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a> CAutoHideDockSite::UnSetAutoHideMode

Wywołuje [CMFCAutoHideBar:: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów w witrynie Docker.

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parametry

*pAutoHideToolbar*\
podczas Wskaźnik do okienka obiektu [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) znajdującego się w `CAutoHideDockSite` .

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje wiersz zawierający *pAutoHideToolbar*. Wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` wszystkie `CMFCAutoHideBar` obiekty w tym wierszu. Jeśli *pAutoHideToolbar* nie została znaleziona lub ma wartość null, ta metoda wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` wszystkie `CMFCAutoHideBar` obiekty w `CAutoHideDockSite` .

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockSite](../../mfc/reference/cdocksite-class.md)
