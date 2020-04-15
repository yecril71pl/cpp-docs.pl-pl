---
title: Klasa CMFCToolBarInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376191"
---
# <a name="cmfctoolbarinfo-class"></a>Klasa CMFCToolBarInfo

Zawiera identyfikatory zasobów obrazów paska narzędzi w różnych stanach. `CMFCToolBarInfo`jest klasą pomocnika, która jest używana jako parametr [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metody.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej regularne (zimne) obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej wyłączone obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej wybrane (gorące) obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej duże, regularne obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej duże, wyłączone obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej duże, zaznaczone obrazy paska narzędzi.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej wyłączone obrazy menu.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Identyfikator zasobu mapy bitowej paska narzędzi zawierającej obrazy menu.|

## <a name="remarks"></a>Uwagi

Pełna mapa bitowa paska narzędzi składa się z małych obrazów (przycisków) paska narzędzi o stałym rozmiarze. Każdy identyfikator zasobu przechowywany `CMFCToolBarInfo` w obiekcie jest bitmapą zawierającą pełny zestaw obrazów paska narzędzi w jednym stanie (na przykład wybrane, wyłączone, duże lub obrazy menu).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID

Określa identyfikator zasobu dla wszystkich zwykłych obrazów przycisków paska narzędzi.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID

Określa identyfikator zasobu dla obrazów paska narzędzi niedostępnych dla przycisków.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID

Określa identyfikator zasobu dla wszystkich wyróżnionych obrazów przycisków paska narzędzi.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID

Określa identyfikator zasobu dla wszystkich dużych zwykłych obrazów przycisków paska narzędzi.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID

Określa identyfikator zasobu dla wszystkich dużych obrazów przycisków wyłączonych paska narzędzi.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID

Określa identyfikator zasobu dla wszystkich dużych podświetlonych obrazów paska narzędzi.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID

Określa identyfikator zasobu dla obrazów niedostępnych dla poleceń paska narzędzi.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID

Określa identyfikator zasobu dla wszystkich zwykłych obrazów elementów menu paska narzędzi.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
