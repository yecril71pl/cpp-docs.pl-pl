---
title: Klasa CMFCDropDownFrame
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869067"
---
# <a name="cmfcdropdownframe-class"></a>Klasa CMFCDropDownFrame

Udostępnia funkcje okna rozwijanego ramki w rozwijane paski narzędzi i rozwijane przyciski paska narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Konstruktor domyślny.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDropDownFrame:: Create](#create)|Tworzy obiekt `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Pobiera nadrzędny pasek menu ramki rozwijanej.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Pobiera nadrzędne menu wyskakujące ramki rozwijanej.|
|`CMFCDropDownFrame::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Zmienia położenie ramki rozwijanej.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Określa, czy podrzędne okno listy rozwijanej jest niszczone automatycznie.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.

Struktura używa tej klasy w celu zapewnienia zachowania ramki dla klas `CMFCDropDownToolbar` i `CMFCDropDownToolbarButton`. Aby uzyskać więcej informacji na temat tych klas, zobacz Klasa [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) i [Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak pobrać wskaźnik do obiektu `CMFCDropDownFrame` z klasy `CFrameWnd` i jak ustawić okno rozwijane podrzędnego okna podręcznego.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar. h

##  <a name="create"></a>CMFCDropDownFrame:: Create

Tworzy obiekt `CMFCDropDownFrame`.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pWndParent*|podczas Okno nadrzędne ramki listy rozwijanej.|
|*y*|podczas Pozioma Współrzędna ekranu dla położenia ramki w dół.|
|*t*|podczas Współrzędne ekranu pionowego dla lokalizacji ramki w dół.|
|*pWndOriginToolbar*|podczas Pasek narzędzi, który zawiera przyciski rozwijane używane przez tę metodę do wypełniania nowego obiektu ramki listy rozwijanej.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ramka listy rozwijanej została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje podstawową metodę [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) , aby utworzyć okno ramki rozwijanej z stylem WS_POPUP. Okno z ramką rozwijaną pojawia się na określonych współrzędnych ekranu. Ta metoda kończy się niepowodzeniem, jeśli metoda [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) zwróci wartość false.

Klasa `CMFCDropDownFrame` tworzy kopię podanego parametru `CMFCDropDownToolBar`. Ta metoda kopiuje obrazy przycisków i Stany przycisków z `pWndOriginToolbar` parametru do `m_pWndOriginToolbar` elementu członkowskiego danych.

##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Pobiera nadrzędny pasek menu ramki rozwijanej.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nadrzędnego paska menu rozwijanej ramki lub wartość NULL, jeśli ramka nie ma elementu nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera nadrzędny pasek menu z przycisku nadrzędnego. Ta metoda zwraca wartość NULL, jeśli nie ma przycisku nadrzędnego lub przycisk nadrzędny nie ma nadrzędnego paska menu.

##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Pobiera nadrzędne menu wyskakujące ramki rozwijanej.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nadrzędnego menu rozwijanego ramki rozwijanej lub wartość NULL, jeśli ramka nie ma elementu nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera menu nadrzędne z przycisku nadrzędnego. Ta metoda zwraca wartość NULL, jeśli nie ma przycisku nadrzędnego lub przycisk nadrzędny nie ma menu nadrzędnego.

##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Zmienia położenie ramki rozwijanej.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bNotify*|podczas Przestrzeń.|

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę po utworzeniu ramki rozwijanej lub zmianie rozmiaru okna nadrzędnego. Ta metoda oblicza położenie i rozmiar ramki rozwijanej przy użyciu pozycji i rozmiaru okna nadrzędnego.

##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Określa, czy podrzędne okno listy rozwijanej jest niszczone automatycznie.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
podczas TRUE, aby automatycznie zniszczyć skojarzone okno rozwijane paska narzędzi. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *bAutoDestroy* ma wartość true, destruktor `CMFCDropDownFrame` niszczy skojarzone okno paska narzędzi listy rozwijanej. Wartość domyślna to TRUE.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
