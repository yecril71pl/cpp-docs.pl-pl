---
title: Struktura CMFCTabToolTipInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367339"
---
# <a name="cmfctabtooltipinfo-structure"></a>Struktura CMFCTabToolTipInfo

Ta struktura zawiera informacje o karcie MDI, na którą znajduje się najechanie kursorem myszy.

## <a name="syntax"></a>Składnia

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Określa indeks formantu karty.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Wskaźnik do kontrolki karty.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Tekst etykietki narzędzia.|

## <a name="remarks"></a>Uwagi

Wskaźnik do `CMFCTabToolTipInfo` struktury jest przekazywany jako parametr AFX_WM_ON_GET_TAB_TOOLTIP wiadomości. Ten komunikat jest generowany, gdy karty MDI są włączone, a użytkownik najedzie kursorem na kontrolkę karty.

## <a name="example"></a>Przykład

W poniższym `CMFCTabToolTipInfo` przykładzie pokazano, jak jest używany w [przykładzie MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex

Określa indeks formantu karty.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Uwagi

Indeks karty, nad którą użytkownik jest najechaniem kursorem.

### <a name="example"></a>Przykład

W poniższym `m_nTabIndex` przykładzie pokazano, jak jest używany w [przykładzie MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd

Wskaźnik do kontrolki karty.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Przykład

W poniższym `m_pTabWnd` przykładzie pokazano, jak jest używany w [przykładzie MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText

Tekst etykietki narzędzia.

```
CString m_strText;
```

### <a name="remarks"></a>Uwagi

Jeśli ciąg jest pusty, etykietka narzędzia nie jest wyświetlana.

### <a name="example"></a>Przykład

W poniższym `m_strText` przykładzie pokazano, jak jest używany w [przykładzie MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
