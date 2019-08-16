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
ms.openlocfilehash: f1b6f626b5f9844c73cd2225a7d6311f5b2f7d4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505092"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Klasa CMFCPropertyGridToolTipCtrl

Implementuje formant ToolTip, którego [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) używa do wyświetlania etykietek narzędzi.

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
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCPropertyGridToolTipCtrl:: Create](#create)|Tworzy okno dla kontrolki ToolTip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Dezaktywuje i ukrywa kontrolkę etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Zwraca współrzędne ostatniej pozycji kontrolki ToolTip.|
|[CMFCPropertyGridToolTipCtrl:: Hide](#hide)|Ukrywa kontrolkę etykietki narzędzia.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okna przed ich wysłaniem do funkcji [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Przesłania [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Ustawia odstępy między tekstem etykietki narzędzia a obramowaniem okna etykietki narzędzia.|
|[CMFCPropertyGridToolTipCtrl:: Track](#track)|Wyświetla kontrolkę etykietki narzędzia.|

## <a name="remarks"></a>Uwagi

Etykietki narzędzi są wyświetlane, gdy wskaźnik zmieni się na nazwę właściwości. Klasa [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) wyświetla etykietkę narzędzia, aby można ją było łatwo odczytać przez użytkownika. Zwykle pozycja etykietki narzędzia jest określana na podstawie pozycji wskaźnika. Za pomocą tej klasy, etykietka narzędzia pojawia się nad nazwą właściwości i przypomina rozszerzenie właściwości naturalnej, dzięki czemu nazwa właściwości jest w pełni widoczna.

MFC automatycznie tworzy ten formant i używa go w [klasie CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCPropertyGridToolTipCtrl` klasy i sposób wyświetlania kontrolki ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridtooltipctrl. h

##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Konstruuje `CMFCPropertyGridToolTipCtrl` obiekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>CMFCPropertyGridToolTipCtrl:: Create

Tworzy okno dla kontrolki ToolTip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do okna nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało pomyślnie utworzone; w przeciwnym razie FALSE.

##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::D eactivate

Dezaktywuje i ukrywa kontrolkę etykietki narzędzia.

```
void Deactivate();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia ostatnią pozycję i tekst na puste wartości, tak aby przyszłe wywołania [CMFCPropertyGridToolTipCtrl:: Track](#track) wyświetlały etykietkę narzędzia.

##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Zwraca współrzędne ostatniej pozycji kontrolki ToolTip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
określoną Zawiera ostatnią pozycję kontrolki ToolTip.

##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl:: Hide

Ukrywa kontrolkę etykietki narzędzia.

```
void Hide();
```

##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Ustawia odstępy między tekstem etykietki narzędzia a obramowaniem okna etykietki narzędzia.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
podczas Określa odstępy między tekstem kontrolki etykietki narzędzia a obramowaniem okna etykietki narzędzia. Wartość domyślna to 10 pikseli.

##  <a name="track"></a>CMFCPropertyGridToolTipCtrl:: Track

Wyświetla kontrolkę etykietki narzędzia.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Określa położenie i rozmiar kontrolki ToolTip.

*strText*<br/>
podczas Określa tekst, który ma być wyświetlany w etykietce narzędzia.

### <a name="remarks"></a>Uwagi

Ta metoda wyświetla kontrolkę etykietki narzędzia w pozycji i rozmiarze określonym przez element *Rect*. Jeśli pozycja, rozmiar i tekst nie uległy zmianie od czasu ostatniego wywołania tej metody, ta metoda nie ma żadnego wpływu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
