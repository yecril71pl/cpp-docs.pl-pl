---
title: CMFCDropDownFrame Class
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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284752"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame Class

Oferuje funkcje okna ramki listy rozwijanej paski narzędzi z listy rozwijanej i przycisków na pasku narzędzi listy rozwijanej.

## <a name="syntax"></a>Składnia

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Domyślny konstruktor.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDropDownFrame::Create](#create)|Tworzy `CMFCDropDownFrame` obiektu.|
|`CMFCDropDownFrame::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Pobiera na pasku menu nadrzędnej ramki listy rozwijanej.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Pobiera menu podręcznego nadrzędnej ramki listy rozwijanej.|
|`CMFCDropDownFrame::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Powoduje przeniesienie ramkę z listy rozwijanej.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Określa, czy okno podrzędne rozwijany pasek narzędzi jest niszczony, automatycznie.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.

Struktura korzysta z tej klasy zapewniające ramki do `CMFCDropDownToolbar` i `CMFCDropDownToolbarButton` klasy. Aby uzyskać więcej informacji na temat tych klas, zobacz [klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) i [klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać wskaźnika do `CMFCDropDownFrame` obiektu z `CFrameWnd` klasy i jak ustawić element podrzędny rozwijany pasek narzędzi okna mają zostać zniszczone automatycznie.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar.h

##  <a name="create"></a>  CMFCDropDownFrame::Create

Tworzy `CMFCDropDownFrame` obiektu.

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
|*pWndParent*|[in] Okno nadrzędne ramki listy rozwijanej.|
|*x*|[in] Współrzędna pozioma ekranu dla lokalizacji ramki w dół w dół.|
|*y*|[in] Współrzędna pionowa ekranu dla lokalizacji ramki w dół w dół.|
|*pWndOriginToolbar*|[in] Pasek narzędzi, który zawiera przyciski listy rozwijanej, korzystającą z tej metody w celu wypełnienia nowy obiekt w ramce listy rozwijanej.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ramka listy rozwijanej został pomyślnie utworzony; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje base [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metodę, aby utworzyć okno ramowe listy rozwijanej ze stylem WS_POPUP. Okno ramowe listy rozwijanej pojawia się na współrzędnych ekranu. Ta metoda kończy się niepowodzeniem, jeśli [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metoda zwraca wartość FALSE.

`CMFCDropDownFrame` Klasy jest tworzona kopia udostępnionych `CMFCDropDownToolBar` parametru. Ta metoda kopiuje obrazy przycisków i Stany przycisku z `pWndOriginToolbar` parametr `m_pWndOriginToolbar` element członkowski danych.

##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar

Pobiera na pasku menu nadrzędnej ramki listy rozwijanej.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na pasku menu nadrzędnej ramki listy rozwijanej, lub wartość NULL, jeśli ramka nie ma obiektu nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera nadrzędny paska menu przy użyciu przycisku nadrzędnej. Ta metoda zwraca wartość NULL, jeśli ramkę z listy rozwijanej ma przycisk nie nadrzędnej lub przycisk nadrzędny ma nadrzędny paska menu.

##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu

Pobiera menu podręcznego nadrzędnej ramki listy rozwijanej.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do menu rozwijanego nadrzędnej ramki listy rozwijanej, lub wartość NULL, jeśli ramka nie ma obiektu nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera menu nadrzędnej przy użyciu przycisku nadrzędnej. Ta metoda zwraca wartość NULL, jeśli ramkę z listy rozwijanej ma przycisk nie nadrzędnej lub przycisk nadrzędny ma menu nie nadrzędnej.

##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout

Powoduje przeniesienie ramkę z listy rozwijanej.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bNotify*|[in] Nieużywane.|

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, po utworzeniu ramki listy rozwijanej lub ze zmienionym rozmiarem okna nadrzędnego. Ta metoda oblicza położenie i rozmiar ramki listy rozwijanej położenie i rozmiar okna nadrzędnego.

##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy

Określa, czy okno podrzędne rozwijany pasek narzędzi jest niszczony, automatycznie.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[in] Wartość TRUE, aby automatycznie zniszczyć skojarzone rozwijany pasek narzędzi okna; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *bAutoDestroy* ma wartość PRAWDA, a następnie `CMFCDropDownFrame` destruktor niszczy okno skojarzone rozwijany pasek narzędzi. Wartość domyślna to TRUE.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
