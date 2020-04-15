---
title: Klasa CMFCPropertyGridToolTipCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 94d75f914e5f7928d08dd2a87997ab02c4f16832
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361788"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Klasa CMFCPropertyGridToolTipCtrl

Implementuje formant etykietki narzędzia, który [CMFCPropertyGridCtrl Klasa](../../mfc/reference/cmfcpropertygridctrl-class.md) używa do wyświetlania etykietek narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Konstruuje `CMFCPropertyGridToolTipCtrl` obiekt.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCPropertyGridToolTipCtrl::Tworzenie](#create)|Tworzy okno dla formantu etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl: :Daktywować](#deactivate)|Dezaktywuje i ukrywa formant etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Zwraca współrzędne ostatniej pozycji formantu etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl::Ukryj](#hide)|Ukrywa formant etykietki narzędzia.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do tłumaczenia wiadomości okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Zastępuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Ustawia odstępy między tekstem etykietki narzędzia a obramowaniem okna etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl::Utwór](#track)|Wyświetla kontrolkę etykietki narzędzia.|

## <a name="remarks"></a>Uwagi

Etykietki narzędzi są wyświetlane, gdy wskaźnik opiera się na nazwie właściwości. [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) klasy wyświetla etykietki narzędzia, dzięki czemu jest łatwo czytelny przez użytkownika. Zazwyczaj położenie etykietki narzędzia jest określane przez położenie wskaźnika. Za pomocą tej klasy etykietka narzędzia pojawia się nad nazwą właściwości i przypomina naturalne rozszerzenie właściwości, dzięki czemu nazwa właściwości jest w pełni widoczna.

MFC automatycznie tworzy ten formant i używa go w [CMFCPropertyGridCtrl Klasy](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCPropertyGridToolTipCtrl` skonstruować obiekt klasy i jak wyświetlić formant etykietki narzędzia.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridtooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Konstruuje `CMFCPropertyGridToolTipCtrl` obiekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Tworzenie

Tworzy okno dla formantu etykietki narzędzia.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało pomyślnie utworzone; w przeciwnym razie FALSE.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl: :Daktywować

Dezaktywuje i ukrywa formant etykietki narzędzia.

```
void Deactivate();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia ostatnią pozycję i tekst do pustych wartości, tak aby przyszłe wywołania [CMFCPropertyGridToolTipCtrl::Track](#track) wyświetlić etykietkę narzędzia.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Zwraca współrzędne ostatniej pozycji formantu etykietki narzędzia.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[na zewnątrz] Zawiera ostatnią pozycję formantu etykietki narzędzia.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Ukryj

Ukrywa formant etykietki narzędzia.

```
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Ustawia odstępy między tekstem etykietki narzędzia a obramowaniem okna etykietki narzędzia.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
[w] Określa odstępy między tekstem sterującym etykietki narzędzia a obramowaniem okna etykietki narzędzia. Wartość domyślna to 10 pikseli.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Utwór

Wyświetla kontrolkę etykietki narzędzia.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Określa położenie i rozmiar formantu etykietki narzędzia.

*strText (tekst)*<br/>
[w] Określa tekst, który ma być wyświetlany w etykietce narzędzia.

### <a name="remarks"></a>Uwagi

Ta metoda wyświetla kontrolkę etykietki narzędzia w miejscu i rozmiarze określonym przez *rect*. Jeśli pozycja, rozmiar i tekst nie uległy zmianie od czasu ostatniego wywołania tej metody, ta metoda nie ma wpływu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
