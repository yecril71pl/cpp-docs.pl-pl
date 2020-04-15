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
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367552"
---
# <a name="cmfcdropdownframe-class"></a>Klasa CMFCDropDownFrame

Funkcje okna rozwijanej ramki do rozwijanych pasków narzędzi i przycisków rozwijanych paska narzędzi.

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
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDropDownFrame::Utwórz](#create)|Tworzy obiekt `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Pobiera pasek menu nadrzędnego ramki rozwijanej.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Pobiera nadrzędne menu podręczne ramki rozwijanej.|
|`CMFCDropDownFrame::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Zmienia położenie ramki rozwijanej.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Określa, czy okno rozwijane podrzędne jest niszczone automatycznie.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio z kodu.

Struktura używa tej klasy, aby zapewnić `CMFCDropDownToolbar` `CMFCDropDownToolbarButton` zachowanie ramki do i klas. Aby uzyskać więcej informacji na temat tych klas, zobacz [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) i [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCDropDownFrame` pobrać wskaźnik `CFrameWnd` do obiektu z klasy i jak ustawić okno rozwijane podrzędne, które ma zostać automatycznie zniszczone.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd (CMiniFrameWnd)](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame (CMFCDropDownFrame)](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Utwórz

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
|*pWndRodziciela*|[w] Okno nadrzędne ramki rozwijanej.|
|*X*|[w] Współrzędna ekranu poziomego dla położenia ramki w dół.|
|*Y*|[w] Pionowa współrzędna ekranu dla położenia ramki w dół.|
|*pWndOriginToolbar*|[w] Pasek narzędzi zawierający przyciski rozwijane używane przez tę metodę do wypełniania nowego obiektu ramki rozwijanej.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ramka rozwijana została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje podstawową metodę [CMiniFrameWnd::CreateEx,](../../mfc/reference/cminiframewnd-class.md#createex) aby utworzyć okno ramki rozwijanej ze stylem WS_POPUP. Okno rozwijanej ramki pojawi się na określonych współrzędnych ekranu. Ta metoda kończy się niepowodzeniem, jeśli [metoda CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) zwraca wartość FAŁSZ.

Klasa `CMFCDropDownFrame` tworzy kopię dostarczonego `CMFCDropDownToolBar` parametru. Ta metoda kopiuje obrazy przycisków `pWndOriginToolbar` i `m_pWndOriginToolbar` stany przycisków z parametru do elementu członkowskiego danych.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Pobiera pasek menu nadrzędnego ramki rozwijanej.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do paska menu nadrzędnego ramki rozwijanej lub NULL, jeśli ramka nie ma nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera pasek menu nadrzędnego z przycisku nadrzędnego. Ta metoda zwraca wartość NULL, jeśli ramka rozwijana nie ma przycisku nadrzędnego lub przycisk nadrzędny nie ma paska menu nadrzędnego.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Pobiera nadrzędne menu podręczne ramki rozwijanej.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nadrzędnego menu rozwijanego ramki rozwijanej lub NULL, jeśli ramka nie ma nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera menu nadrzędnego z przycisku nadrzędnego. Ta metoda zwraca wartość NULL, jeśli ramka rozwijana nie ma przycisku nadrzędnego lub przycisk nadrzędny nie ma menu nadrzędnego.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Zmienia położenie ramki rozwijanej.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bNotuj*|[w] Nieużywane.|

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tworzona jest ramka rozwijana lub rozmiar okna nadrzędnego. Ta metoda oblicza położenie i rozmiar ramki rozwijanej przy użyciu położenia i rozmiaru okna nadrzędnego.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Określa, czy okno rozwijane podrzędne jest niszczone automatycznie.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroj*<br/>
[w] PRAWDA, aby automatycznie zniszczyć skojarzone okno rozwijane paska narzędzi; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *bAutoDestroy* ma wartość `CMFCDropDownFrame` TRUE, destruktor niszczy skojarzone okno paska narzędzi rozwijanych. Wartością domyślną jest PRAWDA.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
