---
title: Struktura CMFCTabToolTipInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: b785754a7970573c42fcc1d0736541416f522c9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429178"
---
# <a name="cmfctabtooltipinfo-structure"></a>Struktura CMFCTabToolTipInfo

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

W poniższym przykładzie przedstawiono sposób `CMFCTabToolTipInfo` jest używany w [MDITabsDemo próbki: aplikacja z kartami MDI w MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Określa indeks formant karty.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Uwagi

Indeks karty, nad którym znajduje się użytkownik.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_nTabIndex` jest używany w [MDITabsDemo próbki: aplikacja z kartami MDI w MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Wskaźnik do formantu karty.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_pTabWnd` jest używany w [MDITabsDemo próbki: aplikacja z kartami MDI w MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

Tekst etykietki narzędzia.

```
CString m_strText;
```

### <a name="remarks"></a>Uwagi

Jeśli ten ciąg jest pusty, nie jest wyświetlana etykietka narzędzia.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób `m_strText` jest używany w [MDITabsDemo próbki: aplikacja z kartami MDI w MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
