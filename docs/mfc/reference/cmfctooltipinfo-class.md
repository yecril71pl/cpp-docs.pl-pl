---
title: Klasa CMFCToolTipInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4685b050f7fca71a8aaaf05b072069bdd985ccdc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061686"
---
# <a name="cmfctooltipinfo-class"></a>Klasa CMFCToolTipInfo

Przechowuje informacje na temat wyglądu etykietek narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCToolTipInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolTipInfo::operator =](#operator_eq)||

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Wartość logiczna wskazująca, czy etykietka narzędzia wygląd dymek.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Wartość logiczna wskazująca, czy etykietka narzędzia etykiety są wyświetlane pogrubioną czcionką.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Wartość logiczna wskazująca, czy etykietka narzędzia zawiera opis.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Wartość logiczna wskazująca, czy etykietka narzędzia jest wyświetlana ikona.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Wartość logiczna wskazująca, czy między etykietki narzędzia etykiety i opis etykietki narzędzia wyświetlana jest separatorem.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Wartość logiczna wskazująca, czy etykietki narzędzia ma zaokrąglone rogi.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Zmiennej typu Boolean wskazującą, czy wygląd etykietki narzędzia powinny być kontrolowane przez Menedżer wizualnego (zobacz [klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)).|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Kolor obramowania etykietki narzędzia.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Kolor tła etykietki narzędzia.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Kolor wypełnienia gradientowego w etykietce narzędzia.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Kolor tekstu w etykietce narzędzia.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Kąt wypełnieniem gradientowym w etykietce narzędzia.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Maksymalna możliwa szerokość w pikselach, opis w etykietce narzędzia.|

## <a name="remarks"></a>Uwagi

Użyj [klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, i [klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) ze sobą, aby implementować niestandardowe etykietki narzędzi w aplikacji. Na przykład dotyczące używania tych klas etykietki narzędzia zobacz [klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) tematu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można ustawić wartości różne zmienne Członkowskie `CMFCToolTipInfo` klasy.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtooltipctrl.h

##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip

Określa styl wyświetlania wszystkich etykietek narzędzi.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE wskazuje, że etykietki narzędzi korzystać stylu balonowego, wartość FALSE wskazuje, że etykietki narzędzi korzystać styl prostokątny.

##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel

Określa czcionkę tekstu etykietki narzędzia jest pogrubiony.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Uwagi

Ustaw tą składową, aby wartość PRAWDA, aby tekst etykietki narzędzia wyświetlana czcionką pogrubioną, lub FAŁSZ Aby wyświetlić etykietkę narzędzia etykiety przy użyciu pogrubiona czcionki.

##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription

Określa, czy każdy etykietka narzędzia zawiera tekst opisu.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Uwagi

Ustaw ten element na wartość true, Wyświetl opis lub FAŁSZYWE do ukrycia opis. Można określić opis w etykietce narzędzia, wywołując [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon

Określa, czy wszystkie etykietki narzędzi wyświetlanie ikon.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski ustaw wartość TRUE, aby wyświetlić ikonę na każdym etykietki narzędzia, lub FAŁSZ, aby wyświetlić etykietki narzędzi bez ikony.

##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator

Określa, czy każdy etykietki narzędzia ma znak oddzielający etykiety i jego opis.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Uwagi

Ustaw ten element członkowski na wartość TRUE, aby wyświetlić separator między etykietki narzędzia etykiety i opis lub wartość FAŁSZ powoduje wyświetlanie etykietek narzędzi bez separatorów.

##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners

Określa, czy wszystkie etykietki narzędzi ma zaokrąglone rogi.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Uwagi

Ustaw tą składową, aby wartość true, ekran zaokrąglone narożniki dotyczących etykietek narzędzi, lub FAŁSZ Aby wyświetlić prostokątny rogi dotyczących etykietek narzędzi.

##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder

Określa kolor obramowania na wszystkie etykietki narzędzi.

```
COLORREF m_clrBorder;
```

##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill

Określa kolor tła etykietki narzędzia.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Uwagi

Jeśli [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) wynosi -1, kolor tła etykietek narzędzi jest `m_clrFill`. W przeciwnym razie `m_clrFill` Określa kolor początkowy gradientu i `m_clrFillGradient` Określa kolor końcowy gradientu. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Określa kierunek gradientu.

##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient

Określa kolor końcowy gradientu tła etykietek narzędzi.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_clrFillGradient` wynosi -1, nie ma żadnych gradientu. W przeciwnym razie kolor początkowy gradientu jest określona przez [CMFCToolTipInfo::m_clrFill](#m_clrfill) i określany przez kolor gradientu Zakończ `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Określa kierunek gradientu.

##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText

Określa kolor tekstu, wszystkie etykietek narzędzi.

```
COLORREF m_clrText;
```

##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle

Określa kąt rysowania gradientu tła etykietek narzędzi.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Uwagi

`m_nGradientAngle` Określa kąt w stopniach, że gradientu tła etykietek narzędzi jest przesunięcie od poziomych. Jeśli `m_nGradientAngle` wynosi 0, gradientu jest rysowana od lewej do prawej. Jeśli `m_nGradientAngle` to od 1 do 360 gradientu jest obracanie zgodnie ze wskazówkami zegara przez tę liczbę stopni. Jeśli `m_nGradientAngle` wynosi -1, która jest wartością domyślną, gradientu jest rysowana od góry do dołu. To jest taka sama, jak ustawienie `m_nGradientAngle` na 90.

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` Określa kolor początkowy gradientu i [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` Określa kolor końcowy gradientu. Jeśli `m_clrFillGradient` wynosi -1, nie ma żadnych gradientu.

##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth

Określa maksymalną szerokość opis, który on wyświetlany w każdym etykietki narzędzia. Szerokość opisu przekracza określoną wartość, opakowaniu tekstu.

```
int m_nMaxDescrWidth;
```

##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme

Określa, czy visual Menedżera aplikacji steruje wyglądem wszystkie etykietki narzędzi.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bVislManagerTheme` ma wartość TRUE, co etykietki narzędzia żądania nowy [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) z visual Menedżera aplikacji przed ich na ekranie i używa wartości w tym obiekcie do określenia sposobu ich wyświetlania. Innym członkom swojej [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) są ignorowane.

##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Parametry

[in] *src*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)
