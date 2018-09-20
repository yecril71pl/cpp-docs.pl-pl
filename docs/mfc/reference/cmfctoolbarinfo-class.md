---
title: Klasa CMFCToolBarInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7825983fbc70dafbbcc96221b8a38c3ae4e939c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435444"
---
# <a name="cmfctoolbarinfo-class"></a>Klasa CMFCToolBarInfo

Zawiera identyfikatory paska narzędzi obrazów w różnych stanach. `CMFCToolBarInfo` jest pomocnikiem klasy, która jest używana jako parametr [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metody.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identyfikator zasobu mapy bitowej paska narzędzi, który zawiera obrazy regularne narzędzi ("zimne").|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi, zawierającą wyłączonego paska narzędzi obrazów.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Identyfikator zasobu mapy bitowej paska narzędzi, który zawiera obrazy wybranych narzędzi (gorąca).|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Identyfikator zasobu mapy bitowej paska narzędzi, zawierający obrazy dużych, regularne paska narzędzi.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi, który zawiera dużą, wyłączone obrazami paska narzędzi.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Identyfikator zasobu mapy bitowej paska narzędzi, który zawiera obrazy dużych, wybranych narzędzi.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Identyfikator zasobu mapy bitowej paska narzędzi, zawierającą wyłączonego menu obrazy.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Identyfikator zasobu mapy bitowej paska narzędzi, który zawiera obrazy w menu.|

## <a name="remarks"></a>Uwagi

Mapy bitowej narzędzi Pełny składa się z małych paska narzędzi obrazów (przyciski) o stałym rozmiarze. Każdy identyfikator zasobu, która jest przechowywana w `CMFCToolBarInfo` obiekt jest mapy bitowej, który zawiera pełny zestaw narzędzi obrazów w jednym stanie (przykład wybrane wyłączone dużych obrazów lub menu).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

Określa identyfikator zasobu dla wszystkich obrazów zwykły przycisk paska narzędzi.

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

Określa identyfikator zasobu na samych obrazach niedostępny przycisku paska narzędzi.

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

Określa identyfikator zasobu dla wszystkich obrazów podświetlony przycisk paska narzędzi.

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

Określa identyfikator zasobu dla wszystkich obrazów dużych zwykły przycisk paska narzędzi.

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

Określa identyfikator zasobu dla wszystkich obrazów duży wyłączony przycisk paska narzędzi.

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

Określa identyfikator zasobu do dużych obrazów wyróżnione paska narzędzi.

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

Określa identyfikator zasobu dla polecenia dostępne obrazy paska narzędzi.

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

Określa identyfikator zasobu dla wszystkich obrazów elementów menu regularne paska narzędzi.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
