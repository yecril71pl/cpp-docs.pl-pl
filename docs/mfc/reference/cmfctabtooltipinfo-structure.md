---
title: Struktura CMFCTabToolTipInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21e612615110370922d71e1acaebcda56b2e692e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435457"
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
