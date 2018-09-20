---
title: Klasa CMFCPropertyGridToolTipCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea84af41178316085a903d2663ded74ee57c99a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389749"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Klasa CMFCPropertyGridToolTipCtrl

Implementuje w etykietce narzędzia kontrolkę, która [klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) używa w celu wyświetlenia etykietki narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Konstruuje `CMFCPropertyGridToolTipCtrl` obiektu.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Tworzy okno dla kontrolki tooltip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Dezaktywuje i ukrywa kontrolki tooltip.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Zwraca współrzędne ostatnia pozycja kontrolki tooltip.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Ukrywa kontrolki tooltip.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Ustawia odstęp między tekst etykietki narzędzia i krawędź okna etykiety narzędzi.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Wyświetla kontrolki tooltip.|

## <a name="remarks"></a>Uwagi

Etykietki narzędzi są wyświetlane po zatrzymaniu wskaźnika myszy nad nazwy właściwości. [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) tak, aby łatwo czytelnej przez użytkownika, klasa wyświetla etykietkę narzędzia. Zazwyczaj położenia etykietki narzędzia jest ustalany położenia wskaźnika. Za pomocą tej klasy, etykietki narzędzia pojawi się nad nazwy właściwości i przypomina rozszerzenie właściwości fizyczne, aby w pełni widoczna jest nazwa właściwości.

MFC, automatycznie tworzy ten formant i używa go w [klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCPropertyGridToolTipCtrl` klasy i sposób wyświetlania kontrolki tooltip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Konstruuje `CMFCPropertyGridToolTipCtrl` obiektu.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Tworzy okno dla kontrolki tooltip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno został pomyślnie utworzony; w przeciwnym razie wartość FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Dezaktywuje i ukrywa kontrolki tooltip.

```
void Deactivate();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia ostatniej pozycji i tekst wartości puste, aby w przyszłości wywołuje w celu [CMFCPropertyGridToolTipCtrl::Track](#track) wyświetlić etykietkę narzędzia.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Zwraca współrzędne ostatnia pozycja kontrolki tooltip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[out] Zawiera ostatnia pozycja kontrolki tooltip.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

Ukrywa kontrolki tooltip.

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

Ustawia odstęp między tekst etykietki narzędzia i krawędź okna etykiety narzędzi.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
[in] Określa odstępy między tekst kontrolki etykietki narzędzia i krawędź okna etykiety narzędzi. Wartość domyślna to 10 pikseli.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Wyświetla kontrolki tooltip.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Określa położenie i rozmiar kontrolki tooltip.

*strText*<br/>
[in] Określa tekst wyświetlany w etykietce narzędzia.

### <a name="remarks"></a>Uwagi

Ta metoda Wy Wyświetla kontrolki tooltip na położenie i rozmiar określony przez *prostokąt*. Jeśli położenie, rozmiar i tekst nie uległy zmianie od czasu ostatniego wywołania tej metody, Metoda ta nie ma znaczenia.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
