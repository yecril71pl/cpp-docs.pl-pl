---
title: CMFCTabToolTipInfo Structure
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: 87c8820bc33f3a344933faa797a9fc60d2422b13
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773167"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo Structure

Ta struktura zawiera informacje dotyczące zakładki MDI, który użytkownik po umieszczeniu wskaźnika nad.

## <a name="syntax"></a>Składnia

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Określa indeks formant karty.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Wskaźnik do formantu karty.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Tekst etykietki narzędzia.|

## <a name="remarks"></a>Uwagi

Wskaźnik do `CMFCTabToolTipInfo` struktury jest przekazywany jako parametr AFX_WM_ON_GET_TAB_TOOLTIP wiadomości. Ten komunikat jest generowany, gdy kart MDI są włączone i użytkownik znajduje się nad formantem karty.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `CMFCTabToolTipInfo` jest używany w [MDITabsDemo próbki: MFC z kartami MDI aplikacji](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Wymagania

**Header:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Określa indeks formant karty.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Uwagi

Indeks karty, nad którym znajduje się użytkownik.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_nTabIndex` jest używany w [MDITabsDemo próbki: MFC z kartami MDI aplikacji](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Wskaźnik do formantu karty.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_pTabWnd` jest używany w [MDITabsDemo próbki: MFC z kartami MDI aplikacji](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

Tekst etykietki narzędzia.

```
CString m_strText;
```

### <a name="remarks"></a>Uwagi

Jeśli ten ciąg jest pusty, nie jest wyświetlana etykietka narzędzia.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_strText` jest używany w [MDITabsDemo próbki: MFC z kartami MDI aplikacji](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
